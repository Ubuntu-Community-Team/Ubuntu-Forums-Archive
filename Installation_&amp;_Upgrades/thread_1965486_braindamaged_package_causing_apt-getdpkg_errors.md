---
title: "braindamaged package causing apt-get/dpkg errors"
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by strask on 2012-04-25
Ok, so I was stupid. I added a ppa and attempted to install a package that wasn't correctly made, and now I get errors every time I do ANY package management function.

I started the problem by typing these commands:```
sudo add-apt-repository ppa:eugenesan/java
sudo apt-get update 
sudo apt-get install oracle-java7-installer
```What seems to happen is that the package installs, then has a post-install or configuration script that tries to download the java installer from Oracle and run it, but the script fails because the installer doesn't download correctly (or something, the checksum doesn't match).

As a side note, if I had known that the package was just going to get the installer from Oracle, I would have gone and gotten it directly. :(

Anyway, now the package is left in a "half configured" state, according to dpkg --audit, and no matter what I try to do with it (configure, remove, etc.) it just runs the same script again and fails the same way. apt-get detects and complains about this problem every time I try to do anything, like install an unrelated package via Software Center. So every operation looks like a failure, even if it succeeds.

How do I do surgery on my system to remove this broken package? I have searched and not yet found a way to remove a half-configured package or get it out of the half-configured state.

Below is the errors it gets when I try to remove it:```
trask@reptoid:~$ sudo apt-get purge oracle-java7-installer
[sudo] password for trask: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  oracle-java7-installer*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 82.9 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 171317 files and directories currently installed.)
Removing oracle-java7-installer ...
update-alternatives: error: unknown argument `bootinfoscript'
dpkg: error processing oracle-java7-installer (--purge):
 subprocess installed pre-removal script returned error exit status 2
Downloading...
--2012-04-25 17:47:40--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 98.174.31.138, 98.174.31.91
Connecting to download.oracle.com (download.oracle.com)|98.174.31.138|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz [following]
--2012-04-25 17:47:40--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 184.51.30.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|184.51.30.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-04-25 17:47:41--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|98.174.31.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'

     0K .....                                                 100% 8.01M=0.001s

2012-04-25 17:47:41 (8.01 MB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
trask@reptoid:~$ 

```

---

### Post by strask on 2012-04-26
Solution, dangerous but worked for me:

Run the following to find all the files that were installed: 
dpkg --listfiles  
Then delete each one 

Edit the file /var/lib/dpkg/status 
Remove the section for your badly broken package (Make a backup before you edit the file!)  

Edit the file /var/lib/dpkg/available 
Remove the section for your badly broken package (Make a backup before you edit the file!)  

Found this solution at [http://linux.chrissweeney.co.uk/topic.php?t=18](http://linux.chrissweeney.co.uk/topic.php?t=18)

---

### Post by techsupport on 2012-04-26
Oh you don't want to use that PPA.  That one looked kinda shady, imho. Use this one instead:

```
sudo add-apt-repository ppa:webupd8team/java 
sudo apt-get update 
sudo apt-get install oracle-jdk7-installer
```But then again, they are recommending the OpenJDK 7 since it is essentially the same now after Oracle pulled the plug a few months ago with Ubuntu. And OpenJDK is in the Ubuntu repositories which makes it a breeze to install it on 12.04 LTS.

I mean, unless you are running something like Minecraft that explicitly requires Sun Java not OpenJDK, you don't need it.

> **strask said:**
> Solution, dangerous but worked for me:

Run the following to find all the files that were installed: 
dpkg --listfiles  
Then delete each one 

Edit the file /var/lib/dpkg/status 
Remove the section for your badly broken package (Make a backup before you edit the file!)  

Edit the file /var/lib/dpkg/available 
Remove the section for your badly broken package (Make a backup before you edit the file!)  

Found this solution at [http://linux.chrissweeney.co.uk/topic.php?t=18](http://linux.chrissweeney.co.uk/topic.php?t=18)

---

### Post by strask on 2012-04-26
> **techsupport said:**
> Oh you don't want to use that PPA.  That one looked kinda shady, imho. Use this one instead:
Meh. Now that I understand that the package just downloads the oracle installer and runs it, I might as well just do that myself, directly.

> But then again, they are recommending the OpenJDK 7 since it is essentially the same now after Oracle pulled the plug a few months ago with Ubuntu. And OpenJDK is in the Ubuntu repositories which makes it a breeze to install it on 12.04 LTS.

I mean, unless you are running something like Minecraft that explicitly requires Sun Java not OpenJDK, you don't need it.

That's all very true. :)

---

### Post by QIII on 2012-04-26
> **techsupport said:**
> Oracle pulled the plug a few months ago with Ubuntu. And OpenJDK is in the Ubuntu repositories which makes it a breeze to install it on 12.04 LTS.

Oracle pulled the plug on everyone, not just Ubuntu.

The problem with OpenJDK 7 is that even though it is the reference implementation for Java 7, most of the world does not realize that or recognize it as "Java".  There is more in the world that will not run with OpenJDK than what will.

Hopefully this will be rectified shortly as the world realizes this fact.

> **strask said:**
> Meh. Now that I understand that the package just  downloads the oracle installer and runs it, I might as well just do that  myself, directly.

The problem with that is that every time there is a Java update, you will have to* reinstall*  it yourself, directly.

The installer package from the webupd8team PPA (which actually works properly) will do that automatically during your normal updates when there is a new Java version available.

---

### Post by Dry Lips on 2012-04-30
> **techsupport said:**
> Oh you don't want to use that PPA.  That one looked kinda shady, imho. Use this one instead:

```
sudo add-apt-repository ppa:webupd8team/java 
sudo apt-get update 
sudo apt-get install oracle-jdk7-installer
```> **QIII said:**
> 
The problem with that is that every time there is a Java update, you will have to* reinstall*  it yourself, directly.

The installer package from the webupd8team PPA (which actually works properly) will do that automatically during your normal updates when there is a new Java version available.

Just to double check... The webupd8 ppa works with 12.04, right?

---

### Post by jafrelin on 2012-05-08
I am getting a bunch of error while trying to install.

Followed the directions above and got"

sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of oracle-jdk7-installer:
 oracle-jdk7-installer depends on oracle-java7-installer; however:
  Package oracle-java7-installer is not configured yet.
dpkg: error processing oracle-jdk7-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 oracle-java7-installer
 oracle-jdk7-installer


I suspecty there are multiple things that need to get untangled and start again.

Suggestions?

Thanks

---

### Post by strask on 2012-05-09
> **jafrelin said:**
> I am getting a bunch of error while trying to install.

Followed the directions above and got"

Hmm... *which* directions above did you follow already? Did you try to install from the eugenesan ppa, which is broken? Or did you try to install from the webupd8 ppa which people claim works?

Either way, I think at this point you probably need to follow the steps in the second post in this thread; I'll repeat them here:

Solution, dangerous but worked for me:

Run the following to find all the files that were installed: 
```
sudo dpkg --listfiles  oracle-jdk7-installer
```Then delete each one -- NOTE: Some of the items listed will be directories that contain more than just the package files; delete the individual listed files first and then delete directories only if they are empty!

Edit the file /var/lib/dpkg/status 
Remove the section for your badly broken package (Make a backup before you edit the file!)  

Edit the file /var/lib/dpkg/available 
Remove the section for your badly broken package (Make a backup before you edit the file!)

Finally, remember to remove the broken ppa from your configuration, I find it easiest to do this via the Software Sources gui.

---

### Post by jfrelin on 2012-05-11
Thanks perfect-  I usually hate to do the most dangerous things

---

### Post by johndpeterson on 2012-06-29
I know this thread is closed but I wanted to simply say thanks.  I made the same mistake - I used the same ppa and got the exact same errors.  ended up going the download, tar, and install route to get around it.  "Please note, this package does not contain any files. It contains a script to download the file from Oracle."

---

### Post by g34ncarlovinhal on 2012-07-03
I had the same problem and manual edition of files '/var/lib/dpkg/status' and '/var/lib/dpkg/available' was very simple and worked fine. Just some more details:

Command 'sudo dpkg --listfiles' doesn't returns anything, except that 'oracle-jdk7-installer' wasn't installed.

I had to delete from both files the references to 'oracle-jdk7-installer'. For example, from /var/lib/dpkg/status, I deleted:

```

Package: oracle-java7-installer
Status: purge ok half-configured
Priority: optional
Section: non-free/java
Installed-Size: 81
Maintainer: Alin Andrei <webupd8@gmail.com>
Architecture: all
Version: 7u3-0~eugenesan~precise4
Replaces: icedtea-6-plugin, icedtea-7-plugin, openjdk-6-jdk, openjdk-6-jre, openjdk-6-jre-headless, openjdk-7-jdk, openjdk-7-jre, openjdk-7-jre-headless, oracle-jdk7-installer, sun-java6-bin, sun-java6-jdk, sun-java6-jre
Provides: default-jre, default-jre-headless, java-jdk, java-runtime, java-runtime-headless, java-virtual-machine, java2-jdk, java2-runtime, java2-runtime-headless, java5-jdk, java5-runtime, java5-runtime-headless, java6-jdk, java6-runtime, java6-runtime-headless, java7-jdk, java7-runtime, java7-runtime-headless, oracle-java7, oracle-java7-plugin, oracle-jdk7-installer
Depends: java-common (>= 0.24), locales, debconf (>= 0.5) | debconf-2.0
Pre-Depends: wget
Recommends: gsfonts-x11
Suggests: binfmt-support, ttf-baekmuk | ttf-unfonts | ttf-unfonts-core, ttf-kochi-gothic | ttf-sazanami-gothic, ttf-kochi-mincho | ttf-sazanami-mincho, ttf-arphic-uming, firefox | firefox-2 | iceweasel | mozilla-firefox | iceape-browser | mozilla-browser | epiphany-gecko | epiphany-webkit | epiphany-browser | galeon | midbrowser | moblin-web-browser | xulrunner | xulrunner-1.9 | konqueror | chromium-browser | midori | google-chrome
Conflicts: j2se-common, oracle-jdk7-installer
Description: Sun Java(TM) Development Kit (JDK) 7
 The JDK(TM) is a development environment for building and running
 applications, applets, and components using the Java programming language.
 .
 The JDK(TM) includes Java Runtime Environment (JRE) for running applications,
 Java Plug-in for running applets in web browsers and tools useful for
 developing and testing programs written in the Java programming language.
 .
 Note that this package does not contain any software from Oracle. This
 package does however contain a script to download and install Oracle JDK 7.
 All information regarding Java itself can be found on this website:
 http://www.oracle.com/
Homepage: http://www.oracle.com/technetwork/java/javase/downloads/index.html
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a
Npp-Mimetype: application/x-java-vm, application/x-java-applet, application/x-java-applet;version=1.1, application/x-java-applet;version=1.1.1, application/x-java-applet;version=1.1.2, application/x-java-applet;version=1.1.3, application/x-java-applet;version=1.2, application/x-java-applet;version=1.2.1, application/x-java-applet;version=1.2.2, application/x-java-applet;version=1.3, application/x-java-applet;version=1.3.1, application/x-java-applet;version=1.4, application/x-java-applet;version=1.4.1, application/x-java-applet;version=1.4.2, application/x-java-applet;version=1.5, application/x-java-applet;version=1.6, application/x-java-applet;jpi-version=1.6.0_07, application/x-java-bean, application/x-java-bean;version=1.1, application/x-java-bean;version=1.1.1, application/x-java-bean;version=1.1.2, application/x-java-bean;version=1.1.3, application/x-java-bean;version=1.2, application/x-java-bean;version=1.2.1, application/x-java-bean;version=1.2.2, application/x-java-bean;version=1.3, application/x-java-bean;version=1.3.1, application/x-java-bean;version=1.4, application/x-java-bean;version=1.4.1, application/x-java-bean;version=1.4.2, application/x-java-bean;version=1.5, application/x-java-bean;version=1.6, application/x-java-bean;jpi-version=1.7.0_03
Npp-Name: The Java(TM) Plug-in, Java SE 7

```Sure, you have to edit files with su powers. For example: 
```
$ sudo emacs /var/lib/dpkg/status
```

---

