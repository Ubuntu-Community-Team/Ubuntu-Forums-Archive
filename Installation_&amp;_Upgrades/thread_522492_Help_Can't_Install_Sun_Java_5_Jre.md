---
title: "Help Can't Install Sun Java 5 Jre"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by signjguy101 on 2007-08-10
I'm trying to install sun java 5 jre for for Playstation 3 xubuntu 7.04 feisty fawn. it says package is broken from the terminal, or the dependency are not satisfiable when i try to debian. It won't work from the synaptic manager either, do I have the wrong sun java 5.

---

### Post by Pumalite on 2007-08-10
What do you mean by ' it doesn't work from Synaptic'?

---

### Post by stchman on 2007-08-10
> **signjguy101 said:**
> I'm trying to install sun java 5 jre for for Playstation 3 xubuntu 7.04 feisty fawn. it says package is broken from the terminal, or the dependency are not satisfiable when i try to debian. It won't work from the synaptic manager either, do I have the wrong sun java 5.

Try this line:

```

sudo apt-get -y install sun-java5-bin sun-java5-jre sun-java5-jdk sun-java5-fonts sun-java5-plugin

```

---

### Post by signjguy101 on 2007-08-10
when i try to install it from the synaptic manager it says unresolvable dependency.

---

### Post by Pumalite on 2007-08-10
That's weird. I hope stchman has the answer.

---

### Post by Pumalite on 2007-08-10
I can contribute with this: [https://www.centos.org/modules/newbb/viewtopic.php?forum=28&topic](https://www.centos.org/modules/newbb/viewtopic.php?forum=28&topic)

I hope it helps.

---

### Post by signjguy101 on 2007-08-10
stchman I did what you said, but it says 

oot@joshua-desktop:~# sudo apt-get -y install sun-java5-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java5-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  sun-java5-jre
E: Package sun-java5-bin has no installation candidate
root@joshua-desktop:~# pt-get -y install sun-java5-bin sun-java5-jre sun-java5-jdk sun-java5-fonts sun-java5-plugin
bash: pt-get: command not found
root@joshua-desktop:~# sudo apt-get -y install sun-java5-bin sun-java5-jre sun-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java5-bin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  sun-java5-jre
E: Package sun-java5-bin has no installation candidate

---

### Post by Pumalite on 2007-08-10
Did you run the command with the package suggested?

---

### Post by signjguy101 on 2007-08-10
ya I tried that did not work it says : Package sun-java5-bin has no installation candidate.

---

### Post by Pumalite on 2007-08-10
I meant sun-java5-jre

---

### Post by signjguy101 on 2007-08-10
ya I tried that already.

---

### Post by Pumalite on 2007-08-10
That's funny because your error message concluded at the end that sun-java5-jre replaced sun-java5-bin.??

---

### Post by DGentry on 2007-08-10
I had the same problem as you. I finally found this web page that did it with no muss and no fuss.. just follow from 5 onwards...

Installing Sun Java on Ubuntu

   1. Note: these instructions give detailed steps for installing Sun Java following a recent installation of Ubuntu. Before you install any new operating systems please make sure you have a backup of data that you want to save. Note: Java and Ubuntu developers may find Installing Sun Java Development Tools on Ubuntu useful
   2. As of this writing the latest development version of Ubuntu is the Ubuntu 6.06 LTS Release Candidate (Dapper).
   3. Burn a Desktop (Live) CD of Ubuntu from [http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/). For most computers this will likely be the PC (Intel x86) desktop CD image.
   4. Restart your computer with the Ubuntu Live CD. After the user interface is ready, double click on the "Install" icon to install Ubuntu to your hard disk. Please consult the Ubuntu documentation for details on installation. During the installation you will create a normal user account to log in to your system (hint: remember your username and password as this information will be required to administer the system).
   5. After Ubuntu has been installed on your computer can install new software from the "Applications | Add/Remove Programs" menu option:
      [install Sun Java on Ubuntu image 15]

   6. Click "Show unsupported applications" and "Show commercial applications" and then Enter "Sun Java" in the Search: box in the Add/Remove Applications program:
      [install Sun Java on Ubuntu image 16]

   7. Click on "Sun Java 5.0 Runtime" to install Sun Java. You will need to enable the multiverse component as shown here (what are components?):

      [install Sun Java on Ubuntu image 17]

   8. Then click OK to install Sun Java. During the installation you will be prompted to accept the DLJ (Sun's EULA for Java):
      [install Sun Java on Ubuntu image 19]

   9. To integrate the Sun Java Plug-in with web browsers like Firefox open a terminal window (Applications | Accessories | Terminal) and type the following:

      myname@laptop:~$ sudo apt-get install sun-java5-plugin
      Password:
      Reading package lists... Done
      Building dependency tree... Done
      The following NEW packages will be installed:
        sun-java5-plugin
      0 upgraded, 1 newly installed, 0 to remove and 30 not upgraded.
      Need to get 0B/1334B of archives.
      After unpacking 65.5kB of additional disk space will be used.
      Selecting previously deselected package sun-java5-plugin.
      (Reading database ... 73800 files and directories currently installed.)
      Unpacking sun-java5-plugin (from .../sun-java5-plugin_1.5.0-06-1_i386.deb) ...
      Setting up sun-java5-plugin (1.5.0-06-1) ...

      myname@laptop:~$

  10. After the installation is complete you can (re-)start the Firefox browser and enter the URL "about:plugins" to verify that the Java Plug-in has been installed
      ( Note: for the JRE JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun/jre ):
      [install Sun Java on Ubuntu image 14]

---

### Post by DGentry on 2007-08-10
Here's the web page link that was so helpful for me when I was trying to install java.

[https://jdk-distros.dev.java.net/ubuntu.html](https://jdk-distros.dev.java.net/ubuntu.html)

---

### Post by signjguy101 on 2007-08-10
so what it sounds like is sun java 5 jre won't run on xubuntu feist fawn 7.04. this is were I installed it from [http://psubuntu.com/installation-instructions/](http://psubuntu.com/installation-instructions/).

---

