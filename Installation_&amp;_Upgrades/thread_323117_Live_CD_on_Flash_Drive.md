---
title: "Live CD on Flash Drive"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by nhandler on 2006-12-21
I just got a 2GB flash drive. I was wondering if it is possible to put the Ubuntu live cd on it. I don't mean store the iso file. I mean make it so I can boot off the flash drive and get the ubuntu live cd desktop. Is this possible? If so, how?

---

### Post by meng on 2006-12-21
Try looking at:
[www.pendrivelinux.com](www.pendrivelinux.com)
there are tutorials for how to do this with other Linux distros (I don't think Ubuntu is one of them, unless it's been added recently). The tutorials are mostly identical, use the same technique.

---

### Post by nhandler on 2006-12-21
> **meng said:**
> Try looking at:
[www.pendrivelinux.com](www.pendrivelinux.com)
there are tutorials for how to do this with other Linux distros (I don't think Ubuntu is one of them, unless it's been added recently). The tutorials are mostly identical, use the same technique.

They mention using syslinux.exe to do something. How would I do that on linux?

---

### Post by 454redhawk on 2006-12-21
> **Cheater said:**
> I just got a 2GB flash drive. I was wondering if it is possible to put the Ubuntu live cd on it. I don't mean store the iso file. I mean make it so I can boot off the flash drive and get the ubuntu live cd desktop. Is this possible? If so, how?


This is EXACTLY what you are looking for and the persistance lets you save changes.

