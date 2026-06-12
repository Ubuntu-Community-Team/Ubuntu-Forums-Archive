---
title: "Any way to install .exe files?"
date: 2015-01-14
forum: Installation &amp; Upgrades
---

### Post by kenny18 on 2015-01-14
Im not sure if there's any way to install these.. seems like a lot of stuff has to be ran thru terminal.. any help is thanked :)

---

### Post by QIII on 2015-01-14
Hello!

.exe files are usually Windows executables.

What are you trying to install?

---

### Post by yancek on 2015-01-14
You can put as many .exe files on Linux as you want but they won't do anything.  If you want to run something you use in windows there are several options.
Use wine, see the link below:

[https://www.winehq.org/](https://www.winehq.org/)

You can also install VirtualBox or some other virtual software and install windows on that inside Linux.
You can find a Linux version of whatever you run on windows if it is available.  You would have to indicate what software you want for anyone to help.

---

### Post by kenny18 on 2015-01-14
Its a google map application.. I relize it was a windows version..

How do I install or run a .tar.gz file?

---

### Post by ian-weisser on 2015-01-14
> **kenny18 said:**
> How do I install or run a .tar.gz file?

Step-by-step instructions: [http://askubuntu.com/questions/25961/how-do-i-install-a-tar-gz-or-tar-bz2-file](http://askubuntu.com/questions/25961/how-do-i-install-a-tar-gz-or-tar-bz2-file)

WARNING: You are trying to install untrusted software that you downloaded from the wild, dirty internet. If that software breaks your system or steals your data or shaves your cat, it's not Ubuntu's fault.

Many excellent applications are already in Ubuntu Software Center, tested and safe. I look there first.

---

### Post by DuckHook on 2015-01-14
Whenever I see a new user asking about .exe files, a great big red flag goes up and I strongly suspect that said user needs to carefully read the following:

"Linux is not Windows" intro:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Linux in general and Ubuntu in particular is not a "free Windows". It doesn't run Windows programs. Exceptionally clever people have written exceptionally clever kludges that awkwardly run a *few* Windows programs, but it's still a kludge. What you are trying to do is akin to trying to attach a part made for a train onto a jet.

In addition to above, I also recommend the following to give you some initial bearings with Ubuntu:

General Ubuntu Intros:

[https://help.ubuntu.com/community/ExternalGuides](https://help.ubuntu.com/community/ExternalGuides)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://owlcroft.com/ubuntu/](http://owlcroft.com/ubuntu/)
[https://sites.google.com/site/easylinuxtipsproject/Home](https://sites.google.com/site/easylinuxtipsproject/Home)

---

### Post by kenny18 on 2015-01-15
Okay im trying to install this game. 
First I extracted it to the desktop

Went to terminal and ran
"cd/home/kg/desktop/CreepTD"
Results were no such file or directory

What do I do?

---

### Post by yancek on 2015-01-15
> "cd/home/kg/desktop/CreepTD"

If you are trying to access some file in the CreepTD directory, you need a space after cd and before / as below.  Also, when you are in a terminal, it is case sensitive so if the directory is "CreepTD" and you accidentally enter creepTD, you will get the same error:

> "cd /home/kg/desktop/CreepTD"

---

### Post by mastablasta on 2015-01-16
I hope it's not a windows game. 

but if it is and if it runs in wine (check here [https://appdb.winehq.org/](https://appdb.winehq.org/)) install and use playonlinux (available in software center) to install it. you wont' have to mess arround in terminal.

I rarely use terminal on desktop, but when I do it's usually for some specialised software that has no GUI available. e.g. I recently had to check some data from hard disk and then disable the firmware based on that data.

---

