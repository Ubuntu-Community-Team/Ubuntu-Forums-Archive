---
title: "Red5 installation on 10.10"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by jovemac on 2010-10-25
Dear all!
 
I have upgraded to ubuntu 10.10 desktop version. Looking for to install RED5 in my exisiting OS. I'm new to Linux. Brief assistance is appricated.
 
Thanks in advance.

---

### Post by jovemac on 2010-10-27
Hi!

I myself managed to install RED5 on my current ubuntu maverick installation.

Step 1:

Install required Libraries..


01    apt-get update
02    apt-get install java-package ( Skip this step if it dosnt gives output)
03    apt-get install sun-java6-jdk
04    apt-get install sun-java6-jre
05    apt-get install ant
06    apt-get install subversion

Step 2:

Download and install RED5


01    wget [http://www.red5.org/downloads/0_9/red5-0.9.0.tar.gz](http://www.red5.org/downloads/0_9/red5-0.9.0.tar.gz)
02    tar xvfz red5-0.9.0.tar.gz
03    mv red5-0.9.0 red5
04    mv red5 /usr/share/


Step 3:

Test the installation.

01    cd /usr/share/red5
02    sh red5.sh

You should see a bunch of text appear, the last line looking like:

    [INFO] [Launcher:/installer] org.red5.server.service.Installer – Installer service created

Now try going to [http://your-server-address:5080](http://your-server-address:5080) in a web-browser. You should see:

This page is used to test the proper operation of the Red5 server after it has been installed. If you can read this page it means that the Red5 server installed at this site is working properly. 

Done...

---

### Post by Sylslay on 2010-10-27
Great post for new user on forum:

step by step.

THX:popcorn:

2min , after:
WOW - You learnt Yourself.

---

