---
title: "Dual Boot with Windows 7"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by yo shu la on 2011-01-23
I have a Toshiba A9 laptop that has a clean install of Windows 7. I want to install Ubuntu and have it dual boot. 

The problem is when I try and install Ubuntu it does not give me the usual option to install the systems side by side. It's as if it don't know my windows 7 instillation is there. I have installed Ubuntu on top of a Windows system loads of times, but this is the first time the usual option to resize the drive and decide how much you want to allocate to Ubuntu is missing. I have defragmented the Windows drive as I read this could help. 

Any help would be appreciated.

Thanks...

---

### Post by mikewhatever on 2011-01-23
I've heard that W7 doesn't like its partitions resized by anything other then its own disk manager. Try resizing first, then boot the Ubuntu installer.

---

### Post by yo shu la on 2011-01-23
Thanks for the suggestion. Just tried that. Still only got the same 2 options: Erase and use the entire disk or Specify partitions manually. As it's not picking up the Windows instillation i'm guessing it won't create a dual boot?

What I don't get is I did a clean install of Windows 7 a couple of weeks ago and had no problem creating a dual boot with Ubuntu as the options at install were there to install side by side This time they are not and I'm damned if I can work out what is different! I'm tempted to reinstall Windows again and try again, but it's such a pain installing Window, getting updates etc, etc...

---

### Post by Quackers on 2011-01-23
Did you use 10.04 last time, and trying 10.10 this time?

---

### Post by presence1960 on 2011-01-23
If you shrunk Win 7 and made unallocated space, you are half way there. next boot the Ubuntu Live CD/USB and choose try ubuntu or boot gparted Live CD/USB. You now want to create an ext4 partition for the ubuntu install and a linux-swap partition out of the unallocated space. Then choose manual install. It will install to those partitions and set up the dual boot.

---

### Post by yo shu la on 2011-01-23
I been using 10.10. I will give the suggestion above a go. Thanks. Still can't work out why it don't recognise the Windows partition and still can't see how it will recognise it after doing the above, but will give it a go and post back when done. Thanks for your help...

---

### Post by mikewhatever on 2011-01-23
> **yo shu la said:**
> Thanks for the suggestion. Just tried that. Still only got the same 2 options: Erase and use the entire disk or Specify partitions manually. As it's not picking up the Windows instillation i'm guessing it won't create a dual boot?
...

A dual boot is just two OSs installed on separate partitions. The Ubuntu installer is there to install Ubuntu and not recognize Windows or create dual boots. If, for whatever reasons, W7 is not present as a boot option, adding it as a custom option is fairly easy.

---

### Post by yo shu la on 2011-01-23
I've given up. 
Just installed Ubuntu using entire disk and forgot about the Windows bit. I will probably encourage me to spend more time and learn a bit about linux.

I would still love to know why it don't see the Windows install and another time it did?

Thanks you for your help.

---

### Post by mikewhatever on 2011-01-23
It could have been related to the number of pre-existing partitions at the time of installation. For example, with 3 pre-existing primary partitions, the installer would not offer the automated option.

---

### Post by ChurchillK on 2011-01-23
I am having the same problem with side-by-side installation.

I'm using an HP DV6 64-bit system.  
The ( only ) disk has four primary partitions.
I am installing v10.04.1 ( LTS ) from a USB.

My suspicion was that the 4 partitions defined would prevent the side-by-side option from being offered.  What I found was that in about 1 attempt out of 10 the installer _would_ offer side-by-side installation.

I have not been able to replicate the various options that I have used so that I can consistently get the side-by-side option offered.

Various options in my installation attempts include:

  Ethernet connected / disconnected
  SDCard ( = /dev/sdc ) inserted / no SDCard
  prior to running install the /dev/sda is mounted / not mounted
  when installer asks to umount sda or sdc or both I respond YES / No
  the USB contains Ubuntu v10.04.1 / v10.10 / v09.10
  the USB was created using the pindrive (?) USB installer v1.8.2.1 / v 1.7.9.9

Again, at least twice ( three times ) I have gotten the side-by-side option on the install.  But I usually do not.

Any ideas on what definitely is or is not a factor in causing this?
Or is there perhaps something else I might be doing that is affecting the result?

---

### Post by presence1960 on 2011-01-23
> **ChurchillK said:**
> I am having the same problem with side-by-side installation.

I'm using an HP DV6 64-bit system.  
The ( only ) disk has four primary partitions.
I am installing v10.04.1 ( LTS ) from a USB.

My suspicion was that the 4 partitions defined would prevent the side-by-side option from being offered.  What I found was that in about 1 attempt out of 10 the installer _would_ offer side-by-side installation.

I have not been able to replicate the various options that I have used so that I can consistently get the side-by-side option offered.

Various options in my installation attempts include:

  Ethernet connected / disconnected
  SDCard ( = /dev/sdc ) inserted / no SDCard
  prior to running install the /dev/sda is mounted / not mounted
  when installer asks to umount sda or sdc or both I respond YES / No
  the USB contains Ubuntu v10.04.1 / v10.10 / v09.10
  the USB was created using the pindrive (?) USB installer v1.8.2.1 / v 1.7.9.9

Again, at least twice ( three times ) I have gotten the side-by-side option on the install.  But I usually do not.

Any ideas on what definitely is or is not a factor in causing this?
Or is there perhaps something else I might be doing that is affecting the result?

You can not have more than 4 primary or 3 primary and an extended partition on any disk no matter what OS you are using. You are at the limit. You will need to remove a primary partition after backing up any data and then create an extended partition for ubuntu. Within the extended partition you can create as many logical partitions that you want- the only limit being the amount of space you allocate for the extended partition.

---

