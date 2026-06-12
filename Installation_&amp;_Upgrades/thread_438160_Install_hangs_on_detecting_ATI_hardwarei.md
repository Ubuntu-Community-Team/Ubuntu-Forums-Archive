---
title: "Install hangs on detecting ATI hardwarei"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by wydaho on 2007-05-09
I am trying to install Ubuntu 7.04 on a new Gateway laptop MX6453, AMD Turion 64 X2 with an ATI Radeon Xpress 1150 display adapter.  Before trying to install I can run in "live" mode and see that the ATI driver shows up as a restricted driver.

I've read the posts about testing & installing methods for ATI drivers plus many other threads, but I can't get fiesty to install to try fixing the video even if I use the Alternate install disk.

Here's a brief description of what happens:

1. When I try the install form the Live desktop, things go well until the install hangs at "Detecting Hardware, please wait ... "Loading module 'sata_sil' for ATI Technologies Inc Standard ...".  At this point the disk partitions have been created and many MBs of Ubuntu files have been written, but the install has failed and I can only start over.

2.  Tried doing the install using the alternate disk in expert mode with noacpi & nolacpi, but it hangs even sooner at the CD detect stage.

Both installation CDs check out with a good  MD5sum.  The live install disk also gives a valid CD check.  The alternate disks fail the CD check even though I have burned three seperate disks at  a a slow 4X.  

One other note - I am trying this as a dual boot with Windows Vista as the other, already installed operating system.  Ubuntu is located on a previously unallocated disk segments that were later formatted during the live install process.  After my first Ubuntu install attempt I no longer can boot into Vista.  Message is that there is no operating system installed & I have to use "Super Grub" to allow me to  boot in the Windws partition if I want to get back to Vista (which seems to still work).

Any suggestions?  Is there someway to bypass the hang in the live install?  Any ideas as to why the alternative install disk won't pass the CD check even after careful burning and with an valid MD5sum?  

Thanks in advance for help provided,

Wydaho

---

### Post by Matty2006 on 2007-05-11
you may need a boot loader like this post suggests:
[URL="http://ubuntuforums.org/showthread.php?t=260772"]
http://ubuntuforums.org/showthread.php?t=260772[/URL]

check out this link:
[http://support.microsoft.com/kb/919529](http://support.microsoft.com/kb/919529)

I dont think vista uses the traditional MBR boot loader any more by default.. so you might have to go this route in the above link even for only these two OS's.. I have personally not attempted this myself so I am not familiar with the process.

 If you problem does in fact have something to do with boot record getting tweaked, there is a way to convert The new boot format to MBR using diskpart from MS. This can be done with the new windows boot disk(CD). MS diskpart tool has many sub commands.. 

If you have anything you care about on the vista OS make sure you backup or take an image using imageX from the MS boot disk.

This is pretty new stuff and is not really well documented. This is how I might go about it if I was running vista.. If you get any further I would be curious to know how it works out.

Good luck

---

### Post by wydaho on 2007-05-12
Thanks, Matty.  Your links to the debate about proprietary drivers help put my problem in perspective.

I'll do some more digging, but at first glance it looks like my install of fiesty fawn is being held hostage to the open vs proprietary softawre conflict.  

I'll keep checking for alternative solutions, as well as trying to find out why I can't generate a valid alernative install CD despite many slower reburns and MD5sum checks.

---

### Post by wydaho on 2007-05-14
Okay, I'm posting a followup to my original query as I have now figured out what the problem is and have been able to install Fiesty Fawn on the Gateway.  Hopefully this will be of some use to others with similar problems

First of all, the original problem was the Live install hangs, and using the Alternate install disk also died before completion (details in the first note of this thread).  

The help instructions with the Alternate disk said that to disable flaky power management during setup you should enter "noacpi" and "nolacpi".  Tried this with no success, but if I enter "acpi=off".  The install works fine!  I still have to resolve a problem with the broadcom wireless connection and the ATI restricted drivers, but at least I was able to get the system up and running.

As expected a clean install also resolved the boot problem I was having with windows Vista (this is a dual boot system with Vista installed first).  Grub took over the MBR, detected Vista, and now gives you the choice on power up.

I think the main take-away from the many hours spent trying to fix this is that the Help text on the alternate install disk is either in error or is at least confusing.  Why would it say "noacpi" instead of "acpi=off".  I also had to use "acpi=off" to even check the CD integrity.  Have others seen this as a problem?  I would be interested to know if anyone has had a similar experience.

Now the next step will be the wireless and video driver.

Thanks again to Matty 2006 for the reply and help - Wydaho

---

