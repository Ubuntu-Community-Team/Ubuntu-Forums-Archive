---
title: "How to install FTP server"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by pingman on 2006-10-13
Hi,

This is what I'm using to install FTP server on my ub box:

sudo apt-get install proftpd

and this is what I get:

sudo apt-get install proftpd
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package proftpd

using a similar command successfully installed appahe!

Appreciate all the help](*,) 

Thanks

---

### Post by adwait on 2006-10-14
Have you enabled universe and multiverse? Check the wiki on how to.

---

### Post by wieman01 on 2006-10-14
From terminal:
> sudo gedit /etc/apt/sources.list
Then add this line & save:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

---

### Post by pingman on 2006-10-14
Thanks, same problem, do I need to restart something after making this change?

---

### Post by wieman01 on 2006-10-14
Are you behind a proxy or something? Have you got access to the Internet?

---

### Post by pingman on 2006-10-14
No proxy no firewall yet....

---

### Post by pingman on 2006-10-14
I can get to [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) from my browser without a problem

---

### Post by wieman01 on 2006-10-14
Have you tried "Synaptic" instead or are you running a server without GUI?

---

### Post by pingman on 2006-10-14
I'm trying to install this stuff on ub desktop and am running the gui

---

### Post by pingman on 2006-10-14
what is Synaptic

---

### Post by wieman01 on 2006-10-14
Ok, open a terminal windows and type this command:
> sudo synaptic
Enter your password when prompted. That the repository GUI that let's you install software. Then search for "proftpd".

---

### Post by pingman on 2006-10-14
thanks man, I got it:mrgreen:

---

### Post by Avarus on 2006-10-16
Errr... I don't have any GUI, so I can't get it downloaded. I'm not behind a proxy btw.

---

### Post by wieman01 on 2006-10-16
> **Avarus said:**
> Errr... I don't have any GUI, so I can't get it downloaded. I'm not behind a proxy btw.
So what's your exact problem? What Ubuntu version are you using what what does this file look like:
> /etc/apt/sources.list

---

### Post by benblout on 2006-10-16
> **pingman said:**
> Thanks, same problem, do I need to restart something after making this change?

I don't use apt-get a lot, but I believe you need to issue an
apt-get update
command to re-read the sources.list file.

> **pingman said:**
> what is Synaptic
Synaptic is a very nice, and ubuntu-preferred graphical package managment tool.  If you are running a gui, just type
sudo synaptic
at a terminal prompt.

One a side note, I have been very happy with vsftpd on my installations.

-Ben

---

