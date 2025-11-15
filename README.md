# configServerRepo
This is the parctice repository to config the centralized server

##########################################
Eureka server creation : 
step 1: add dependencies - (spring-cloud-starter-netflix-eureka-server and spring-boot-starter-web).
step 2: annote this annotation - (@EnableEurekaServer) in mail class.
step 3: add the following properties in application.properties
"""
// port number 
server.port= 8761

// This tells Eureka what hostname to use for this server instance.If hosting on AWS, Docker, Kubernetes → this will be the instance's actual hostname/IP.
eureka.instance.hostname=localhost

//Normally, a service that acts as a Eureka client downloads the list of registered services (registry).But the Eureka Server does NOT need to fetch registry from itself.
eureka.client.fetch-registry=false

//Normally, microservices register themselves into Eureka.But the Eureka Server should not try to register itself as a client.
eureka.client.register-with-eureka=false
"""

###########################################
ApiGateWay creation:
step 1: add dependencies - (spring-boot-starter-web, spring-cloud-starter-gateway, spring-cloud-starter-netflix-eureka-client , reactor-test(if want to test reactive)
step 2:  add the following properties in application.properties
"""
server.port=5000

spring.cloud.gateway.server.webflux.discovery.locator.enabled=true
spring.cloud.gateway.server.webflux.discovery.locator.lower-case-service-id=true

spring.main.web-application-type=reactive
"""


