---
title: "Install Ubuntu 14.04 on new Acer Aspire S7-392"
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by colo3 on 2014-10-06
Hi,

I bought this computer last days, and my intention was to install Ubuntu alongside Windows 8, since day 1, so I don't have to back-up personal data, only Windows restore related data. I was trying to find some useful post, but none of them convinced me that i would be able to do it without any problem. Could anyone who was able to do it help me or guide me? 

Thanks in advence.

---

### Post by matt_symes on 2014-10-06
Hi

> **colo3 said:**
> Hi,

I bought this computer last days, and my intention was to install Ubuntu alongside Windows 8, since day 1, so I don't have to back-up personal data, only Windows restore related data. I was trying to find some useful post, but none of them convinced me that i would be able to do it without any problem. Could anyone who was able to do it help me or guide me? 

Thanks in advence.

If you have a spare external hard drive i would image your computers hard drive first in case there are any problems.

Anyway, to start with, boot into Windows and use the Windows 'Disk Manager' tool to shrink the main Windows partition to create some empty space. 15GB to 30GB should be plenty to start with.

This is where Ubuntu will be installed.

Kind regards

---

### Post by colo3 on 2014-10-06
Hi, 

Thanks for the quick responce. The computer has a 256 ssd. But it is configured to use 2 128ssd using RAID 0. I know that i have to shrink the Windows partition, but I think that i also have to disable RAID, SafeBoot and many others things in order to have a dual boot. I know this computer in particular is kind of difficult to get the dual boot, that's why i was asking.

---

### Post by matt_symes on 2014-10-06
Hi

> **colo3 said:**
> Hi, 

Thanks for the quick responce. The computer has a 256 ssd. But it is configured to use 2 128ssd using RAID 0. I know that i have to shrink the Windows partition, but I think that i also have to disable RAID, SafeBoot and many others things in order to have a dual boot. I know this computer in particular is kind of difficult to get the dual boot, that's why i was asking.

I see. 

I don't have any experience of installing on an Acer Aspire S7-392 so i will wait to see if others have before offering any further suggestions, as it looks slightly more awkward than a standard installation.

Kind regards

---

### Post by colo3 on 2014-10-07
Anyone?

---

### Post by jmcfarlane on 2015-03-04
> **colo3 said:**
> Anyone?

I managed to set up dual-boot with Windows 8.1 and Ubuntu 14.04 on an S7 382-9890 about a year ago and it wasn't easy. From what I remember, the final step involved using [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"). 

I'm now trying to reinstall the system as a dedicated Ubuntu system and having even less luck than before! There are a few useful tidbits [here]("https://wiki.archlinux.org/index.php/Acer_Aspire_S7-392") related to BIOS settings on dual-SSD S7-392 systems.

Good luck!

---

