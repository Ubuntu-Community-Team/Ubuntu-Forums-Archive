---
title: "First Time User Software Issues"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by pangtn on 2008-01-23
Hi Guys, 

Some help or advice if possible. I've installed Ubuntu Desktop and am now trying to install a couple of Apps with no luck. Is there a certain way to install software or programs in Linux/Ubuntu?? I keep getting an error message about access denied etc. I have the error message details if required, thanks in advance!

---

### Post by kellemes on 2008-01-23
> **pangtn said:**
> Hi Guys, 

Some help or advice if possible. I've installed Ubuntu Desktop and am now trying to install a couple of Apps with no luck. Is there a certain way to install software or programs in Linux/Ubuntu?? I keep getting an error message about access denied etc. I have the error message details if required, thanks in advance!



Try this.
[https://help.ubuntu.com/7.10/add-applications/C/gnome-app-install.html](https://help.ubuntu.com/7.10/add-applications/C/gnome-app-install.html)

---

### Post by pangtn on 2008-01-23
Thanks, about to try Synaptic. Will it allow me to install third party software I have downloaded from the Net, for example Avast AV ?

---

### Post by kellemes on 2008-01-23
If packages are not in the repositories.. (not installable using synaptic) you may need other ways's.
Not sure if this helps for Avast.
[http://ubuntuforums.org/showthread.php?t=229128](http://ubuntuforums.org/showthread.php?t=229128)

---

### Post by pangtn on 2008-01-23
Ok thanks, I seem to be making some progress with Avast. What about files that are only available in tar.gz format? I understand that they are compressed files but once extracted I seem to have issues still...

---

### Post by kellemes on 2008-01-23
> **pangtn said:**
> Ok thanks, I seem to be making some progress with Avast. What about files that are only available in tar.gz format? I understand that they are compressed files but once extracted I seem to have issues still...


Decompressing the tarball.
```
tar xfvz file.tar.gz
```
The directory-structure will be decompressed to disk, move to this directory (mv ..)
Instructions are in the readme or install-file you'll find there..

What are the issues you're having? Maybe I can help..

---

### Post by oldos2er on 2008-01-23
See [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Steveway on 2008-01-23
1. Stick to oldos2er's Link in his post above me.
2. You don't need antivirus software for your Linux-system. The only use-cases for anti-virus on linux would be if you run a mail-server (to check mails etc before sending them to Windows-user.) or if you want to check your files before you send them to a Windows-using friend, so you won't unkowningly send him a virus with it.
But normally you won't need it. And before you are going to ask: You don't need to defrag your Linux-filesystem and there is no need to configure the (inbuilt) firewall on a normal Desktop-system.

---

### Post by pangtn on 2008-01-24
Thanks for the info so far guys, I'm going to try Synaptic and the Tar methods and see how far that gets me.

Apart from Avast, I'm trying to install Merak Mail Server without much luck, hopefully this works!

---

### Post by oldsoundguy on 2008-01-24
It begs the question:  What in the heck are you installing an ANTI VIRUS PROGRAM for?  Unless the machine is to be a SERVER with WINDORK boxes attached, really a waste of time!

Besides that.  F-Prot has an AV program (free for Linux, of course) that they have that installs a lot easier if need be.

---

### Post by pangtn on 2008-01-24
> **oldsoundguy said:**
> It begs the question:  What in the heck are you installing an ANTI VIRUS PROGRAM for?  Unless the machine is to be a SERVER with WINDORK boxes attached, really a waste of time!

Besides that.  F-Prot has an AV program (free for Linux, of course) that they have that installs a lot easier if need be.

Correct, its hopefully going to be a mail server one day...

---

### Post by pangtn on 2008-01-24
It looks like its going further, seems to be having a problem writing to the /opt diretory. I tried to change permissions but the owner is Root, do I need to be logged on as Root perhaps? The user I'm currently using is part of the Root Group...

$\e[0;32m**	$\e[0mCreating /opt/merak directory 
$\e[0;31m**	$\e[0mFailed! Check user permissions 
$\e[0;32m**	$\e[0mExtracting distribution 
$\e[0;32m**	$\e[0mPlease wait... 
$\e[0;32m**	$\e[0mChanging permissions 
$\e[0;31m**	$\e[0mFailed! Check user permissions on /opt/merak 
$\e[0m**	$\e[0mFile /opt/merak/config/merak.conf is not writeable, skipping postconfiguration!

---

