### Deployment

This is the link to the Deployment Script: [scripts](https://github.com/psnakhwa/TraziBot/tree/master/ansible)

#### Initial Testing

* Say "hi/hello", so bot will know you are the manager with whom he will work with.
* Wait for bot to respond and then give the repo name to work with as "Sample-mock-repo". 
* As a simple step of authentication, bot will ask the owner of this repo. Owner of "Sample-mock-repo" is "dupandit".
* If they match, bot will list all the commands for each usecase it can perform.

![alt text](https://github.com/psnakhwa/TraziBot/blob/master/images/Screen%20Shot%202017-11-28%20at%2010.47.19%20PM.png)

[Alternate Flow]:
* Bot should throw an error when repo name and owner of the repo doesn't match.

![alt text](https://github.com/psnakhwa/TraziBot/blob/master/images/Screen%20Shot%202017-11-28%20at%2010.48.46%20PM.png)


#### Usecase 1 Testing
* We will request for a list of employees that can best solve a particular issue using 1st valid command ```find assignee for issue <no>```
* We know the bot needs to get details for that issue. Particularly it tries to find skills which are related to this issue via “labels” and “issue name and description”. After getting tags, bot should list names of 3 employees with highest tag count.
* Bot should then ask whom to assign the issue from these 3 employees.
* We select an employee by providing its name as one listed by bot previously and bot assigns the issue to that employee. We can check the corresponding issue manually and check the assignee in github.
* Bot also updates table "issue_assignee" and notifies him via email.


![alt text](https://github.com/psnakhwa/TraziBot/blob/master/images/Screen%20Shot%202017-11-28%20at%2010.51.14%20PM.png)


[Alternate Flow] :
* If the issue number given by us doesn’t exist for a given repo bot should reply that "issue does not exist"
* If the id of the selected employee is not from the given recommendations, bot will prompt you to put correct id. Failure of that will not allow you to proceed forward or even implement usecase 2 or 3.

![alt text](https://github.com/psnakhwa/TraziBot/blob/master/images/Screen%20Shot%202017-11-28%20at%2010.52.36%20PM.png)

![alt text](https://github.com/psnakhwa/TraziBot/blob/master/images/Screen%20Shot%202017-11-28%20at%2010.54.25%20PM.png)


#### Usecase 2 Testing
* We should provide bot, filename of the code requiring modifications using 2nd valid command ```find contributors for file```.
* bot uses git api to fetch the list of all commits along with commit messages.
* The bot should returns both: A summary of all the contributors of that code and also detailed version of the same.
* The bot should then ask the manager for the employee (id) to be notified.
* We can select employee based on highest contribution or rather total number of commits by providing id as listed by the bot.Bot shoul confirm our selection.
* Bot should then that contributor is notified through an email registered with his git account.

![alt text](https://github.com/psnakhwa/TraziBot/blob/master/images/Screen%20Shot%202017-11-28%20at%2010.56.18%20PM.png)

![alt text](https://github.com/psnakhwa/TraziBot/blob/master/images/Screen%20Shot%202017-11-28%20at%2010.56.34%20PM.png)

[Alternate Flow]:
* Bot should check for a valid file. It should return "No such file exists in the repository" if invalid filename provided.
* Bot should checks if a valid user id is entered. It should reask if not from the recommendations.

![alt text](https://github.com/psnakhwa/TraziBot/blob/master/images/Screen%20Shot%202017-11-28%20at%2010.57.08%20PM.png)


#### Usecase 3 Testing
* We can request for a list of reviewers that can best review a particular issue using ```find reviewers for issue <no>``` command.
Note :  This issue was already assigned to an employee previously, that's why want a reviewing. 
* Similar to usecase 1, bot needs to get details for that issue. Particularly it tries to find skills which are related to this issue. In this scenario, it finds tags for an issue from the database-table "issue_tags".
* After getting tags, bot should get the list of collaborators and find the employees with highest reviewer count if there are any reviewing entries in the table.
* Bot should also list top employees who have solved the issues with similar skill set. By this bot makes sure that it provides some useful names to us even though they haven't reviewed previously.
* Bot should then ask whom to ask to review this issue from these employees.
* We select an employee or employees with comma separated ids, bot assigns the reviewing task for that issue to the selected employees.
* Bot should then notify that reviewer via email.
  
![alt text](https://github.com/psnakhwa/TraziBot/blob/master/images/Screen%20Shot%202017-11-28%20at%2010.58.41%20PM.png)

[Alternate Flow] :
* If the issue number given by us doesn’t exist for a given repo bot should reply that "issue does not exist"
* If the id of the selected employee is not from the given recommendations, bot will prompt you to put correct id. Failure of that will not allow you to proceed forward or even implement usecase 1 or 2.

![alt flow](https://github.com/psnakhwa/TraziBot/blob/master/images/Screen%20Shot%202017-11-28%20at%2010.59.30%20PM.png)

![alt flow](https://github.com/psnakhwa/TraziBot/blob/master/images/Screen%20Shot%202017-11-28%20at%2010.57.08%20PM.png)

### Screencast
* The link to the screencast for Deployment of TraziBot [link](https://youtu.be/z84uEk1zra8)
* The link to the screencast for TraziBot interaction [link](https://youtu.be/litSo4GG4Bo)





