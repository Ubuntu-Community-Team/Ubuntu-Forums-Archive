---
title: "still afraid to try the update"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by de Bacon on 2010-05-08
I started this yesterday, made progress but not finished and no further participation came in that thread!  Trying again!
> 
Been strictly an 8.04 user since summer 08. I have always had problems with the nvidia graphics card (gforce 6600 LE). Every time I have tried to use the nvidia driver package by clicking the enable "NVIDIA accelerated graphics driver (latest cards)" box, I completely loose my GUI (causing to totally reload the system). When the latest supposed update came out, (last fall I think) said to resolve that issue, I was afraid to even try it! I realize this video card is a problem with linux but it has worked with big limits, and I don't need much from a video card


Having an extra HDD on my machine, I decided to test lucid. I disconnected all the others the other day and loaded lucid on that clean disk. I ended up with no GUI there...

I got so I can get a **GUI** by inserting **nomodeset** into the grub 2 menu at startup.  I don't know how to put the needed line into the file /etc/default/grub so the test can proceed.  Without doing that I again have no GUI after a fresh boot.  

Then there is the second part of this process.  After I successfully make a boot happen on this HDD, which is in reality just a test, I want to update my normal use system hardy to lucid.  I just don't know if when I go through that process the result will be no GUI again.  And if so, will placing that command, the one which at present time I don't know the syntax of nor location to place said command, into the grub file would resolve the issue.  

Yesterdays topic name was " I'm afraid to try the update" with a nVidia tag, if you want to see that thread.  

Help would sure be appreciated. I am pretty ignorant about code in general and commands to do work in terminal, though I am willing.

---

### Post by Catharsis on 2010-05-08
You can make "nomodeset" permanent by:
```
gksudo gedit /etc/default/grub
```
Add "nomodeset" to the line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
so it reads
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
Save and exit. Then run in a terminal:
```
sudo update-grub
```
Then reboot.

If I understand correctly, you have more than one HDD for your computer? And you just disconnected all but one and did a clean install of Lucid onto it?

If that's the case, then if you get Lucid running on this test case, then there's no reason you shouldn't have the same experience on the other drives. The only problem would be the upgrade process, which has been known to break in rare cases. 

I suggest you run this test case for a week or two and see if you run into any more problems. If not, backup all of your data and upgrade your Hardy install. You'll then have to implement the "nomodeset" fixes you did on your test case. Worst-case scenario, you know the LiveCD works and you know a clean install works, so you can do both of those.

---

### Post by de Bacon on 2010-05-08
Catharsis,

Yes I have done as you understood me to say with hard disks.   I will feel better about doing a upgrade if I can get a system running on this other hard disk.  

You are right, I can do a complet re-install though that is what I really want to avoid going through.    

Thanks for the input.  Your info is perfectly clear so I will go ahead and see what happens.  I'll then report back as to what happened.

Thanks, :)

---

### Post by LuridCinema on 2010-05-08
I just updated both my dual-boot Asus Eee PC netbook and my i-5 video editing box w/ 4 drives at home .. NO PROBLEMS... Flawless. I did have to update my /etc/fstab/ to have my extra drives mount on boot. That is all

I was ready to do a fresh install on the video editing machine just in case, but all is good !

THANXX Ubuntu !

---

### Post by de Bacon on 2010-05-08
There is success.  
Thanks so much to all for the assistance!

---

