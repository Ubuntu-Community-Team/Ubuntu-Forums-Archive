---
title: "java installation for total noob"
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by rialfred on 2012-03-13
Can someone help me get java running on this pen stick installation of ubuntu?  I just annot get it running, I have downloaded and followed some instructions but got in a bit of a mess with it as nothing seems straight forward to me

would appreciate some help

thanks in advance
Fred

---

### Post by ajgreeny on 2012-03-13
What version of ubuntu, and also which java packages are you trying to install? The sun-java packages that used to be included in the repos are not there any more and for sun-java you will need to follow the instructions in [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Do you really need the sun-java packages?  In the past I always used them as my bank website would not work with the openjdk version. Now, however that is not a problem; either the bank site has accepted the openjdk java, or openjdk has become much better than it used to be.

---

### Post by rialfred on 2012-03-15
hey thanks for the reply, i am trying to use a mail applet that just doesnt seem to work no matter what, when i go to this page [http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_24&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=3.2.0-18-generic-pae](http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_24&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=3.2.0-18-generic-pae)

i get this Verifying Java Version 
 A newer version of Java is available 

 Please click the download button to get the recommended Java for your computer. 
Your Java version: Version 6 Update 24

the problem is i have absolutely no clue what i am doing with cmd line or anything really, ive tried downloading a few things, just cannot get it to work at all

would appreciate a true idiots run through of how i remove whatever i have and how i install a different version so then i can try it??

thank you

---

### Post by rialfred on 2012-03-15
ubuntu 12.04lts 32bit if that helps

---

### Post by sammiev on 2012-03-15
Read post#2 it's the one I use.

---

### Post by BezoBT on 2012-03-15
hey maybe i can help you. I had install java with this way on my Bt5. Maybe its working by you. ;)

1. open terminal

2. Close firefox ```
killall -9 /opt/firefox/firefox-bin
```3. Downloading java  ```
wget http://javadl.sun.com/webapps/download/AutoDL?BundleId=52240 -O /tmp/java.bin
```4.Creating the directories and running the self extraction
```
mkdir -p /opt/java && cd /opt/java
``````
chmod +x /tmp/java.bin && /tmp/java.bin
```5. Update java  
```
update-alternatives --install /usr/bin/java java /opt/java/jre1.6.?_??/bin/java 1 
``````
update-alternatives --set java /opt/java/jre1.6.?_??/bin/java
```6.Adding the plugin to Firefox
```
mkdir -p /usr/lib/mozilla/plugins/
``````
ln -sf /opt/java/jre1.6.?_??/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins/
``````
export JAVA_HOME=”/opt/java/jre1.6.?_??/bin/java”
```7. Plugin test
```
firefox http://java.com/en/download/testjava.jsp
```

---

### Post by rialfred on 2012-03-15
I was following post 2, i got to download the file, then move after creating directories, then when i try to execute i get the following mess.

ubuntu@ubuntu:/opt/java/32$ sudo ./jre-6u31-linux-i586.rpm
./jre-6u31-linux-i586.rpm: 1: ./jre-6u31-linux-i586.rpm: &#65533;&#65533;&#65533;&#65533;jre-1.6.0_31-fcs&#65533;P: not found
./jre-6u31-linux-i586.rpm: 118: ./jre-6u31-linux-i586.rpm: Syntax error: "(" unexpected
ubuntu@ubuntu:/opt/java/32$ 


32 was exchanged for 64 in the tutorial as i was using 32 bit, for some reason the folder also now looks very messy

---

### Post by rialfred on 2012-03-15
BezoBT on following your instructions i got stuck here

ubuntu@ubuntu:~$ ln -sf /opt/java/jre1.6.?_??/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins/
ln: failed to create symbolic link `/usr/lib/mozilla/plugins/libnpjp2.so': Permission denied
ubuntu@ubuntu:~$

---

### Post by rialfred on 2012-03-15
arghhhhhhhhhhh how can anything be so messy!! just cannot get it to work, really would like to get to know this os more but, this is just beyond recognition for me!

---

