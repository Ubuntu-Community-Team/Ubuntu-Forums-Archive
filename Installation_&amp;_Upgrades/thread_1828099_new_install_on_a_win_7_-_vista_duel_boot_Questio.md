---
title: "new install on a win 7 - vista duel boot Questio"
date: 2011-08-18
forum: Installation &amp; Upgrades
---

### Post by hard ist on 2011-08-18
I have Windows 7 and Vista set o a duel boot system, I made a new partition  20 gb in size , I burned a cd , and want to install it to that partition, here is the question - when I boot from the cd and get to  the screen  where the install  is - if I choose to install , do I get the option to install to the partition I made , or does it just install where IT wants to?

---

### Post by lobotomyboy on 2011-08-18
Ubuntu will give you the option to install under a particular partition with the "advanced options."

---

### Post by hard ist on 2011-08-18
ok , where are the advanced options ?

---

### Post by hard ist on 2011-08-18
All I'm afraid of is that when I click install its going to overwrite my windows installations, so when I click install setup runs, does it let me install where I want it to , or what, thats what I need to know.  I am new to ubuntu and just want to be sure.

---

### Post by critin on 2011-08-18
When it asks where you want to install, read the options carefully.  If it chooses the free partition--great, let it install.  If it asks to install them side-by-side, don't.  Choose 'OTHER' and click forward.  At the next page click on the free partition and then click 'install now'.  Make note of the partition number and make sure it installs to that partition.  

You may have to go one more step and click 'change'.  To do that, right click on the free partition  and choose change in menu- or click 'change' if you see it there.   config it by choosing make it 'file system', and then click / to make it install there.  Open the option boxes to see the choices.  (you may not have to do this)

Just take note of the partition number.

critin

---

### Post by Hakunka-Matata on 2011-08-19
Evidently your bootCD, or LiveCD/usb works, you're getting into the install phase.  Have you tried out Ubuntu yet?  Does it play OK on your hardware?  If so, I'd suggest you 'try Ubuntu without installing" again, and have a look around, like at your partitioning.  It may require work before you can even start installing Ubuntu.

You don't say how you created the new 20GiB partition, is it an Ext4 partition, has windows converted your hard drive to Dynamic from Basic?    You should also create a /SWAP partition.  As a matter of fact, creating a SWAP partition before you start is a really good idea, (Thanks Herman?, did I get that right oldfred?)" it will speed up the install, because the installer will use that swap during the install.

Some more information would help in advising how to proceed,

---

### Post by hard ist on 2011-08-19
Well I used acronis to resize a windows partition , then I made the free space into a partition
windows said it was NTSF .

---

### Post by hard ist on 2011-08-19
SoI need a Ext4 partition ,AND a /SWAP partition.vExt4 partition ? Well that seems to be a lot to do , more so since I don't know how to create Ext4 partitions.

---

### Post by critin on 2011-08-19
Which version do you want to install?  If you choose ubuntu 10.04,  it will take care of formatting and swap by itself.  At least it did for me.  The newer 11.04 wants you to make a swap which isn't hard, but not a snap if you are very new to partitioning.  It depends on you and how well you can focus on what it says to do.   There are some directions.  
It will format to ext 4 before it installs.  All you have to do is watch.

You will want to make the partition a 'primary' at the point where you 'change' it.

Try the live cd for awhile as suggested above by Hakunka Matata   to be sure it works on your hardware.     __Search the forums for answers before you do anything.  I may forget a step and I hope if I have, someone will step in and say so.  You don't want to lose your Windows.

critin

---

### Post by teh603 on 2011-08-19
> **hard ist said:**
> All I'm afraid of is that when I click install its going to overwrite my windows installations, so when I click install setup runs, does it let me install where I want it to , or what, thats what I need to know.  I am new to ubuntu and just want to be sure.On its default setting, the installer will shrink the NTFS partition to about half its original size, and then put both an ext4 partition and a swap partition in the remaining space, then configure GRUB to allow you to choose whether you want to boot to Linux or Win7.

That's IF the OEM install of Win7 didn't use up all your partitions. I've seen a few that did; what I did in that case was to format the drive using Ubuntu then reinstall Win7 from the recovery CDs. The recovery install only uses one or two partitions, which frees up at least two for Linux.

---

### Post by Hakunka-Matata on 2011-08-19
post the output of
```
sudo fdisk -lu
```

so we can see how your drive is partitioned now, and what your options are.

---

### Post by Mark Phelps on 2011-08-21
First thing you need to do is go into your hard drive with Acronis and REMOVE the NTFS partition you created for Ubuntu.

Thus, when you then go to install, use the Manual Partitioning option to have the installer format the new unallocated space.  Be very careful when selecting it to ensure that you don't accidentally select your Windows partition.

Also, do NOT allow the installer to shrink the Win7 partition using a side-by-side install.  That is not what you are trying to do -- and runs the risk of corrupting the Win7 install.

---

