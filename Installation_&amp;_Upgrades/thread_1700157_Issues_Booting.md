---
title: "Issues Booting"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by Ørion on 2011-03-04
Hey everyone, I'm having some issues getting Ubuntu to boot.  I've installed it a bunch of times before, but dual booting and not.  Right now though, I'm having issues installing it along with Windows 7, on separate hard drives.  Here's my current configuration:

60GB SSD with windows 7
500GB HDD, NTFS, windows 7 data

I bought a 1TB HDD that I want Ubuntu on, but I only want Ubuntu to use 100 GB.  I want the other 900GB for Windows 7.  So, I put in the Ubuntu CD, chose to edit the partitions manually in the 1TB HDD, created a 100GB ext4 primary partition for linux and a 2GB swap partition, leaving the other 900GB unallocated.  Ubuntu seemed to install fine, said it succeeded, and asked me to reboot.  When I did, however, my computer boots straight into Windows (no GRUB screen at all).  I've tried changing the boot priority to all three of my installed drives from BIOS and tried putting GRUB on both my SSD and 1TB HDD.  Any suggestions?  Help is very much appreciated.

---

### Post by Hedgehog1 on 2011-03-05
Ørion,

We need to get a look at your disk partition layout.

Please boot Ubuntu from the LiveCD, select 'TRY', and then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

[B]TO BE CLEAR - You now have THREE hard drives, right?

60GB SSD with windows 7
500GB HDD, NTFS, windows 7 data
1 TB, Ubuntu & ntfs[/B]

***The Hedge***

:KS

---

