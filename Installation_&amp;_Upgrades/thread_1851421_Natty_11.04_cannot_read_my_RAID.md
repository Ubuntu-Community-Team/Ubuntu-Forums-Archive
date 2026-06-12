---
title: "Natty 11.04 cannot read my RAID"
date: 2011-09-28
forum: Installation &amp; Upgrades
---

### Post by fossilman on 2011-09-28
Hello,

I am new to the Linux environment and I am giving it a try, recently I installed the new version of Ubuntu 11.04 x64, I have 6 1TB disks,of which 4 of them are in a BIOS controlled RAID 5.

Two disks are stand alone, and in one of them there is Win 7 installed, and in the other I installed Ubuntu 11.04. I did a dual boot installation and it works fine, however Natty cannot see my RAID 5.

Is there anything I could do to see my data.

---

### Post by Quackers on 2011-09-28
Try installing the kpartx package via synaptic package manager and then see if your raid partitions can be seen.

---

### Post by fossilman on 2011-09-30
> **Quackers said:**
> Try installing the kpartx package via synaptic package manager and then see if your raid partitions can be seen.
 
Thank you for your answer, I did as you requested, and I still cannot see the RAID, any other suggestions would be appreciated.
 
During the installation, I disconnected the HDD that initially have Win 7 installed, just for avoiding any problem with the MBR and later after everything was running, did and update to grub and can dual boot without any hassle.  My question is, could that installation affected or be the reason that I cannot see my files in raid?

---

### Post by ronparent on 2011-09-30
If you didn't install Ubuntu on the raid it is likely that 'dmraid', the program needed to read a raid, wasn't installed. If I am correct it doesn't install by default unless you are installing directly to a raid.

If that is the case the solution is simply to install it. Any of the processes for installing a program will work. I usually just install by writing 'sudo apt-get install dmraid' in a terminal. Once installed all of your raid partitions should be visible.

---

### Post by fossilman on 2011-09-30
> **ronparent said:**
> If you didn't install Ubuntu on the raid it is likely that 'dmraid', the program needed to read a raid, wasn't installed. If I am correct it doesn't install by default unless you are installing directly to a raid.
 
If that is the case the solution is simply to install it. Any of the processes for installing a program will work. I usually just install by writing 'sudo apt-get install dmraid' in a terminal. Once installed all of your raid partitions should be visible.
 
When I decided to install Ubuntu I came here to this forum to read about the major problems that I would face before making my installation. I remember reading in one post saying that if I have several disks (in my case I have 6 1TB disks), the best option for dual boot would be to simply disconnect the HDD that had Windows preinstalled, make my installation in a free disk and later on update grub.
 
Additional to that I read several documentation regarding RAID's but they mainly were focused to make one, not to see one that was already installed.
 
However, the 4 disks that were in RAID 5, there is no OS installed of any kind, is just used for data storage.
 
Thank you for your suggestion, I will try using dmraid and will report the results.

---

