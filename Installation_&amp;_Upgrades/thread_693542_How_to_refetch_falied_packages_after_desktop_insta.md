---
title: "How to refetch falied packages after desktop install"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by lafaki on 2008-02-11
Hi,

 I have tried to install desktop on Ubuntu Server 7.10 using the below command:

[FONT="Courier New"]sudo apt-get install desktop[/FONT]

It ran 95% correctly but it failed to fetch the below packages:

[COLOR="Silver"]- firefox_2.0.0.11+2nobinonly-0ubuntu0.7.10_i386.deb
- firefox-gnome-support_2.0.0.11+2nobinonly-0ubuntu0.7.10_i386.deb
- linux-headers-2.6.22-14_2.6.22-14.47_all.deb  
- linux-headers-2.6.22-14-generic_2.6.22-14.47_i386.deb[/COLOR]

How can I fix that?
I tried the command: 

[FONT="Courier New"]sudo apt-get install desktop --fix-missing[/FONT]

but I got:

[FONT="Courier New"]Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package desktop[/FONT]

Any ideas??

When coming to this section of the Ubuntu forum, I also saw that the GNOM desktop should be installed with the below command (different to what I did):

[FONT="Courier New"]sudo aptitude update&&sudo aptitude install ubuntu-desktop[/FONT]

Shall I try the below command instead?
If yes, do I have to remove anything before running it??

FYI, after the installation it seems that my desktop doesn't start (automatically with reboot or manually with a command). 

[FONT="Courier New"]lafaki@ubuntu:~$ sudo /etc/init.d/gdm start
sudo: /etc/init.d/gdm: command not found[/FONT]
 
Looking forward to your help!

Thanks a lot,
Akis

---

### Post by Pumalite on 2008-02-11
Go ahead and run it.We'll deal with the problems when they show up.

---

### Post by lafaki on 2008-02-11
Do you mean to run this command?

"sudo aptitude update&&sudo aptitude install ubuntu-desktop"

Is it safe after that I have run the "sudo apt-get install desktop" and have these problems??

---

### Post by Pumalite on 2008-02-11
Go ahead and run it.

---

### Post by lafaki on 2008-02-12
:)

I tried the command and it worked!
This time I also did it locally on the machine without using any remote SSH session.

Thanks for your help.

---

### Post by Pumalite on 2008-02-12
You are welcome. Life has to be lived with courage. Congrats. Good luck.

---

