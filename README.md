# Fetch
The code here is written in Java and will need to be ran in Eclipse or Spring Tool Suite 4 
which is built off of Eclipse. 

Eclipse:
If using Eclipse you should go to File->Open Projects 
From File System.... Then select the unzip folder. Once it has been imported right-click
on the project name which will probably be "Fetch-master" off on the left of the screen.
Click Run As-> Maven Build... Then enter "spring-boot:run" on the goals line. Click Apply
then click Run. It could fail if the localport 8080 us being used so you can run the command
"Get-Process -Id (Get-NetTCPConnection -LocalPort 8080).OwningProcess" in PowerShell then
"taskkill /PID {Id from last command} /F" to kill the process and allow access to Eclipse
to use that port. You can right click the console and click Terminate/DisconnectAll to 
end it, but you may need to manually kill the process because it may still try to hold on
to the port.

Spring Tool Suite 4:
If using Spring Tool Suite 4 you should go to File->Open Projects 
From File System.... Then select the unzip folder. Once it has been imported right-click
on the project name which will probably be "Fetch-master" off on the left of the screen.
Click Run As-> Spring Boot App. You can hit the big red square on the top items bar to 
stop the project.

Running:
The three commands are:
http://localhost:8080/fetch/add       with JSON (payer, points, timestamp)
http://localhost:8080/fetch/get       
http://localhost:8080/fetch/spend     with JSON (points)
They do not have to be Post, Put, or any other special kind of request.
Add will return the JSON of the object you just added.
Get will return all payers' names and balances.
Spend will return the payers' and the amount of points they spent.
I decided to not allow spending of negative points so that will return an empty object.
