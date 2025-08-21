1. IBM Cloud Engine > Create Project > Go to Code Engine CLI
2. $ git clone https://github.com/ibm-developer-skills-network/gentu-microservices_practiceProj.git
3. $ cd gentu-microservices_practiceProj/universities
4. $ ls 
You will see two directories listed.

listing
websites
5. Run the following command to deploy the listing as a microservice 
$ ibmcloud ce app create --name listing --image us.icr.io/${SN_ICR_NAMESPACE}/listing --registry-secret icr-secret --port 5000 --build-context-dir listing --build-source .
6. Run the following command to get the details about the app 
$ ibmcloud ce app get -n listing
7. Try to access the end point 
$ curl <your deplymenturl>/colleges/Trinity
8. Get the details of the deployment again.
$ ibmcloud ce app get --name listing -q
9. Run the following command to deploy the websites as a microservice 
$ ibmcloud ce app create --name websites --image us.icr.io/${SN_ICR_NAMESPACE}/websites --registry-secret icr-secret --port 5000 --build-context-dir websites --build-source .
10. try the access the endpoint 
$ curl <your deplymenturl>/websites/Trinity%20College%20of%20Music
11. Run the following command to scale the listing application to three instances.
$ ibmcloud ce app update --name listing --min 2
12. Run the following command to see if the listing application has scaled.
$ ibmcloud ce app get --name listing -q 
.....
Updating the microservice
1.  make changes in app.py
2. Run the following command to update the application
$ ibmcloud ce app update --name websites --image us.icr.io/${SN_ICR_NAMESPACE}/websites --registry-secret icr-secret --port 5000 --build-context-dir websites --build-source .
3. try to access end point
$ curl <your deplymenturl>/websites/Trinity
4. Scale the websites microservices to have 2 minimum instances 
