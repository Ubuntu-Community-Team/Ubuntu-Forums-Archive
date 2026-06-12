---
title: "Java installation lock-up"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by davidwfox on 2007-06-10
A few days ago I visited a website that needed the Java runtime environment. I downloaded the Linux version from Sun, ran the installation programme, carefully followed all the directions, created a symbolic link, ..etc.., and finally reached the point where I had to enter my root password. As per the Ubuntu directions, "As default Ubuntu has no password set for the root user. To gain root access you have to type in your own user password. This is the password you set for the first user while installing Ubuntu." When I entered my password I got an error message saying that the password was wrong. I finally had to abort the attempted installation.

The aborted installation has seemingly locked up the package installer, but I don't know which one was trying to do the install. I've browsed the forums and looked at #404876 and #461153. I've tried the various suggestions:-   dpkg --configure -a   and    sudo aptitude update && sudo aptitude upgrade     and     sudo apt-get update    and whatever else looked like it was worth trying, but nothing has helped.

I've tried a subsequent install of another downloaded package, that tries to install with GDebi package manager, and that gives an error pop-up saying that "Only one software management tool is allowed to run at the same time. Please close the other application manager." I'd love to, but which manager?? And how do I close it?? And then, how do I actually get the JRE to install properly?

This is all very new to me, as my bean count clearly shows. Clear guidance in plain language will be very much appreciated.

David Fox

---

### Post by taurus on 2007-06-10
What happens when you run these two commands from a terminal?

```
sudo dpkg --configure -a
sudo apt-get update
```

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by davidwfox on 2007-06-10
Taurus - you rock!! No wonder you're a Master Roaster.

What a difference it makes when "sudo" is put in front of dpkg --configure ....etc..

The result:
~$ sudo dpkg --configure -a
Password:
Setting up java-common (0.25ubuntu2) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

Many thanks.  Now I'll try installing the other, previously blocked, apps.
David

---

### Post by davidwfox on 2007-06-10
Taurus
Sadly, my euphoria was short-lived. After the apparent success of installing the JRE, and re-booting, I logged on to one of the websites that I knew needed Java and what do I find? Missing plug-ins! Needless to say, it's missing Java.

Secondly, I started the installation of Opera (that was the "another downloaded package" that I referred to in my initial post). All went well until it reached the point of loading / installing dependencies, that again referring to the JRE. At that point the installation froze. To clear it I had to re-boot.

I then tried your two queries. This shows the end of:
sudo apt-get update
followed by:
sudo dpkg --configure -a

Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources              
Fetched 3B in 8s (0B/s)                                                        
Reading package lists... Done
david@david-laptop:~$ sudo dpkg --configure -a
david@david-laptop:~$ sudo dpkg --configure -a
david@david-laptop:~$ 


What do I try next?

David

---

### Post by davidwfox on 2007-06-11
The following may provide some further clues as to where my problem is coming from:
1.  Applications -> Add/remove... shows, under Installed Applications, Sun Java5 Runtime ticked
2.  Any attempt to install Opera hangs the installation at Installing dependencies - preparing sun-java5-bin.
3.  I've now discovered the terminal window during the installation. At the point where installation hangs, the terminal reads:
dpkg: serious warning: files list file for package 'sun-java5-jre' missing, assuming package has no files currently installed.
88254 files and directories currently installed.)
Preparing to replace sun-java5-bin 1.5.0-11-1ubuntu2 (using .../sun-java5-bin_1.5.0-11-1ubuntu2_i386.deb) ...
debconf: unable to initialise front end: dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Configuring sun-java5-bin
------------------------------------------------
and that's where it sits until I shut down.

Hope that helps.

---

