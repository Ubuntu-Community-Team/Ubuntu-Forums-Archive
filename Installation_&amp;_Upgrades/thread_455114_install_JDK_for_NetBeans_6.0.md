---
title: "install JDK for NetBeans 6.0"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by larry wales on 2007-05-26
Hello,

I've been trying, off and on, to install the NetBeans 6.0 m9 preview on my computer over the past 2 weeks without success.  When I run the downloaded .sh file, I get the following message in the terminal:

[INDENT]Configuring installer...
Search JVM on the system...
Java SE Development Kit (JDK) was not found on this computer
JDK 6 or JDK 5 is required for installing the NetBeans IDE. Make sure that the JDK is properly installed and run installer again.
You can specify valid JDK location using --javahome installer argument.

To download the JDK, visit http//java.sun.com/javase/downloads
[/INDENT]

However, I have JDK 6.0 already installed, (sun-java6-jdk, sun-java6-jre have been installed through Synaptic).

Also, when I perform the following terminal command:

[INDENT]sudo update-alternatives --config java[/INDENT]

I get the following path:

[INDENT]/usr/lib/jvm/java-6-sun/jre/bin/java[/INDENT]

So, could anyone please tell me why the installer can't detect the JDK?

thank you,
larry

---

### Post by Iztari on 2007-05-27
Hello, I have exactly the same problem an I can't fix it, i already tried with 
```
sudo update-alternatives --config java
```
Here is my java -version display:
```
iztari@iztari-laptop:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)
```
Thanks for anyone who can help... I've had this problem for months now.

---

### Post by larry wales on 2007-05-27
I finally managed to install by entering in the terminal:

[INDENT]sh netbeans-6.0m9-full-linux.sh --javahome /usr/lib/jvm/java-6-sun[/INDENT]

I then had a blank monochrome display for the user license window.  I solved this by turning off Desktop Effects.

hth,
larry

---

### Post by kiwinewt on 2007-05-28
I'm with Iztari on this. Does anyone know how to get it working with Ubuntu64? I have managed to get it past the searching for jvm stage, it continuously comes up with errors about not being able to initialize on a 64-bit system.

Please help - I need this for college and am lost.

Nate

---

### Post by olafkock on 2007-06-01
As written in [http://ubuntuforums.org/showthread.php?p=2760135&posted=1#post2760135](http://ubuntuforums.org/showthread.php?p=2760135&posted=1#post2760135) I've needed to use a 32bit vm to run the netbeans6 installer. This solved my problems.
It seems that netbeans runs with the preinstalled jdk as it's configurable during the installation process.

Cheers,
Olaf

---

### Post by albaneze on 2007-06-01
I Managed to install Netbeans 6 preview 9 .

I tried as root and it didnt work but what i tried as a normal user it did work.

the command is 

sh netbeans-6.0m9-standard-linux.sh --javahome /usr/lib/jvm/java-6-sun

as the previous user suggested. 

Cheers to everyone.

---

### Post by Iztari on 2007-06-04
I get this error when I the wizard starts after I use this command:
```
sh netbeans-6.0m9-standard-linux.sh --javahome /usr/lib/jvm/java-6-sun
```

Error:
[IMG]http://bp0.blogger.com/_LWym0gOZbAY/RmOgMgi1SnI/AAAAAAAAAFI/Qy9cYYEMxYE/s320/Screenshot.png[/IMG]

---

### Post by kiwinewt on 2007-06-04
Yeah thats the error I get. I still have no clue what it means...

---

### Post by vilotip on 2008-03-12
first goto the directory where yor netbeans 6.0 for linux installer is located...in the terminal

then in the terminal type
sh /*name of installer file*/ --javahome /*address of location where yor JRE is located*/

/*  */ -signifies comments...ofcourse

---

