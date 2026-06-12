---
title: "Help"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by neilford on 2007-11-08
I have plummeted so far down the rabbit hole that I do not know how to get out. I had Feisty installed and had a great dual booting system with XP. Then I upgraded to Gutsy and everything went downhill. Gutsy broke my wireless. I tried several suggested ways to fix it with no success. I decided to install Feisy back onto one of my empty partitions. When I did this, not only could I not get it to boot up Feisty, but it messed up my ability to boot into Gutsy. I, finally, decided to reformat my linux disk with windows and then I was going to do a clean install of Feisty back onto the disk. Now, I cannot boot into windows anymore. I think that when I made it a dual boot system, that a grub file was installed onto my windows disk and whenever I try to boot windows it tries to run this grub. I can boot in safe mode from my feisty cd, but I don't know where to look on the windows disk for that grub file to remove it and get my windows back up. I need this system, right now. Can anyone help me? Thanks.

neilford

---

### Post by bulldog on 2007-11-08
Boot your windows install cd.
Get to the place where you get three options 
1/Install windows 
2/repair an existing windows
2/quit

Choose the second one,this will bring you to the recovery console
Choose the windows you want to logon,mostly 1 and provide the administrator password
Now perform fixboot and/or fixmbr , you get a warning but ignore that one.
Reboot and windows should boot again.

Some advice,make your topic understandable on first sight,Help is not  a good one!

---

### Post by neilford on 2007-11-09
Thanks. I am still getting the error which looks like this:

Grub Loading stage1.5

Grub loading, please wait...
Error 22

It is still loading a grub boot. Fixboot did not eliminate this. Where is this grub file?
Is it on the disk or is there " PRAM " holding this booter? Thanks

neilford

---

### Post by bulldog on 2007-11-09
22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

How many hdd's  are in this machine?
The fixmbr should repair your windows bootloader,when you tried this,WAS there a windows to logon?

If you have a live cd,can you boot it and type in a terminal```
sudo fdisk -l
``` and copy the output to the forum?

---

### Post by neilford on 2007-11-09
Bulldog,

Thanks for your help. I actually got it fixed. It was much easier than I thought it was going to be. The last time I had accessed my XP system, I had formatted the whole drive that was my Ubuntu disk. Because of this I was able to boot up from the live CD. I created a new partition for Feisty and installed it. It recognized my Windows system and made a Grub entry for it. So, now I have Feisty back and I am reinstalling all my software. I wish that Gutsy had worked out better for me, but the wireless problem was persistent. I had similar experiences with Edgy. As soon as I get back to where I was, I will probably create a Gutsy partition and keep trying to solve my wireless issue. Thanks.

neilford

---

### Post by bulldog on 2007-11-09
Good to hear it works,well good luck then :guitar:

---

