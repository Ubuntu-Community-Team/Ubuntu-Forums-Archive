---
title: "ProxyPass problem - Pls HELP!!!!!!!!!!!!1"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by widernet_project on 2007-06-25
Dear all,
I have problem with setting up ProxyPass and ProxyPassReverse.
I have my search engine in Tomcat6 serving on [http://localhost:8080/websearch](http://localhost:8080/websearch). I want to make a ProxyPass to this, so I use:

ProxyPass /eGranarySearch [http://localhost:8080/websearch](http://localhost:8080/websearch)
ProxyPassReverse /eGranarySearch htpp://localhost:8080/websearch

These lines work well on Window, but not on Ubuntu. So I try another way:

<VirtualHost 128.255.61.110:8080>
ServerName eGranarySearch
ProxyPass / [http://localhost:8080/websearch](http://localhost:8080/websearch)
ProxyPassReverse / [http://localhost:8080/websearch](http://localhost:8080/websearch)
</VirtualHost>

I tried and it didn't work either. 
Can anybody suggest me a solution.
Thank a lot.

Note that I have changed the proxy.conf file as suggested here: [http://ubuntuforums.org/showthread.php?t=39328](http://ubuntuforums.org/showthread.php?t=39328)

---

### Post by Howler9443 on 2007-08-27
You may want to try using ajp instead of http. I had this working in the past with JBoss 4.0.5-GA, but now I am having an issue with 4.2.0-GA. Though it may work for you since you are using Tomcat 6.

$> sudo a2enmod proxy
$> sudo a2enmod proxy_ajp

Change your Proxy lines to something like this.

ProxyPass /eGranarySearch [ajp://localhost:8009/websearch](ajp://localhost:8009/websearch)
ProxyPassReverse /eGranarySearch ajp://localhost:8009/websearch

Assuming that you are using the default AJP port of 8009 and not something else.  I would also change how you are accessing the virtual host. I assume you want to proxy through Apache2 to the Tomcat container.  I hope this helps.

> **widernet_project said:**
> Dear all,
I have problem with setting up ProxyPass and ProxyPassReverse.
I have my search engine in Tomcat6 serving on [http://localhost:8080/websearch](http://localhost:8080/websearch). I want to make a ProxyPass to this, so I use:

ProxyPass /eGranarySearch [http://localhost:8080/websearch](http://localhost:8080/websearch)
ProxyPassReverse /eGranarySearch htpp://localhost:8080/websearch

These lines work well on Window, but not on Ubuntu. So I try another way:

<VirtualHost 128.255.61.110:8080>
ServerName eGranarySearch
ProxyPass / [http://localhost:8080/websearch](http://localhost:8080/websearch)
ProxyPassReverse / [http://localhost:8080/websearch](http://localhost:8080/websearch)
</VirtualHost>

I tried and it didn't work either. 
Can anybody suggest me a solution.
Thank a lot.

Note that I have changed the proxy.conf file as suggested here: [http://ubuntuforums.org/showthread.php?t=39328](http://ubuntuforums.org/showthread.php?t=39328)

---

### Post by widernet_project on 2007-09-12
Thank you for the answer.
Actually, I found the answer for my problem and post the information here in case someone has the same problem with me. 
Instead of using 

ProxyPass /eGranarySearch //IP_ADDRESS:8009/websearch
ProxyPassReverse /eGranarySearch //IP_ADDRESS:8009/websearch

You should rename the folder websearch to eGranarySearch (and file websearh.war to eGranarySearch.war too), and make ProxyPass as:

ProxyPass /eGranarySearch //IP_ADDRESS:8009/eGranarySearch
ProxyPassReverse /eGranarySearch //IP_ADDRESS:8009/eGranarySearch

It will work well.

---

