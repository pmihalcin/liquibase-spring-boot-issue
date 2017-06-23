I created Boot application with JPA, Liquibase, Web, H2 dependencies and enabled h2 console. 
Boot version is **1.5.4-RELEASE**. 
When I run the application without updating liquibase application properties, tables are created.

When I set properties to:
- liquibase.url=jdbc:h2:mem:testdb
- liquibase.user=sa
- liquibase.password=
- liquibase.default-schema=PUBLIC

and connect to http://localhost:8080/h2-console/ using 
- Driver Class: org.h2.Driver
- JDBC URL: jdbc:h2:mem:testdb
- User Name: sa

Then no tables are created.

When I switch back to Boot version **1.5.3-RELEASE**, it works

When I don't specify liquibase application properties (I go with default) using **1.5.4-RELEASE**, tables are created.
It seems it is some regression issue.
My wild guess is it might be related to https://github.com/spring-projects/spring-boot/issues/9218.

**I pushed sample app to reproduce the issue here: https://github.com/pmihalcin/liquibase-spring-boot-issue**


<!--
Thanks for raising a Spring Boot issue. What sort of issue are you raising?

Question

Please ask questions about how to use something, or to understand why something isn't
working as you expect it to, on Stack Overflow using the spring-boot tag.

Bug report

Please provide details of the problem, including the version of Spring Boot that you
are using. If possible, please provide a test case or sample application that reproduces
the problem. This makes it much easier for us to diagnose the problem and to verify that
we have fixed it.

Enhancement

Please start by describing the problem that you are trying to solve. There may already
be a solution, or there may be a way to solve it that you hadn't considered.
-->
