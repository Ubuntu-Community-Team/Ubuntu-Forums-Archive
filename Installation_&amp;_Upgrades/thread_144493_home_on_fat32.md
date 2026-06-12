---
title: "/home on fat32"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by Niels13 on 2006-03-14
Hi, I have a question.
I am kinda new to ubuntu and linux, I have been trying it for some time and I'm starting to understand how it works. But some apps I use only run under windows, so I decided to make my pc dual bootable.

Now it works perfectly, installing was easy, booting was easy, the grub loader is great and all that. But now I want to be able to share files between the two os'es. 

Ubuntu is sayd to be able to read and write to fat32, so I want to make an install with the root on a normal ext3 filesystem, and the /home on a fat32 filesystem. Setting it up is easy, but it doesn't work. When I get to setting up my user name and password in the text fase of the setup, it just keeps asking for my user name and password. No error code, but it justs keeps repeating the screen. My guess is that the username and password and all other settings are stored in the /home folder, in my case the fat32 partition, but it can't write there for some reason.

Do any of you guys know what I'm doing wrong and can point me in the right direction?

Many thanx in advance!

---

### Post by kaamos on 2006-03-14
Bad idea. Fat32 does not handle permissions and this causes big problems.

[http://ubuntuforums.org/showpost.php?p=810198&postcount=2](http://ubuntuforums.org/showpost.php?p=810198&postcount=2)

---

### Post by Niels13 on 2006-03-14
Thanks for the advice!

Gonna try it out now.

---

