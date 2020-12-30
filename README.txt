Contents of Project2 zipped folder:
1.README.txt
2.create.sh
3.destroy.sh
4.udam_network.yml
5.udam_network_params.json
6.udam_server.yml
7.udam_server_params.json
8.bastion_host.pem


Please follow the below steps in order to create the network infrastructure:
1. Unzip the Project2.zip and change directory to Project2 
2. Update the values of the parameters in udam_network_params.json,udam_server_params.json, as required
3. Execute on AWS-CLI terminal: bash create.sh <network_stack name> udam_network.yml udam_network_params.json 
4. Wait till the status of network_stack is shown as CREATE_COMPLETE on AWS Cloudformation dashboard
5. Execute on AWS-CLI terminal: bash create.sh <server_stack name> udam_server.yml udam_server_params.json
6. Wait till the status of server_stack is shown as CREATE_COMPLETE on AWS Cloudformation Service dashboard

Check the project output and other deliverables:
6. The Public URL of the Udagram webpage can be obtained in the "Output" field of the server_stack information with the key : WebAppLB
7. To access the EC2 instance information for the bastion host, click the Physical ID link in the "Resources" field of the above stack with the logical id: BastionEC2Instance

Troubleshooting the Servers:
8. The Public IP address of the bastion host can be obtained from EC2 instance information ,e.g: X.X.X.X 
9. Execute can be reached by Secure Shell  with  the command: ssh -i "bastion_host.pem" ec2-user@ec2-X-X-X-X.us-west-2.compute.amazonaws.com
10. The key file "elbkey.pem" for SSH connection to the Server Instance is created with AWS Parameter Store,and will be present in folder: /home/ec2-user/
11. The private IP address of the Server's EC2 instance can be obtained from the EC2 Instance information dashboard.
12. Please use the following command to SSH into the Server: sudo ssh -i "elbkey.pem" ubuntu@<Server IP>

Destroy the Infrastructure:
13. Delete the server_stack with the command on the CLI terminal:  bash destroy.sh <server_stack name>
14  Wait till the status of the server_stack is shown as DELETE_COMPLETE in the AWS Cloudformation dashboard
15. Delete the network_stack with the commandon the CLI terminal: bash destroy.sh <network_stack>



URL of the Load balancer: http://srvr-WebApp-9DQR82EHY5RX-1988460123.us-west-2.elb.amazonaws.com
