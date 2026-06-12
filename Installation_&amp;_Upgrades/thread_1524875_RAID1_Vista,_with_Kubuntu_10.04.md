---
title: "RAID1 Vista, with Kubuntu 10.04"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by rhodrid on 2010-07-05
I have a 32bit Vista machine with RAID1 (fakeraid from ASUS mobo using 2 identical drives).  I added a new hard drive and installed 64bit Kubuntu 10.04 with the installation disk on the new drive - I want to keep  Vista and Linux separate. The installation proceeded smoothly and I can boot into Vista and Linux. I accepted the default installation process except to have Kubuntu installed on the new drive. When the machine boots, I see the Grub 2 script prompting choice of OS.

Questions
1) Grub 2 shows a choice of booting from 2 different drives in Vista (the two drives in the RAID1). I understand that how Linux and Windows does a fakeraid is different - but I am at risk of getting the Vista RAID1 volumes out of sync by this configuration? Does the Grub 2 script need to know the Vista drives are RAID1? I can see the MBR on both volumes of the RAID1 array drives has the Grub 2 script. No boot loader is installed on the new drive with Linux

2) In Linux with the file manager I see the 2 disks in the RAID1 array as separate hard drives. I only plan on now doing read-only file transfer from the Vista to Linux, but if I ever need to write to the Vista volumes in the future how can this be done without getting the RAID1 drives out of sync?

---

