---
title: "Install openfire 3.7,1 on ubuntu server 12.04 64 bit"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by fulllefty on 2012-05-01
Hi all, what I want to do is install **openfire** from **deb package** on my ubuntu 12.04 server 64 bit. Openfire basic, with no plugin installed.

Here list of way that works for me:

1.Install java (I use sun java 6 update 32 binary package 64bit)
 I'm following this article
 [https://github.com/flexiondotorg/oab-java6/blob/a04949f242777eb040150e53f4dbcd4a3ccb7568/README.rst]("https://github.com/flexiondotorg/oab-java6/blob/a04949f242777eb040150e53f4dbcd4a3ccb7568/README.rst")

run the script, wait (if you want you can open another terminal session to know what process running)
cause in my case the first step is the longest one (downloading about 300 library package)
If the script success in creating package, then you could run apt-get

```
# apt-get install sun-java6-jdk
```

 Then check the java & javac in terminal.

```
# java -version
java version "1.6.0_32"
Java(TM) SE Runtime Environment (build 1.6.0_32-b05)
Java HotSpot(TM) 64-Bit Server VM (build 20.7-b02, mixed mode)

# javac -version
javac 1.6.0_32

```

if the output looks like above (or another variant, depend on your installed java version) then java packaged installed correctly

2.Create table on mysql for openfire
```
# mysql -u root -p;
#mysql > CREATE DATABASE openfire;
#mysql > quit;
```

3.Download the openfire 3.7.1 .deb package from [http://www.igniterealtime.org/downloads/index.jsp]("http://www.igniterealtime.org/downloads/index.jsp")
I get the openfire_3.7.1_all.deb, put it on /opt
now when I try to install using this command:
```
# dpkg -i openfire_3.7.1_all.deb
```

I am no longer get this error:
```
dpkg: regarding openfire_3.7.1_all.deb containing openfire, pre-dependency problem:
 openfire pre-depends on sun-java5-jre | sun-java6-jre | default-jre-headless
  sun-java5-jre is not installed.
  sun-java6-jre is not installed.
  default-jre-headless is not installed.
dpkg: error processing openfire_3.7.1_all.deb (--install):
 pre-dependency problem - not installing openfire
Errors were encountered while processing:
 openfire_3.7.1_all.deb

```

continue the install process in browser.

all happy & running. :p

---

### Post by fulllefty on 2012-05-01
After another browsing session, get to this article
[https://github.com/flexiondotorg/oab-java6/blob/a04949f242777eb040150e53f4dbcd4a3ccb7568/README.rst]("https://github.com/flexiondotorg/oab-java6/blob/a04949f242777eb040150e53f4dbcd4a3ccb7568/README.rst")

run the script, waiting for the java package created
then run apt-get
```
# apt-get install sun-java6-jdk
```
java run well, then

step install openfire could be executed. no more dependency error

---

### Post by gdi2k on 2012-05-02
Thank you, just what I was looking for. 

Are you using Fastpath / Webchat plugins by any chance? I can get things set up ok, but things don't actually work the way they're supposed to (queue rules not being honored, incorrect presence in Fastpath queues etc.). Reinstalling now to see if maybe I borked something there...

Any experience that functionality?

---

### Post by fulllefty on 2012-05-02
I'm glad this could help :p

But, sorry I couldn't help furthermore, cause I still don't have experience using fastpath/webchat plugin.

Maybe somebody could fill me in?

---

### Post by thunder63cs on 2012-05-29
tryign to install openfire and running into issues : 
 
 
I have it installed yet can not seem to access it to finish the config in a web browser?
 
 
Thanks for the help found the issue with the javac version...

---

### Post by christiaan_ on 2012-11-15
Complete instructions can be found here:

[How to setup an Instant Messaging server using Openfire on Ubuntu 12.04]("http://www.thefanclub.co.za/how-to/how-setup-instant-messaging-server-using-openfire-ubuntu-1204")

---

