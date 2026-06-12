---
title: "run.sh error?"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by Whats smite on 2010-01-17
Hey , ive tryed to install this bot for a online game ( runescape ) but when i try to run the run-linux.sh file i get this error

```
root@mod-laptop:/home/mod/Desktop/botcient# ./run.sh
Unrecognized option: -XstartOnFirstThread
Could not create the Java virtual machine.

```
can anyone he\p thank you

---

### Post by cariboo on 2010-01-17
What happens if you try to run the script as a normal user?

---

### Post by Whats smite on 2010-01-17
> **cariboo907 said:**
> What happens if you try to run the script as a normal user?


Same thing comes up

---

### Post by zaksworld on 2010-01-17
Which client is it?
Also, could you please open up run.sh in gedit, so we can see what run.sh is trying to do with which files.  Thanks

---

### Post by Whats smite on 2010-01-17
> **zaksworld said:**
> Which client is it?
Also, could you please open up run.sh in gedit, so we can see what run.sh is trying to do with which files.  Thanks


```
java -XstartOnFirstThread -Xmx1000m -Xbootclasspath/p:"/home/mod/Desktop/botcient/./jars/org.eclipse.jface_3.5.0.I20090313-0100.jar":"/home/mod/Desktop/botcient/./jars/org.eclipse.osgi_3.5.0.v20090311-1300.jar":"/home/mod/Desktop/botcient/./jars/JGoodies-forms-1.2.1.jar":"/home/mod/Desktop/botcient/./jars/org.eclipse.equinox.common_3.5.0.v20090310-1800.jar":"/home/mod/Desktop/botcient/./jars/tools.jar":"/home/mod/Desktop/botcient/./jars/bergCoder1273.jar":"/home/mod/Desktop/botcient/./jars/JGoodies-looks-2.2.2.jar":"/home/mod/Desktop/botcient/./jars/swing-layout-1.0.3.jar":"/home/mod/Desktop/botcient/./jars/install.jar":"/home/mod/Desktop/botcient/./jars/org.eclipse.core.commands_3.5.0.I20081202-0800.jar":"/home/mod/Desktop/botcient/./jars/swt-3.6-Linux-GTK-64bit.jar":"/home/mod/Desktop/botcient/./jars/nexus21.240.jar":"/home/mod/Desktop/botcient/./jars/sqlitejdbc-3.6.14.2-Universal.jar": impsoft.nexus.installer.Main 
```

erm client is rsbots/nexus btw its called botcient cos my l key doesnt work

---

### Post by zaksworld on 2010-01-17
Two last questions:
What site did you get the client from?
Is this for the actual runescape game, or for a runescape private server?

---

### Post by Whats smite on 2010-01-17
> **zaksworld said:**
> Two last questions:
What site did you get the client from?
Is this for the actual runescape game, or for a runescape private server?


its a bot client for runescape you download then you buy codes to enter into the client to auto on runescape . and rsbots.net

do you have any idea why its saying it ?

---

### Post by zaksworld on 2010-01-17
It's giving you that error because the code to run it in linux isn't written right.
The command ```
-XstartOnFirstThread
``` isn't a command for Java in linux, so it won't work.

I'm trying to figure out a way to get all of your .jar files to work at once like your script is trying to do.

---

### Post by Whats smite on 2010-01-17
> **zaksworld said:**
> It's giving you that error because the code to run it in linux isn't written right.
The command ```
-XstartOnFirstThread
``` isn't a command for Java in linux, so it won't work.

I'm trying to figure out a way to get all of your .jar files to work at once like your script is trying to do.


oh thank you btw this may be some use

[http://www.rsbots.net/manuals/Bot-Client-Installation-Manual-for-Mac/](http://www.rsbots.net/manuals/Bot-Client-Installation-Manual-for-Mac/)

i done that.

---

### Post by zaksworld on 2010-01-17
Alright, everything's all set.  Just open up your run.sh file in gedit, then erase all the code in there and put this code in instead:
```
java -Xmx1000m -Xbootclasspath/p:"/home/mod/Desktop/botclient/./jars/install.jar":"/home/mod/Desktop/botclient/./jars/org.eclipse.equinox.common_3.5.0.v20090310-1800.jar":"/home/mod/Desktop/botclient/./jars/org.eclipse.core.commands_3.5.0.I20081202-0800.jar":"/home/mod/Desktop/botclient/./jars/JGoodies-looks-2.2.2.jar":"/home/mod/Desktop/botclient/./jars/swing-layout-1.0.3.jar":"/home/mod/Desktop/botclient/./jars/JGoodies-forms-1.2.1.jar":"/home/mod/Desktop/botclient/./jars/bergCoder1273.jar":"/home/mod/Desktop/botclient/./jars/tools.jar":"/home/mod/Desktop/botclient/./jars/org.eclipse.jface_3.5.0.I20090313-0100.jar":"/home/mod/Desktop/botclient/./jars/org.eclipse.osgi_3.5.0.v20090311-1300.jar":"/home/mod/Desktop/botclient/./jars/swt-3.6-Linux-GTK-32bit.jar":"/home/mod/Desktop/botclient/./jars/nexus21.240.jar":"/home/mod/Desktop/botclient/./jars/sqlitejdbc-3.6.14.2-Universal.jar": impsoft.nexus.installer.Main 
```
and save the file.  Now just double click on run.sh and click on run.
This should work.
Please post the results!

---

### Post by Whats smite on 2010-01-17
> **zaksworld said:**
> Alright, everything's all set.  Just open up your run.sh file in gedit, then erase all the code in there and put this code in instead:
```
java -Xmx1000m -Xbootclasspath/p:"/home/mod/Desktop/botclient/./jars/install.jar":"/home/mod/Desktop/botclient/./jars/org.eclipse.equinox.common_3.5.0.v20090310-1800.jar":"/home/mod/Desktop/botclient/./jars/org.eclipse.core.commands_3.5.0.I20081202-0800.jar":"/home/mod/Desktop/botclient/./jars/JGoodies-looks-2.2.2.jar":"/home/mod/Desktop/botclient/./jars/swing-layout-1.0.3.jar":"/home/mod/Desktop/botclient/./jars/JGoodies-forms-1.2.1.jar":"/home/mod/Desktop/botclient/./jars/bergCoder1273.jar":"/home/mod/Desktop/botclient/./jars/tools.jar":"/home/mod/Desktop/botclient/./jars/org.eclipse.jface_3.5.0.I20090313-0100.jar":"/home/mod/Desktop/botclient/./jars/org.eclipse.osgi_3.5.0.v20090311-1300.jar":"/home/mod/Desktop/botclient/./jars/swt-3.6-Linux-GTK-32bit.jar":"/home/mod/Desktop/botclient/./jars/nexus21.240.jar":"/home/mod/Desktop/botclient/./jars/sqlitejdbc-3.6.14.2-Universal.jar": impsoft.nexus.installer.Main 
```and save the file.  Now just double click on run.sh and click on run.
This should work.
Please post the results!

OMG OMG OMG GODDD <33333 thank you :)!

---

