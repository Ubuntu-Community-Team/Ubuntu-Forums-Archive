---
title: "Ubuntu 10.10 not booting after update"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by Thandrox on 2010-11-30
Hallo,

I have an acer laptop with ubuntu 10.10 running parallel with windows 7. I installed ubuntu using wubi installer

A few weeks ago I updated my system from ubuntu 10.4 to 10.10 and had problems booting to ubuntu. I copied the c:\ubuntu\winboot\wubildr to c:\wubildr  after which I was able to boot to ubuntu and it was working fine.

Today I have allowed an update on ubuntu and have the same problem as before. I cannot boot into ubuntu anymore but can boot into windows. I get an error No wubildr when I try to boot into ubuntu.
I have tried doing the same copy of the wubildr file but still getting the error.

Can anyone help?

---

### Post by Hippytaff on 2010-11-30
Hi, and welcome :-)
 
Wubi doesn't like updates (or should I say new updates don't like Wubi). If you like ubuntu your better of doing a 'real' install and dual booting with windows. If there is nothing important on your wubi ubuntu install I'd suggest removing it and doing this, if you have stuff you want to save, it might be worth reading this....if you get stuck post back :-)
 
[https://wiki.ubuntu.com/WubiGuide#Troubleshooting](https://wiki.ubuntu.com/WubiGuide#Troubleshooting)

---

### Post by Thandrox on 2010-11-30
Hey... thanks for your quick response

Does it mean that there is no other way of going about this problem other than permanenly installing ubuntu? I was kind of hoping for an easy & quick workaraound

---

### Post by Hippytaff on 2010-11-30
There are way s of fixing Wubi, but I'm not sure they are quick. It depends what yu want to do and whether you have anything of value saved in wubi/ubuntu, and if you do manage to fix wubi it will likley break again. It is mainly designed for evaluation rather than long term use :-) depends what you want to do :-)

---

### Post by drs305 on 2010-11-30
So you were able to find c:\ubuntu\winboot\wubildr and copy it to c:\ and it still didn't help?

I just did an update to a Wubi install and in my case when I selected Ubuntu (second menu, the one controlled by Grub) it just rebooted. I've determined how to fix that issue but I received no "wubildr" message so I assume this is not the action on your machine's boot...

---

### Post by Rubi1200 on 2010-11-30
You could try the fix mentioned here to edit the grub.cfg file.
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

This needs to be done from a LiveCD.

Good luck!

---

### Post by Thandrox on 2010-12-01
Thank you all for your tips. I will make a 'real' installation of Ubuntu

---

### Post by megawolf on 2011-02-11
After updating to the latest kernel (...28) instead of getting to the grub screen my machine would reboot. The following fixed the problem.

I am not sure if the first step is necessary (probably not) but this worked for me:

1. Copy c:\ubuntu\winboot\wubildr and c:\ubuntu\winboot\wubildr.mbr to c:\

2. run chkdisk on c:. 

If you are running windows 7 you will be asked to schedule it to run at the next reboot. Chkdisk did not run the first time i rebooted. I had to schedule it again, the second time the chkdisk process completed. It then booted into windows. 

I reboot again. This time when I select Ubuntu I get the grub menu (i think a message was displayed first that said something about windows not closing a file properly or something and that it would be fixed).  After which point I got me grub menu with my new kernel option. I select it and it goes.

---

