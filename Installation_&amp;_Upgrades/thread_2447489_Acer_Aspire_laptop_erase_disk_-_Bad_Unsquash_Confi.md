---
title: "Acer Aspire laptop erase disk - Bad Unsquash Configuration"
date: 2020-07-20
forum: Installation &amp; Upgrades
---

### Post by luponius on 2020-07-20
I realize now, having had a Windows 8 laptop with OEM partitioning it might have been unwise to erase the disk, and found a few topics on this already, however the erasure has already happened.

Trying a manual partitioning with GPT table:
single ext4 file system with ' / ' mount point results in:

Installation Failed
The instlaler failed to create a partition table on ST9500325AS
Create a new partition table (type: gpt) on '/dev/sda'
Job: Create new partition table on device 'dev/sda'
Command: sfdisk /dev/sda

I would appreciate any advise since at this point I'm working from USB and would like to have a full Lubuntu setup available since the standard Windows 10 I previously upgraded to was even slower than 8 and Lubuntu from USB has been lightning fast so far.

Edit:  Believe it might be useful to add my boot setup.  I'm using a YUMI multiboot with lubuntu (and some other linux distros, including ubuntu) on it and boot normally from USB and attempt to install after I boot and successfully connect to WiFi

---

### Post by luponius on 2020-07-20
In the meantime I'm attempting to install Ubuntu, maybe its installation is more robust than Lubuntu somehow and it works.

---

### Post by guiverc on 2020-07-20
Providing the release of Lubuntu may have helped.

Lubuntu is the the Ubuntu base, with a lighter desktop replacing Ubuntu's default and much heavier GNOME (or Unity for 16.04) desktop. 

Lubuntu with 18.04 LTS uses the LXDE desktop, where as modern Lubuntu uses the LXQt desktop (assuming 20.04 LTS). It was also available with two installers, the *ubiquity* installer which is the same as Ubuntu desktop, *OR* the *debian installer* which is like an older Ubuntu Server install. 

 Lubuntu 20.04 LTS however uses the LXQt desktop, and only comes with the *calamares*.

*I'm not familiar with YUMI so I'm ignoring that detail, but by not providing details of release, or ISO used, I don't know which of those three installers you're asking about, nor which release.*

*Unsquash* errors usually mean faulty media, either the ISO wasn't validated, OR the write to media itself was faulty. You didn't provide the exact message however.

To validate the ISO for Ubuntu or flavors, see [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)

The Lubuntu manual page on Installation can be found at [https://manual.lubuntu.me/stable/1/Installing_lubuntu.html](https://manual.lubuntu.me/stable/1/Installing_lubuntu.html)

---

### Post by luponius on 2020-07-20
Thansk for the reply, I'm working with 20.04 for everything since that's the latest and made sure to get the latest LTS for longer term support.

I can say that attempting to install Ubuntu has worked, it partitioned correctly and everything.  I will attempt Lubuntu once again but maybe it was a faulty install.  I was under the impression that downloading via torrent would guarantee a verified download through the peer to peer software but maybe that's not really the case.

Will update back with any results on lubuntu if I make further progress.

---

### Post by guiverc on 2020-07-20
Yes torrent download usually do a checksum check after download to ensure integrity, but it'll depend on software and settings used, as it can be disabled.  In my experience, the write to your install media is usually where errors occur.

All 20.04 LTS media (Ubuntu and flavors) will check itself for flaws in the media, you just have to let it occur, and notice if it reports errors (and not *skip* the check).  In prior releases, the validation was a separate skip most people didn't perform (most of the time write works flawlessly, but most failures to install are due to bad writes so the check i consider cheap insurance).

---

