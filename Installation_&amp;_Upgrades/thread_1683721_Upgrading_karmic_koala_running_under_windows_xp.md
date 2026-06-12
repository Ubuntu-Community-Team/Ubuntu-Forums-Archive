---
title: "Upgrading karmic koala running under windows xp"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by oglipogli on 2011-02-08
I have installed Ubuntu 9.10 & is running succesfully under windows XP. Now i want to upgrade to 10.04 & subsequently to 10.10.
The problem being for the past one year as i have not been using the windows XP i forgot the administrator password for XP. please help
As i am unable to connect mu laptop which is running on ubuntu to internet connections some offline upgrades might be more useful.

---

### Post by debd on 2011-02-08
[http://www.raymond.cc/blog/archives/2006/09/02/how-to-hack-into-a-windows-xp-computer-without-changing-password/](http://www.raymond.cc/blog/archives/2006/09/02/how-to-hack-into-a-windows-xp-computer-without-changing-password/)

may help you

---

### Post by coffeecat on 2011-02-08
> **oglipogli said:**
> I have installed Ubuntu 9.10 & is running succesfully under windows XP.

Do you mean that it is running in Wubi? Wubi means that you have a virtual drive for Ubuntu within the Windows C: partition, rather than Ubuntu being on its own partition. If you have a Wubi installation, then before you attempt to upgrade have a read of the first post in the Wubi Megathread:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

You'll see that updates to grub can cause problems.

**EDIT**: I just re-read your post and noticed your last sentence. If you are unable to connect to the internet in Ubuntu, upgrading is going to be a challenge. You might want to think about doing a fresh install of 10.10 which might solve your internet problem if it is a wireless connectivity problem. And if you have a wubi install at the moment, this might be an opportunity to do a conventional installation of Ubuntu to its own partition - which is always better. If you post more details of your laptop and your Ubuntu installation, people might be able to give relevant advice.

---

### Post by oglipogli on 2011-02-09
Thanks Coffeecat, I Think i will go for a fresh installation of 10.10 but will that harm the other two OS in my laptop i have both XP & Win 7. Also i am using an DELL Inspiron 1525 
2GB (2 X 1024MB) Dual Channel DDR2 SDRAM
Intel(R) Core(TM)2 Duo Processor T5800
HD,160GB,S2,5.4,9.5,WD-ML160

---

### Post by coffeecat on 2011-02-09
> **oglipogli said:**
> Thanks Coffeecat, I Think i will go for a fresh installation of 10.10 but will that harm the other two OS in my laptop i have both XP & Win 7.

Be very, very, very, very cautious if you use the "install alongside" option in the installer. It has a major design flaw in that if you click on either of the 'use whole drive' or 'use whole partition' buttons, it is more likely than not to completely erase all pre-exisiting partitions. Inevitable if you choose 'use whole drive', no doubt, but I have to wonder what the developers were thinking of when they put a 'use whole drive' option in the 'install alongside' choice. The (il)logic of it defeats me. More here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

It is so bad and the developers seemingly so intransigent to doing anything about it that many of us here advise not using 'install alongside' at all and advise going for the manual/advanced option if you want Ubuntu to co-exist with Windows. It's not as complicated as it sounds. If you need help with setting up partitions, run the live CD and post the terminal output of:
```
sudo fdisk -lu
```

---