[http://www.ubuntuforums.org/showpost.php?p=1062799&postcount=100]("http://www.ubuntuforums.org/showpost.php?p=1062799&postcount=100")

---

### Post by nhandler on 2006-12-21
> **454redhawk said:**
> This is EXACTLY what you are looking for and the persistance lets you save changes.

[http://www.ubuntuforums.org/showpost.php?p=1062799&postcount=100]("http://www.ubuntuforums.org/showpost.php?p=1062799&postcount=100")

That still involves windows (and looks more complex).


Is there a way to get around using syslinux.exe (like the pendrivelinux.org said to use)? That site seemed a lot easier. It just uses a windows application.

---

### Post by meng on 2006-12-21
syslinux exists on linux, probably installed by default, so you'd use the same commands.
as for creating a partition, use fdisk /dev/sda (replace sda with whatever the device name of your pendrive is)
as for formatting the partition, if you are formatting to fat32, then
mkdosfs -F 32 /dev/sda1 (or whatever the partition name is)

---

### Post by 454redhawk on 2006-12-21
> **Cheater said:**
> That still involves windows (and looks more complex).



It CANNOT get any easier. Take the plunge.

---

### Post by meng on 2006-12-22
> **454redhawk said:**
> It CANNOT get any easier. Take the plunge.
I'll agree it's easy, but the poster wants to start from Linux, not from Windows.

---

### Post by 454redhawk on 2006-12-22
> **meng said:**
> I'll agree it's easy, but the poster wants to start from Linux, not from Windows.

Everything still applies. Only slight modifications will be needed to do it in linux.

---

### Post by nhandler on 2006-12-22
Since everyone seems to feel it is the easiest, I'll get my hands on a windows xp computer. Is there any free partition program for windows that can accomplish the needed tasks?

---

### Post by nhandler on 2006-12-23
I got it working!!!

After reading through this thread ([http://ubuntuforums.org/showthread.php?t=71567)](http://ubuntuforums.org/showthread.php?t=71567)), I found this wiki page ([https://wiki.ubuntu.com/LiveUsbPendrivePersistent)](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)). That wiki article worked perfectly. I got Edgy Eft installed on a flash drive. I am able to save settings and files and Programs.

Edit: I guess it isn't working perfectly. I tried installing java using the commands in the ubuntu guide.

> ubuntu@ubuntu:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  java-common libltdl3 odbcinst1debian1 sun-java5-bin unixodbc
Suggested packages:
  equivs sun-java5-fonts ttf-sazanami-gothic ttf-sazanami-mincho libmyodbc
  odbc-postgresql libct1
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  java-common libltdl3 odbcinst1debian1 sun-java5-bin sun-java5-jre
  sun-java5-plugin unixodbc
0 upgraded, 7 newly installed, 0 to remove and 157 not upgraded.
Need to get 30.4MB of archives.
After unpacking 84.9MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main java-common 0.25ubuntu1 [76.8kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main libltdl3 1.5.22-4 [168kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main odbcinst1debian1 2.2.11-13 [64.1kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main unixodbc 2.2.11-13 [269kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse sun-java5-bin 1.5.0-08-0ubuntu1 [22.3MB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse sun-java5-jre 1.5.0-08-0ubuntu1 [7454kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse sun-java5-plugin 1.5.0-08-0ubuntu1 [1352B]
Fetched 30.4MB in 1m55s (262kB/s)                                              
Preconfiguring packages ...
Selecting previously deselected package java-common.
(Reading database ... 97247 files and directories currently installed.)
Unpacking java-common (from .../java-common_0.25ubuntu1_all.deb) ...
Selecting previously deselected package libltdl3.
Unpacking libltdl3 (from .../libltdl3_1.5.22-4_i386.deb) ...
Selecting previously deselected package odbcinst1debian1.
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-13_i386.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.11-13_i386.deb) ...
Selecting previously deselected package sun-java5-bin.
Unpacking sun-java5-bin (from .../sun-java5-bin_1.5.0-08-0ubuntu1_i386.deb) ...
Selecting previously deselected package sun-java5-jre.
Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-08-0ubuntu1_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java5-plugin.
Unpacking sun-java5-plugin (from .../sun-java5-plugin_1.5.0-08-0ubuntu1_i386.deb) ...
Setting up java-common (0.25ubuntu1) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

Setting up sun-java5-bin (1.5.0-08-0ubuntu1) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of sun-java5-plugin:
 sun-java5-plugin depends on sun-java5-bin (= 1.5.0-08-0ubuntu1); however:
  Package sun-java5-bin is not configured yet.
dpkg: error processing sun-java5-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-jre:
 sun-java5-jre depends on sun-java5-bin (= 1.5.0-08-0ubuntu1) | ia32-sun-java5-bin (= 1.5.0-08-0ubuntu1); however:
  Package sun-java5-bin is not configured yet.
  Package ia32-sun-java5-bin is not installed.
dpkg: error processing sun-java5-jre (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java5-bin
 sun-java5-plugin
 sun-java5-jre
E: Sub-process /usr/bin/dpkg returned an error code (1)


Then, I tried installing flash:

> ubuntu@ubuntu:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gsfonts-x11
Suggested packages:
  msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree gsfonts-x11
0 upgraded, 2 newly installed, 0 to remove and 157 not upgraded.
3 not fully installed or removed.
Need to get 23.8kB of archives.
After unpacking 221kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  gsfonts-x11
Install these packages without verification [y/N]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main gsfonts-x11 0.20build1 [10.6kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse flashplugin-nonfree 9.0.21.78.2ubuntu1~edgy1 [13.2kB]
Fetched 23.8kB in 2s (10.2kB/s)          
Preconfiguring packages ...
Selecting previously deselected package gsfonts-x11.
(Reading database ... 98180 files and directories currently installed.)
Unpacking gsfonts-x11 (from .../gsfonts-x11_0.20build1_all.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.21.78.2ubuntu1~edgy1_i386.deb) ...
Setting up gsfonts-x11 (0.20build1) ...
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

Setting up flashplugin-nonfree (9.0.21.78.2ubuntu1~edgy1) ...
Downloading... done.

Setting up sun-java5-bin (1.5.0-08-0ubuntu1) ...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of sun-java5-plugin:
 sun-java5-plugin depends on sun-java5-bin (= 1.5.0-08-0ubuntu1); however:
  Package sun-java5-bin is not configured yet.
dpkg: error processing sun-java5-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-jre:
 sun-java5-jre depends on sun-java5-bin (= 1.5.0-08-0ubuntu1) | ia32-sun-java5-bin (= 1.5.0-08-0ubuntu1); however:
  Package sun-java5-bin is not configured yet.
  Package ia32-sun-java5-bin is not installed.
dpkg: error processing sun-java5-jre (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java5-bin
 sun-java5-plugin
 sun-java5-jre
E: Sub-process /usr/bin/dpkg returned an error code (1)


I get the same error when I use aptitude. I've tried 'sudo apt-get -f install', but it doesn't work. Does anyone know how to fix this (I already tried formating the flash drive and starting over).

---

### Post by brt on 2006-12-30
i had the same problems, after some digging it seems to be somehow unionfs related:

when using:

```
strace java
```

here it says:
...
readlink("/proc/self/exe", "/cow/usr/lib/jvm/java-1.5.0-sun-1.5.0.10/jre/bin/java", 4095) = 53
...

here, java seems to be located at: /usr/lib/jvm/java-1.5.0-sun-1.5.0.10

so i did:
```
ln -s / /cow
```
and 
```
apt-get dist-upgrade
```
works now... :)

---

### Post by Siilex on 2007-03-01
You are great, man...   ;o)

Works for me also, mutatis mutandis.

---

