---
title: "Installed dual-boot vista ubuntu, but how do I boot to ubuntu?"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by minulescu on 2007-08-12
I have vista intalled on my HP dv6000t.

I downloaded the ISO of Ubuntu 7.04 and booted the computer from the CD.

Then I pressed install from Ubuntu's desktop.

I went through all the initial installation questions, however.. I did use the bare minimum of space.

[B]SWAP = 260MB
Ubuntu (ext3) ~ 2050 MB (shows up in vista as 1.96 GB)[/B]

Perhaps this is my problem... that I gave so little space?

After it began installing, I left the computer, thinking it would take sometime.

When I came back... it was just showing the Ubuntu desktop... so I assumed the installation completed successfuly. (Does instalation usually show a message upon completion, or just exits?)

Then I shutdown my computer, took out the Ubuntu cd.

Upon powering up my computer... I assumed I would see a message that would ask me whether I want to boot to Ubuntu or Vista... but nope... it just boots straight to vista.

**Is there something I need to do specifically so it can boot to Ubuntu, or so that it asks me what to boot to?**

Thanks for any help.

---

### Post by Pumalite on 2007-08-12
Too little space. XP?. Vista?. Graphics?. Memory?. What iso did you use?

---

### Post by Gremlinzzz on 2007-08-12
[http://www.winmatrix.com/forums/index.php?showtopic=12188](http://www.winmatrix.com/forums/index.php?showtopic=12188)
this is how to make a partition with vista
me i use this method to create a partition then i delete the partition i created making it free space.then i use the live ubuntu cd click the install icon when it gets to the partition question i use 
Guide-use largest continuous free space
then ubuntu does the rest

---

### Post by MQMike on 2007-08-12
Maybe it is a partitioning problem – did you first shrink the Vista partition?
Doesn’t sound like a GRUB issue – the setup is simple, installing Ubuntu after Vista – GRUB should easily install itself to the MBR.


Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)
(GRUB – How to re-install GRUB)

***   The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

---

