---
title: "Armada M700 - Wrong Hard Drive Size Displayed in Partitioner"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by sillgen on 2007-05-16
I am trying to install Ubuntu "Dapper" (LTS 6.06) on an Armada M700 with a 20 GB Hard Drive (Compaq Model CSD CAT020L). Whether I use the partitioner in the Installer or run 'fdisk /dev/hda" from the command prompt, the O.S. reports this drive as being 60GB. As a result, the O.S. appears to have been installed correctly, however, I receive a GRUB Error Code 18 during bootup. 

What needs to be done to allow the partitioner to recognize the correct drive size for this system?

Thanks,

Steve Illgen

---

### Post by sillgen on 2007-05-18
After further investigation, this is what I found...

I ran a SUSE ES 10 installation disk on the notebook and it reported the same HD size as Ubuntu (60 GB). I finally found an Edgy Eft install CD and was able to install the O.S. by first, using 'fdisk' from the CD to "clear" the partition table, then running the installation and allowing the partitioner to set the default partitions for me. I then upgraded to Feisty with 'apt-get dist-upgrade' with no errors.

To see if this is a fluke or a problem with the O.S, I created a 20GB file and added it to the 16GB already used by the O.S. and data. No errors resulted; therefore, I believe that what I have is really a 60GB drive that the BIOS on the M700 reports as 20GB  (and Windows readily accepts), but which Linux ignores and reports the actual space available.

Does this make sense?

Steve Illgen

---

