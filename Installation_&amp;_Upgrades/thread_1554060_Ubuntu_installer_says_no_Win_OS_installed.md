---
title: "Ubuntu installer says no Win OS installed"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by currajong on 2010-08-16
[SIZE=3][FONT=Arial]Hello All,

I am attempting to install 32 bit ubuntu 10.04-i386.iso from boot on a Windows XP Pro standalone desktop PC. I have unused hard drive partitions available for the ubuntu installation. 

At one point the installation dialog box informs me that there is no OS installed on the PC, and the installation program does not correctly indicate the existing Windows hard drive partitions. At that point I abort the installation process.

Can anyone advise me how to proceed from this point. I am an old MSoft OS user from way back - I started when  DOS was all that there was. I am a complete novice however where Ubuntu is concerned.

All help gratefully received.

Thank you.

Regards,

currajong
[/FONT][/SIZE]

---

### Post by Herman on 2010-08-16
Try running CHKDSK /R on it and see if that helps.

One way to run CHKDSK /R is to click on 'My Computer', 'Drive C:', and then right-clcik and click 'Properties', if I remember correctly, then in the 'Tools' Tab, Choose 'Scan Now'.
Make sure both check boxes are ticked, for a thorough scan and look for bad sectors and attempt recovery of them if it finds any.
It will pretend to try to scan right away, but then it realizes it can't run a file system check on a mounted file system, and will ask you if you want to schedule one for the next reboot. Choose to do so and reboot.

You can also run CHKDSK /R from a Windows installation CD if you have one. Try to use an equal or newer version of Windows CD than the version you are working on. You can use a Windows 7 CD to CHKDSK Windows XP, but I would not recommend the other way around.

Maybe even try running CHKDSK twice or even three times. I think that might fix your problem, but it's just a guess. I hope it's a good guess, but a file system check is always a good idea anyway so even if I'm wrong it won't be a complete waste of time. Let me know how you get along.

Regards, Herman :)

---

### Post by currajong on 2010-08-17
> **Herman said:**
> Try running CHKDSK /R on it and see if that helps.

One way to run CHKDSK /R is to click on 'My Computer', 'Drive C:', and then right-clcik and click 'Properties', if I remember correctly, then in the 'Tools' Tab, Choose 'Scan Now'.
Make sure both check boxes are ticked, for a thorough scan and look for bad sectors and attempt recovery of them if it finds any.
It will pretend to try to scan right away, but then it realizes it can't run a file system check on a mounted file system, and will ask you if you want to schedule one for the next reboot. Choose to do so and reboot.

You can also run CHKDSK /R from a Windows installation CD if you have one. Try to use an equal or newer version of Windows CD than the version you are working on. You can use a Windows 7 CD to CHKDSK Windows XP, but I would not recommend the other way around.

Maybe even try running CHKDSK twice or even three times. I think that might fix your problem, but it's just a guess. I hope it's a good guess, but a file system check is always a good idea anyway so even if I'm wrong it won't be a complete waste of time. Let me know how you get along.

Regards, Herman :)
Hello Herman,

Thank you for your response. I have run chkdsk a number of times over all the partitions of my HDD, without any error messages. I have even run SpinRite over the HDD to check for problems - no advices of any errors.
I have run chkdsk both from the command line and the Windows Graphical Interface with no advices of any disk or file errors. The Ubuntu Installer still insists that there is no OS on my PC.

My PC of itself boots up and runs XP and all programs quite happily. 
Some detail - my internal HDD is partitioned thus:
C:\ Windows XP OS
D:\ Program Files and Data
E:\ Empty
K:\ Empty
I was attempting to install Ubuntu to E:\ drive, and have K:\ drive available as swap space. E:\ drive is 31 Gb approx, and K:\ drive is 8 Gb approx.
It's all a little frustrating.
Regards,

currajong

---

### Post by Herman on 2010-08-17
Okay then, I think that by now any file system problems would be well and truly rectified, if there were any.

The next thing to try having a look at would be the partition table.
Are you able to 'see' you partitions and file systems in GParted? 
In your Ubuntu Live CD if you look in 'System', 'Administration', 'GParted', does GParted show a graphical representation of your hard disk with its partitions. Do they look okay?

If they are okay they should have a coloured rectangle around them, (not black), and they should show how full they are by being colored in the center for part of the way across. There shouldn't be any yellow warning triangles with exclamation marks inside them showing up anywhere.

There is no need to go to the effort of posting a screencap from GParted, but if there is anything there that looks like it might be a concern you might find it easier to just post the output from the command 'sudo fdisk -lu' here if you can. 
```
sudo fdisk -lu 
``` I should be able to see the problem from that output if it's a partition table problem.

Sorry I can imagine it would be very frustrating for you and I hope it will be some problem that can be solved easily.

Is there anything you can think of about your hardware or software that might be a little different from standard like a IDE or SATA adapter card or any kind of RAID that might be affecting the Ubuntu partitioner's ability to work on your hard disk?

Regards, Herman :)

---

