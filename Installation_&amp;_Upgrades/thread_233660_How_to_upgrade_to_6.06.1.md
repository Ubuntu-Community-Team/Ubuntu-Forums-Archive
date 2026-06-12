---
title: "How to upgrade to 6.06.1?"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by marsopia on 2006-08-10
How can I upgrade to Dapper 6.06.1 from 6.06? I tried via #sudo apt-get dist-upgrade and nothing happened. Am I already on 6.06.1 if I use to update the system via synaptic or #apt.get update?



Thks

Mariano

---

### Post by GavinX on 2006-08-10
Huh? I kinda guess you're talking about an updated version which you saw on Distrowatch which indicates that it contains about 300 security patches. If that is the cause, you really don't have to do anything IF you have been installing the updates automatically which were sent out periodically. Installing the updates means that your system is as updated as the repos are. So no need to do anything else.

---

### Post by jamesford on 2006-08-10
lsb_release -a
should reveal that you are already runing 6.06.1

---

### Post by marsopia on 2006-08-10
Thank you both!

mariano@mariano-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper

I am already running 6.06.1!

But still cant sync my Visor...

Mariano

---

### Post by freelsjd on 2006-08-10
I have a dapper system that is updated daily.  However, 
the output from

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06 LTS
Release:        6.06
Codename:       dapper


so why no 6.06.1 ?

---

### Post by freelsjd on 2006-08-10
In answer to my own question, it seems I was missing the following line from /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates universe main restricted multiverse

---

### Post by afilonov on 2006-08-10
> **marsopia said:**
> !

But still cant sync my Visor...

Mariano

And what is the problem? I can sync my T3 without any problems. Didn't have any problems with my old Visor either. I use pilot-xfer for backup and J-Pilot for sync. I tried to sync with Evolution on Fedora before, worked almost OK (needed to sync contacts), but J-Pilot works better.

---

