---
title: "Server 6.06 X fowarding help to install JBOSS"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by mikeh883 on 2006-08-06
Hello everyone... I have been beating my head against this for a while now and am looking for some help. I am trying to create an application server for home development projects. 

I have installed Ubuntu Server 6.06 (LAMP Server), Java 1.5, and am now trying to install JBOSS Application server. The problem is that it requires a GUI for installion. I am now trying to fight through the X11 forwarding issues to get this installed. I think I am getting closer. X11 fowarding is enabled in my sshd_config. Here is  what I have added to my profile:

export JAVA_HOME="/usr/lib/jdk"
export PATH=$JAVA_HOME/bin:$PATH
export DISPLAY=192.168.0.3

and here is my current error:
mike@homer:~$ java -jar jboss-4.0.4.GA-Patch1-installer.jar
Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/lib/jdk1.5.0_07/jre/lib/i386/xawt/libmawt.so: libXext.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1647)
        at java.lang.Runtime.load0(Runtime.java:769)
        at java.lang.System.load(System.java:967)
...........

This file does not exist: libXext.so

and now I am starting to wonder if I have been going down the wrong path... I am using putty to connect from an XP machine. Here is part of the log file:
2006-08-06 10:10:01	Access granted
2006-08-06 10:10:01	Opened channel for session
2006-08-06 10:10:01	Requesting X11 forwarding
2006-08-06 10:10:01	Remote debug message: No xauth program; cannot forward with spoofing.
2006-08-06 10:10:01	X11 forwarding refused
2006-08-06 10:10:01	Allocated pty (ospeed 38400bps, ispeed 38400bps)
2006-08-06 10:10:02	Started a shell/command
 I have X11 forwarding enabled and have tried both of the protocols...

If anyone can give me some advice I would greatly appreciate it...

Thanks, Mike

---

### Post by mikeh883 on 2006-08-06
bump...

---

### Post by calenti on 2006-08-27
Probably too late for you, but as I recall JBoss had a zip-only installer that you could just unpack and run. By executing the jar you're trying to fire up the Swing client.

I am looking to do the same thing you are, so I am trying to download the zip 4.0.4 version. I think all you have to do is unpack that on your server,set JAVA_HOME and execute run (for the default level). I'll post a followup on how that goes.

---

### Post by mjbarker1 on 2007-04-18
do this -
on a separate computer  - open up a terminal window
Type: *ssh username@192.168.0.1*    (change this to your username and your ip address)
then type: *sudo apt-get install xauth*   (software to forward GUI stuff)
then type: *exit*   (exit out of the text only ssh session)
then type: *ssh -X -Y username@192.168.0.1*  (this will log you into your server and forward all GUI stuff to the computer in front of you)
then type: *cd /the/path/to/jboss/bin*    (make sure to cd into the bin folder in the jboss download diretory)
then type: *sh run.sh*   (this is the install script - you may have to be root)

you have probably already figured out a way to install your software, but in case anyone else is curious here is a method that has worked for me for variuos other software installations.  MythTV and OpenbravoERP come to mind.

---

### Post by g[r]eek on 2007-07-05
the gui install mode is only needed to allow the user to specify a couple of options, such as which install type (all, ejb3, default, minimal etc...) as well as the destination folder.

you can specify these as command-line arguments however, in which case the gui is not required. this is how i installed jboss using command-line only (i too use the 6.06 server edition):

```
java -jar jems-installer-xxx.jar -installGroup default installpath=/home/username/jbossfolder
```

bear in mind that this assumes you are using the default install.

hope this helps.

---

