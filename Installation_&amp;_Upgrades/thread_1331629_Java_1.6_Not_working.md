---
title: "Java 1.6 Not working"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by Coach_Mark on 2009-11-19
I have Ubuntu 9.04 installed on a 64-bit laptop.  I have installed the latest java.  Synaptic says i have it installed.  Mozilla says the plugins are in place, and enabled.  Terminal confirms the version.  But, nothing that uses Java works.  All I get is a grey box with a circle and an arrow in it.  In a few cases, it opens the correct web page, but the page stays blank, and the bottom of the window says "done."  what the heck is going on, and how do I fix it?

---

### Post by Axos on 2009-11-19
To verify whether you installed the "Open" or "Sun" version of Java, please post the output of running the command...

java -version

---

### Post by Coach_Mark on 2009-11-19
OK.  my bad.  I did not read everything correctly.  here is my Java check:

mark@mark-laptop:~$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu12)
OpenJDK Server VM (build 14.0-b08, mixed mode)

why did the 64-bit download from Java not install?  hmmm...  hazards of being a noob, i guess.  i seem to recall reading somewhere that the 64-bit processors have trouble on Open JDK.  I'm fairly sure it means I have to install the 64-bit from Java.  but, after getting it, it doesn't seem to have installed.  so, where do i go from here?  (i still have a copy of the downloaded *.bin on my desktop..kept it in case i ever need it again, just haven't burned it to a disk yet)

---

### Post by Axos on 2009-11-19
I can help you but it will be a multi-step process because I am running 32-bit Ubuntu and do not have the OpenJDK installed.

When you say "from Java" I'm guessing you mean "from Sun". Yes, you need to download the file jdk-6u17-linux-x64.bin from [http://java.sun.com/javase/downloads/widget/jdk6.jsp](http://java.sun.com/javase/downloads/widget/jdk6.jsp) (choose the platform "Linux x64").

Once you download it, you need to make it executable:

chmod +x jdk-6u17-linux-x64.bin

Before you run it, cd to the directory where you want to install it. The installer will create a subdirectory within that directory and put all the files within it. It's very clean...it doesn't go splattering files all over your system. Therefore you don't (and shouldn't) have to run it with sudo. You can just install it in your home directory, if you like.

In the case of the 32-bit version, the installer creates a directory called jdk1.6.0_17. It's probably the same for the 64-bit version but I don't know for sure.

The next step is to edit your PATH so that the installation's bin directory is at the front of it because you want to run this version, not the OpenJDK version. If you are using GNOME (which is the default for Ubuntu), edit or create the file ~/.gnomerc and put something like this in it, modifying it to point to where you actually installed the JDK:

export PATH=/home/[user]/jdk1.6.0_17/bin:$PATH

Now log off and back on and open a terminal and run:

java -version

It should say something like this (probably different because I'm running the 32-bit version):

java version "1.6.0_17"
Java(TM) SE Runtime Environment (build 1.6.0_17-b04)
Java HotSpot(TM) Server VM (build 14.3-b01, mixed mode)

Once you've gotten this far, the next step is to remove the OpenJDK browser plugins. To help you with that, I need you to run the following commands and copy and paste the output into a post:

ls -lR /usr/lib/mozilla/plugins /usr/lib/firefox/plugins

The other command will need to be modified depending upon where you installed the Sun JDK. I need you to run a command which looks like this:

ls -lR /home/[user]/jdk1.6.0_17/jre/plugin/

That will show me what the name of Sun's 64-bit plugin is so I can give you a command to create a symbolic link to it.

---

### Post by Axos on 2009-11-20
I cannot believe it. I just discovered that Sun **still** does not support the browser plug-in on 64-bit Linux. They added 64-bit plug-in support for Windows ages ago (update 12). I moronically assumed they added Linux support at the same time. Gah!!! I'm learning it's never safe to assume **anything**.

Soooooo, you can run local Java apps but you cannot see any Java applets on web pages.

Here's what Sun has to say:

"For Java Plug-in and Java Web Start on 64-bit Linux systems, support is not offered at this time."

[http://java.sun.com/javase/6/webnotes/install/system-configurations.html#deployment-footnotes](http://java.sun.com/javase/6/webnotes/install/system-configurations.html#deployment-footnotes)

---

### Post by Axos on 2009-11-23
I just learned that there really is a 64-bit plug-in for Linux. The information on Sun's site is apparently out of date.

This post has a link to a site with complete instructions:

[http://ubuntuforums.org/showpost.php?p=8372094&postcount=4](http://ubuntuforums.org/showpost.php?p=8372094&postcount=4)

---

