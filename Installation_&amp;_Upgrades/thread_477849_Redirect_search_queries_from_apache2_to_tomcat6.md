---
title: "Redirect search queries from apache2 to tomcat6?"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by widernet_project on 2007-06-18
Dear all,
I'm setting up Ubuntu server and have some difficulties with apache2 and tomcat6.
My requirement is: I have a search box In my webpage and when user want to search something, it should redirect the query to tomcat6 (search pages are in /usr/local/tomcat6/webapps/websearch). I've tried but not been successful yet. Can anybody have a solution for my requirement?
You can log to this IP address to check: 
128.255.61.110:9980 (apache2 server, after finishing setting up proxy, type [http://egranary](http://egranary) to web browser)
128.255.61.110:8080 (tomcat6 server, if you are using proxy, remember to turn it off)
128.255.61.110:8080/websearch/index.htm (search page)
(Note that both apache and tomcat are working well, I just don't know how to redirect queries from apache to tomcat.)
Thank you.

---

