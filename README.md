# Solution
  - step1:
  - docker run -d infracloudio/csvserver:latest 
  - check errors by using command docker logs Container_id
    ```console
    2021/01/20 15:19:12 error while reading the file "./inputdata": open ./inputdata: no such file or directory
    ```
  - step2:
  - Create a gencsv.sh file and a directory
    ```console
    vi gencsv.sh
	  ```
  > **NOTE**: gencsv.sh file is provided in solution directory
  
  - step3:
  - Run the following script 
    ```console
    chmod +x gencsv.sh
    ./gencsv.sh
	  ```
  - It will create a file name called as inputFile which we need to provide in container at path /csvserver
  - step4:
  - Run the docker in dettached mode
    ```console
    docker run -d -v /root/inputFile:/csvserver/inputdata infracloudio/csvserver:latest
    ```
  - Remove running container using command docker rm -f Container_i
  - Use docker inspect to check the port exposed in container
    ```console
    docker inspect container_id
	  ```
  - step5:
  - To set environment variable and port use -e and -p options.
    ```console
    docker run -d -p 9393:9300 -v /root/inputFile:/csvserver/inputdata -e CSVSERVER_BORDER=Orange infracloudio/csvserver:latest
    ```
  - step6:
  - docker-compose file is provided at **solution** directory
  ```console
  docker-compose up
  ```
  - step6:
  - Promethus requires promethus configuration file promethus.yml which is provided in solution directory.
> **NOTE**: Change ip address and port in promethus.yml file.
  ```console
  docker-compose up
  ```    
