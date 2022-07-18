# spring cloud sleuth 

* Spring cloud sleuth implements a distributed tracing solution for spring cloud.
* Span is basic unit of work.It has unique 64 bit id. It also has metadata.
* Trace is a set of spans forming a tree like structure.
* Trace id always reman same for single request but span id change on requesting form one service to another service within the request because it is the same request that is from one service to another.

* In this application we are requesting from `doctor-portal` to `doctor-service` and `patient-service`. From `doctor-service` and `patient-service` we are requesting to `notification-service`.

* In application when we request `http://localhost:7081/doctors` we will traverse through doctor-portal to doctor-service then to notification service. we are showing info of `doctor-portal` and all services where 2nd parameter is trace id and 3rd parameter is span id.
    1. In doctor portal we have:
    > INFO [doctor-portal,30666ee6d7348da9,30666ee6d7348da9] 
    2. In doctor Service we have:
    > INFO [doctor-service,30666ee6d7348da9,8634000cfd36097d]
    3. In notification service we have:
    > INFO [notification-service,30666ee6d7348da9,9abf8a8506059159]
  
    Here we can see that all the doctor portal, doctor service and notification service have same trace id but differnt span id but the span id is same on doctor service all info and for notification service too.
* spring.sleuth.enabled is bydefault true.