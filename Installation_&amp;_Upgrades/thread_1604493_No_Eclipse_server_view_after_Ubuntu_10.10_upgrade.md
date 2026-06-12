---
title: "No Eclipse server view after Ubuntu 10.10 upgrade"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by axe87 on 2010-10-24
I've just tried using Eclipse for the first time after upgrading to Ubuntu 10.10 and can't access the Eclipse server view. I've tried reinstalling Eclipse Web Tools (WTP) but still have the same problem.

Before I try completely uninstalling and reinstalling Eclipse using the manual approach and not by the Software Centre this time, I wondered if anyone else has seen this problem.

---

### Post by DrTomFlint on 2010-11-09
Also running Ubuntu 10.10 , eclipse 3.5.2, and installed tomcat 6.0.28,  all from official repos using Synaptic package manager.  Apache 2.2.16. 

I know apache is working, it servers my website no problems.  Not so sure about the tomcat install.

I got the server view from the menus:

[B]Window | Show View | Other... | Server
[/B]
But then try to add the tomcat server by right click in the servers window and select New -> server

There is nothing listed in the server type box.  

Do I need to use the "download additional server adapters" ?

---

### Post by axe87 on 2010-11-10
I believe you will need JST Server Adapters.

See the following link

[http://old.nabble.com/Re%3A-Tomcat-Adapter-for-Eclipse-3.5-Galileo--p24499099.html](http://old.nabble.com/Re%3A-Tomcat-Adapter-for-Eclipse-3.5-Galileo--p24499099.html)

I have WTP installed and therefore the Tomcat Adapter came with that.

---

### Post by anupindi007 on 2011-02-19
Hi,
Not able to add apache server to eclipse wtp,  my system shows the following and suggest me what should i do:

Trying to configure Eclipse WTP but not able to add the apache2 server.

[http://www.eclipse.org/webtools/community/tutorials/BuildJ2EEWebApp/BuildJ2EEWebApp.html](http://www.eclipse.org/webtools/community/tutorials/BuildJ2EEWebApp/BuildJ2EEWebApp.html)


1.#lsb_release -d -s -c
Ubuntu 10.10  maverick

2. #/usr/sbin/apache2 -v
Server version: Apache/2.2.16 (Ubuntu)

3. #Eclipse>windows>preferences>Java>Installed_JREs:
Name: java-6-openjdk  Location: /usr/lib/jvm/java-6openjdkType:Standard VM

#Eclipse>windows>preferences>Server>RuntimeEnvironment 
Server Runtime Environment shows blank

Tried to add
Apache Tomcat v7.0
Browse :/etc/apache2   says:  Unknown version of Tomcat was specified.
JRE: java-6-openjdk(/workbench default)


Thanks

---

