---
title: "Hardware problem"
date: 2014-07-16
forum: Installation &amp; Upgrades
---

### Post by derwalroszsagt on 2014-07-16
Forum Members

I have a 2006 notebook with a intel cpu, 40GB Harddrive and 500MB ram that was running Windows XP.  I believe it was infected with malware and maybe hijacked.  The machine would not boot to the start menu in the normal mode and would not respond when booted to safe mode.  I did not have the Windows XP installation disk to do a repair.  I finally decided to reformat the drive and install Ubuntu 14 as I have it running on along with windows on 3 other computers.  I used Knoppix live CD to reformat and repartition the disk to a single 40GB partition.  All features of the Knoppix worked correctly including the network connections.  I downloaded the Ubuntu iso and tried to install it.  The installation went smoothly but crashed at about the 2/3's point (the ask question screen was up) in the process with the error message that it couldn't write to the Harddrive. I repeated the process with the same result.  The bug report feature did not work as apparently the crash was complete.   I also tried installing Ubuntu 12.04.3 (a copy I have used several times in the past) and it also crashed at about the 3/4 point but without a message (the little progress wheel was stopped).  
My request is for your expert opinion on whether or not this is a software or hardware problem and if a hardware problem is it the Harddrive or memory.  Any help is appreciated in advance.


Derwalrosz

---

### Post by kc1di on 2014-07-16
Hi Derwalrosz and Welcome to Ubuntu , 

It's most likely software related with that old a machine, and only 500mb ram it would be well under the minumum to run unity.  I would give lubuntu or xubuntu a try.
> Minimum System Requirements
1 GHz processor (for example Intel Celeron or better)
1.5 GB RAM (system memory)
7 GB of free hard drive space for installation
Either a CD/DVD drive or a USB port for the installer media
Internet access is helpful (for installing updates during the installation process).
If you have an old machine, you may consider other alternatives like Lubuntu or Xubuntu.

above quoted from official system requirements on ReleaseNotes page.

---

### Post by lukeiamyourfather on 2014-07-16
I agree, Lubuntu would be a better option given the quantity of memory in the system. The disk might be failing or damaged, it's 8 years old after all which is forever for a hard drive. Though it's too soon to tell in my opinion. Give Lubuntu a shot and see how it goes.

---

### Post by tgalati4 on 2014-07-17
Put a 2 GB swap drive partition on the drive and try again.  It's possible that you ran out of RAM during installation, or the hard disk really does have a problem, and that killed the WinXP in the first place.

Run *badblocks* with the Knoppix Live CD.

---

### Post by derwalroszsagt on 2014-07-18
[SOLVED]Thanks to you all for replying.  I proceeded with your suggestions and downloaded lubuntu and tried to install it.  Same problem, only earlier.  I had never heard of badblocks so tried it.  Lot's of bad blocks starting at 137743.  Thanks tgalati4.  As I really don't want to spend a lot of money on this machine I'll get a Harddrive at eBay and try the installation with that.  
Thank you again for your help and most of all for contributing your expertise to the forum.  You guys are really good.  

derwalrosz

---

### Post by tgalati4 on 2014-07-18
You are quite familiar with *badblocks* now.  I would say you are an expert.  Burn a copy of Ultimate Boot CD (UBCD) and boot from it, then use the manufacturer's low-level formatting tool.  It might rescue the disk.  If the manufacturer's diagnostics show problems, then the disk is trash.

You can mark the title of the thread as "solved" in thread tools.

Best of luck and welcome to the forums.

---

### Post by derwalroszsagt on 2014-07-26
Forum members,

Just to close the loop on this thread.  I got a used hard drive at e-bay and installed it.  I loaded Ubuntu 14.04 without a problem and it works well albeit very slow.  I will install 2GB of RAM and hope it speeds up some.  Considering the age of the machine I must live with whatever speed I get with the 2GB RAM.  I'm just going to give the machine away to someone without a machine anyway.  Thanks again to you that helped me out on this. 

derwalrosz

---

