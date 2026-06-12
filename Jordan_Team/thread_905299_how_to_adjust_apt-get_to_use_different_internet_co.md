---
title: "how to adjust apt-get to use different internet connection than default"
date: 2008-08-30
forum: Jordan Team
---

### Post by mkrahmeh on 2008-08-30
gurus
i connected my pc to a new DSL connection, browsing worked fine after changing the settings in firefox, but apt-get (through command line)
 rendered disconnected..how do i adjust the apt-get to be able to connect through the new connection? 
i searched in the related configuration files but found nothing that might help..moreover, the file /etc/apt/aptconf is not present in my system, which seems to be a problem
any suggestions??

---

### Post by AboSamoor on 2008-09-09
are you behind a proxy ?

---

### Post by mkrahmeh on 2008-09-09
actually i am :)
earlier, in order to get connected through the proxy, i defined two variables in my /etc/profile

```
export http_proxy="192.168.20.20:8080"
export ftp_proxy="192.168.20.20:8080"
``` 

so i commented these two lines..and everything went just fine on the DSL
___________________________________________

now the problem is going in the reverse order..
when am back behind the **proxy** again, browsing is fine, but the apt-get is unable to reach the repositories..:confused:

suggestions ?? i really appreciate your help..

---

### Post by Jad on 2008-09-11
System -> Adminstration -> Synaptic Package Manager, Then 

Settings -> Network tab

---

### Post by mkrahmeh on 2008-09-11
thanks..that should work
but assuming that am working in a text-mode login, how can i configure the apt-get manually ?? is it a problem not finding the 
/etc/apt/aptconf 
file in my system ??

---

### Post by NoReflex on 2008-09-11
You can try to define the proxy in a proxy file. Create a file named proxy in /etc/apt/apt.conf.d and enter this in the file : 
```
Acquire::http::Proxy "http://proxy_hostname:proxy_port";
```
Best wishes,
NoReflex

---

### Post by mkrahmeh on 2008-09-11
so what does this acquire command does exactly ??
can i ommit the export lines using this method ?
i guess i need to replace the proxy_hostname with the proxy number..right?

---

### Post by NoReflex on 2008-09-12
Yes you can ommit the export lines using this method and yes you need to replace proxy_hostname and proxy_port with your proxy information.

Best wishes,
NoReflex

---

