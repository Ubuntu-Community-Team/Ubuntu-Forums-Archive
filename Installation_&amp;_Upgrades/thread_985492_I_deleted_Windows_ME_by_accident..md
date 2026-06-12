---
title: "I deleted Windows ME by accident."
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by Tudles1 on 2008-11-17
I'm fairly positive that when I was setting up the partition between Ubuntu and Windows ME; I set the partition to 100% Ubuntu (Version 8.10) and there was no room left for Windows.
I had data on my laptop (in Windows) that I would like to retrieve. Is there some way I can restore my computer to before I installed Ubuntu, or is there a beyond the grave recycle bin I can access for this information? I'm very new to Ubuntu, and I've never fiddled around with changing OS's before. Could anybody help me?

---

### Post by SeanHodges on 2008-11-17
The first thing is to collect a bit of information about your situation, can you open a terminal (Applications menu -> Accessories -> Terminal) and type the following:

```
sudo fdisk -l<enter>
```

enter your password when requested, and post the resulting output?

---

### Post by oilchangeguy on 2008-11-17
> **Tudles1 said:**
> I'm fairly positive that when I was setting up the partition between Ubuntu and Windows ME; I set the partition to 100% Ubuntu (Version 8.10) and there was no room left for Windows.
I had data on my laptop (in Windows) that I would like to retrieve. Is there some way I can restore my computer to before I installed Ubuntu, or is there a beyond the grave recycle bin I can access for this information? I'm very new to Ubuntu, and I've never fiddled around with changing OS's before. Could anybody help me?

also see this thread:
[http://ubuntuforums.org/showthread.php?t=984649](http://ubuntuforums.org/showthread.php?t=984649)

---

### Post by Tudles1 on 2008-11-17
Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e639e63


It also says more about device boot, start and end, blocks, Id, and system. HOwever; I don't know how to copy and paste :\ there are only 3 boots and the systems are Linux, Extended, and Linux Swap / Solaris

---

### Post by gnusci on 2008-11-17
> **Tudles1 said:**
> I don't know how to copy and paste :\ there are only 3 boots and the systems are Linux, Extended, and Linux Swap / Solaris

Post the full information, you only need to select what you wan to copy, and then, give a middle mouse click in a text editor.

---

### Post by Tudles1 on 2008-11-17
I'm on a very very old laptop, and I don't have a mouse with a middle button. It says that cntrl+shift+c is copy and that the same goes for pasting (but with v), yet when I tried that nothing happened.

---

### Post by Tudles1 on 2008-11-17
Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e639e63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2339    18787986   83  Linux
/dev/sda2            2340        2432      747022+   5  Extended
/dev/sda5            2340        2432      746991   82  Linux swap / Solaris


Okay I figured out copy/pasting. P.E.B.K.A.C.

---

### Post by poebae on 2008-11-17
lol kudos to you for admitting that you made a mistake :)

At first I thought this was a joke thread about what a rubbish system Windows ME was :P

---

### Post by SeanHodges on 2008-11-18
> **Tudles1 said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2339    18787986   83  Linux
/dev/sda2            2340        2432      747022+   5  Extended
/dev/sda5            2340        2432      746991   82  Linux swap / Solaris


It appears you do not have a partition labeled "WIN95 FAT32" or similar, which is what you should expect if you still had Windows ME installed on your computer. I'm sorry to say your Windows ME partition is gone and most likely unrecoverable.

Ensure that next time you install an new operating system (whether it be a new version of Windows, Linux, or something else), make sure you back up *ALL* important data before doing so. You can never guarantee the safety of your data when doing such a fundamental change to your system.

If you try to install Windows ME again, you'll probably find that the installer will not recognise the presence Ubuntu and will take over the hard disk completely again. Your easiest option is to let it do this and then run the Ubuntu installer again, this time checking carefully that the partition option you have chosen provides space for both Windows and Ubuntu.

---

### Post by Tudles1 on 2008-11-18
Ok, thanks Sean. I was worried that was the problem. Thanks for the help though.
How will I know how much room to leave for the partition? I want to install Ubuntu on my family computer with Vista, but have Vista be the default boot. There are 3 other users who won't want to use Linux, and I don't want to cause Vista to run out of space because of my partitioning.

---

