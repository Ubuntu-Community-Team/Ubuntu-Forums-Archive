---
title: "Install doesn't see my Win XP Partition"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by Ullyxes on 2010-07-30
Once more (and really really not the last time) I need help with Ubuntu.
This time its the following problem:

I'm running a Win XP sp3 on my Pc and it has a 250GB Partition, so it uses up almost my whole HDD (only 8mb unallocated space). Now, I'd really like to dual boot Ubuntu 10.04 LTS and Win XP, but when the installation progress comes to the point with the partitions, it just shows me, I would have nothing installed on my HDD. Even GParted(in Live mode) couldn't recognize my Win XP partition. What do I have to do, in order to be able to Dual-Boot XP and Ubuntu???

P.S: With Ubuntu 9.10, it all worked well

---

### Post by Ullyxes on 2010-07-31
Adding Information:  > P.S: With Ubuntu 9.10, it all worked well

It all was like this: First, I had Win Xp, then I installed Ubuntu 9.10 (like 4 months ago). I kept it a while, but then I uninstalled it. I still had Win XP. When 10.04 LTS came out, I burned it to a dvd and now I tried to install it, but I have this problem.

Please help me, because I'm getting tired of Win Xp, but still need it sometimes

---

### Post by hyperAura on 2010-07-31
can u choose to do manually resize and partitioning to install ubuntu 10.04 during the installation? I think that's how I did it last time..

---

### Post by oldfred on 2010-07-31
Have you recently run chkdsk in your windows?

My gparted should not show sda and/or took forever to come up with my other drives. Even though my XP seemed to be working ok, I ran chkdsk from windows ( requires  several reboots) and then gparted saw it & brought up all the drives very quickly.

Windows needs about 20-30% free space so that is the max that you can shrink windows. With XP you can use gparted to shrink it. I would shrink it in gparted from the liveCD not the installer and reboot into windows. It may want to run another chkdsk. Then you can run the installer.

---

### Post by efflandt on 2010-08-01
You can check the disk in Windows by right clicking on the drive in My Computer under Properties > Tools.  Check the box to fix errors.  It will tell you that it cannot do that until next boot, so click OK.

For maximum flexibility in resizing the Windows partition, you may want to temporarily disable virtual memory (like Windows swap), since that is a file that cannot be moved.  Under System > Advanced make a note of current settings and disable virtual memory.

Then reboot and Windows should check your disk, and virtual memory should be disabled after it reboots following the disk check.  After you install Linux, you can re-enable virtual memory in Windows.

Note that when a Windows partition is resized, it will be marked as dirty, so Windows will do a chkdsk the next time it boots to make sure it is okay.

---

### Post by Ullyxes on 2010-08-18
Hi everyone!
Yesterday, I came back from my holiday went online and read your posts.
First of all, I'd like to thank you for trying to help me.
Now, let's turn to this CHDSK thing: Actually, I'm running CHDSK really often, but maybe the problem is, that I never check the "fix errors" box. I'll try it all and then I'll post the results.
So long.........

---

### Post by Ullyxes on 2010-08-21
Hi guys!!
I've got some bad news: I ran 2 CHDSK, defragmented my HDD,
but the problem still is the same!!!!
I even tried out a Linux Mint LXDE Live CD, but even there, the HDD was shown as
whole unallocated space.
To make it all even worse, in Win XP Computer Management, it shoes me I would have a 280GB HDD with a free space of 48GB, but in fact I have a 250Gb and the free space is 10MB
If someone has an idea, what to do, please post it

---

### Post by dino99 on 2010-08-21
boot with partedmagic and follow this little help if you want to install ubuntu:

prepare your hdd first:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by oldfred on 2010-08-22
From the liveCD post this so we know exactly what is installed where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

