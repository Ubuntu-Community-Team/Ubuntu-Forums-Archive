---
title: "Help me triple boot!"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by hhh on 2010-07-31
I currently dual-boot XP and Debian sid. I currently have XP on /dev/sda1, sid on /dev/sda2 with /home mounted seperately on /dev/sa3, swap is /dev/sda4. I have free space in both sa3 and 4, mostly in 4, of course.

What I'd like to do is add a third partition, either with or without a seperate home mount, but have my current grub2 still be the bootloader. I'm thinking I'll give a total of 33 G to it (I keep almost nothing on my hard drive, it's all on the cloud).

I want to install Kubuntu and try it out, I've burnt the Live CD and it's very cool. Suggestions?

---

### Post by ajgreeny on 2010-07-31
You already have four primary (I assume) partitions, so you are at the limit available on the disk unless you shrink one or more other partitions in order to make the current sda4 large enough to accommodate both the new install and swap inside an extended partition.

Can you show us a screenshot of gparted from the live CD so it's possible to get a better view of the partition layout, sizes, and current space used.  It may then be easier to give some suggestions of the best way to proceed.

---

### Post by hhh on 2010-07-31
Hey, sorry for the delay. Here's GParted, click for fullsize..

[[IMG]http://img39.imageshack.us/img39/6459/screenshot0731201007303.png[/IMG]](http://img137.imageshack.us/img137/6459/screenshot0731201007303.png)

---

### Post by 23dornot23d on 2010-07-31
Because you have four partitions set up already

I would do it like this .......

_____________________________________

Boot from a LiveCD (so that nothing you are using is mounted)

Delete the swap

Resize sda3 

Create a new extended partition and then in it  create a ext4 and a swap space

Then install your new Version of Linux to it.

([Here are the ones I have set up on mine]("http://sites.google.com/site/23dornot23d/"))
and some more information on multiple systems

---

### Post by oldfred on 2010-07-31
You are going to have to delete swap. Which means when your recreate it in the extended partition it will have a new UUID. You will have to edit fstab in Ubuntu to the new UUID to get it to work. Use gparted to edit partitions from liveCD. Then use the liveCD to find UUIDs and edit the fstab. Sudo blkid - not sure if in liveCD you need sudo??

After you delete swap you can shrink sda3 - your /home and then make all the available space the extended partition. Then inside the extended you can create the additional partitions.

---

### Post by hhh on 2010-07-31
Thanks guys. What about having sid be the owner of Grub2? Will it be easier if I wipe the debian install, repartition, and install debian last?

---

### Post by 23dornot23d on 2010-07-31
Yep the last installation usually controls GRUB2 so install Debian Sid last.

or if you don't want to - 

I cheat by putting Grub2 on the partition with the Last Distro (sda5 possibly in your case) ..... 
if I do not want it to take control
(it does warn you that this is a bad thing to do though) I have no idea why !!!

[COLOR=Red]But the last thing I want to do is start re-installing running distros just to get a (GRUB2) menu working (its only point is to point to a Distro and run it ).[/COLOR]

In the advanced option when installing ....... choose sda5 ....... but as I say the developers put a note up
saying that this is a bad thing to do.

---

### Post by hhh on 2010-07-31
One last question. Say I remove Kubuntu as the middle install in the future and install another OS. How can I keep debian as the master of grub2?

---

### Post by 23dornot23d on 2010-07-31
I have just answered that - but as I say its probably not accepted as the correct way ....

install the last GRUB2 to the partition it resides on 

*(advanced option last screen before it installs off the liveCD - you can choose where to put GRUB2)

Until someone lets me know why its such a bad thing - to only have one GRUB2 controlling my system ........ 

(I will continue to do it this way as it works for me ..... and I currently run 13 operating systems side by side.)

---

### Post by hhh on 2010-07-31
Thanks for the tips! I'll post when it's all done.

---

### Post by 23dornot23d on 2010-07-31
One more thing ..... doing it this way and having one controlling GRUB2 ...... means you are in control of the GRUB2 update ........ 

by that I mean

*You have to always go back to the controlling system to do the update-grub command to
get your system menu to be up to date.

[COLOR=Red]*this may be the bad thing they mean - but to me its a good thing - my menu for my Distros changes when I want it to change , "NOT WHEN MY COMPUTER" wants to change it.



[/COLOR]So if you do decide on my way ,,,, 
go back into Sid Debian ,,,, and do a 

update-grub

After the installation ...... otherwise you will not see your last addition in your MENU

---

### Post by hhh on 2010-07-31
Posting from my Kubuntu install. I did end up reinstalling debian, I put Kubuntu last (sda7) and let it overwrite grub...

[[IMG]http://img440.imageshack.us/img440/3941/snapshot1l.th.png[/IMG]](http://img440.imageshack.us/img440/3941/snapshot1l.png)

Thanks again for the help!

---

### Post by 23dornot23d on 2010-07-31
Very neat and tidy .... looks good ..... glad it was successful.

---

### Post by hhh on 2010-07-31
Thanks!

---

### Post by hhh on 2010-08-01
Running
```
grub-install /dev/sda
```
as root while logged in to debian restored debian's grub2 as the bootloader.

---

