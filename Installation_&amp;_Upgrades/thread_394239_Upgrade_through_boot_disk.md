---
title: "Upgrade through boot disk"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by bullraiser on 2007-03-26
Hi, 

I had already installed Ubuntu 6.10. But couldnt connect to Internet as my laptop uses Intel Pro Wireless properitory card.

I now got the latest 7.04 beta release boot CD and tried live CD. I was able to connect to Internet now.

But, how can I upgrade already existing 6.10 to 7.04, as I dont have internet connection and have only 7.10 boot disk?

Any suggestions??

---

### Post by zvacet on 2007-03-26
You can not do that with Live CD,alternate is the choice.but if you have separate home partition do fresh install.if you don´t have separate home and you have enuogh space to make one here is how to do it
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by bullraiser on 2007-03-27
How can I delete the existing partition used by Ubuntu and install a fresh Ubuntu updated version?

I am dual booting with Windows XP.

Any suggestions?

---

### Post by zvacet on 2007-03-27
You can do that during installation proces.Choose manualy way to partition and you will see your existing Ubuntu partition.Delete it (I think you highlight it and questions will follow what to do with it)and in the same place install Feisty.If you have enough free space make separate home partition.

---

### Post by bullraiser on 2007-04-10
How can I erase all the previous Ubuntu partition and install the new version?

I have the following partition:

1. ext3 - 14 GB
2. SWAP - 700 MB

Remaining are NTFS partition.

Shall I delete all the ext3 and SWAP partition?
Will this will erase my current exisiting Linux and install the new version of Linux?

If for any reason, Linux isin't installed, will the GRUB menu will be also deleted, as this will make me not to login to Windows partition as well?

Let me know, what approach should I follow.

--TIA

---

### Post by az on 2007-04-10
> **bullraiser said:**
> How can I erase all the previous Ubuntu partition and install the new version?

I have the following partition:

1. ext3 - 14 GB
2. SWAP - 700 MB

Remaining are NTFS partition.

Shall I delete all the ext3 and SWAP partition?
Will this will erase my current exisiting Linux and install the new version of Linux?

If for any reason, Linux isin't installed, will the GRUB menu will be also deleted, as this will make me not to login to Windows partition as well?

Let me know, what approach should I follow.

--TIA


Delete both of those partitions and then press the "ga back" button.  The installer will detect the FREE SPACE and offer to install Ubuntu there.  After that, all your wishes will come true!  The partitions will be made and the bootloader will be installed.  It will work.  That's how you replace your Edgy install with Feisty.

---

### Post by bullraiser on 2007-04-10
Excellent!! I installed Fiesty 7.04 by deleting my old partition and it works flawlessly.
I can now able to connect to internet with Intel Pro Wireless card detected by default.

There was onething, I was noticed is that for the first time, when I was restarting my machine after installation, there was disk check utility running and it showed that there was some error and restart required.

But after the restart, system booted and everything was working.
I will be testing the system for sometime now and will report the updates, although nVidia driver is not able to enabled.

Cheers.

---

