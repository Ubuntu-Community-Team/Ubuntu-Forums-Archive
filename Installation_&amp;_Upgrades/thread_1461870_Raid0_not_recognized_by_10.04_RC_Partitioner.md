---
title: "Raid0 not recognized by 10.04 RC Partitioner"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by green_earth on 2010-04-24
I have a 2.5 year old gigabyte motherboard with an Athlon 64 3.0. I am using the built in nVidia SATA Raid controller to manage two 250 GB hard drives as one 500. I have Windows 7 installed and working fine. When I try to install 10.04 RC the disk partitioner is recognizing the two drives independently, and even offering to re-partition one of them which it shows Win7 is on.

How do I make Ubuntu recognize the Raid0 configuration correctly?

If I use a spare SATA drive I have to install Ubuntu, will Grub destroy the boot information for Windows because it is not properly recognizing the Raid configuration Windows is using?

I am a perpetual newbie to Linux... even though I've been toying with Ubuntu for many years off and on.

Thanks.

---

### Post by green_earth on 2010-05-17
Can anyone direct me to information about SATA RAID with nVidia motherboards? Three weeks and no reply to my post. Appreciate any help out there...

---

### Post by ronparent on 2010-05-19
If you want to install on the spare drive, try setting it as default boot drive in bios. Then your mbr on the raid won't be overwritten, Your access to the raid should be preserved as a dual boot setup. I believe this should work, but, if it doesn't, you would still have access to windows by changing the boot drive order in bios.

---

