---
title: "Alternate Install Steps - OEM"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by w116tjb on 2007-01-20
So I just installed Ubuntu from the i386 alternate install cd and selected the OEM installation. At the end of the install it provided some instructions for removing the OEM user and setting up a normal user. I've forgotten exactly what those steps are. If anyone could help me out, I would really appreciate it.

---

### Post by w116tjb on 2007-01-20
Nevermind, I just found the answer to my question.

If anyone is having the same problem, just go into Terminal and type:

sudo oem-config-prepare

---

### Post by gregconquest on 2007-02-18
This was confusing for me as well. I did a regular install of 6.10. There are no requirements listing the regular distribution as not being able to install Grub anywhere other than the mbr of the boot drive. The notes for the alternate install mention this, but that doesn't help anyone looking at the regular install.

Anyway, I eventually got the "alternate install" and installed it. It gave a splash screen to login using 
oem
as the username and to use the password I selected earlier during the installation. -- ONLY THIS DOESN'T WORK!

I entered
oem
as username and then no password. That got me in.

Then I entered Users and Groups and added a new user
Then
sudo oem-config-prepare
only my previously selected password was not accepted . . .
Doh! It is no password. Leave the password field blank.

This is not what the install instructions say. Why can't the regular install CD allow non-mbr grub installs? That would solve all these problems.

Greg Conquest

PS What was the 4th step in the post setup 1st time regular user login? I thought I hadn't pressed the "next" button completely, so I pressed it (again), it waited a moment, and then shot past some multi-field form. I hope it was the network info . . .

PPS This keeps getting worse. Now I am not allowed to access Users and Groups
The configuration could not be loaded
You are not allowed to access the system configuration.

Is this because when I added myself as user, I didn't check the "administration" ability in user privileges? Oh... How do I add admin privileges to my regular account?

UPDATE: neither
sudo usermod -a -G myusername
nor
gksudo users
worked. I reinstalled --- got screenshots this time. The alternate install needs reform.

---

