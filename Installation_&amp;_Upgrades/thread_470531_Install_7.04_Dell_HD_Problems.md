---
title: "Install 7.04 Dell HD Problems"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by kwrxxx on 2007-06-11
I have a dell e510 with two SATA drives 
/dev/SDA1 Dell utility 100 MB
/dev/SDA2 Windows XP 160 GB
/dev/SDB1 EXT3 66 GB      <- this is where I want to install Ubuntu 7.04 & place GRUB
/dev/SDB5 SWAP 1 GB
/dev/SDB6 FAT32 30 GB Storage area

When I attempt to run the disk partioner in manual mode I set up Ubuntu to
format SDB1 and SDB5 however the disk partitioner complains about SDA1 
having irregular clusters. I don't want Ubuntu to do anything with the SDA drive 
just set up and install on /dev/SDB1 and /dev/SDB5 , but I'm afraid ubuntu 
will format /dev/SDA partitions. 

I also want to install GRUB on /dev/sdb1 boot sector and not on /dev/SDA.

---

### Post by HunkirDowne on 2007-06-11
How old is this Dell?  I have an old Dell.  Mine has a BIOS that **does not** support booting partitions that exist past the dreaded 1024 cylinder limit :(.  I did, however, manage to install on a 1023-cylinder sized /dev/sdb1 and it does just fine, but...

...and here's the deal.  I think it *DID* put Grub on /dev/sda which is not what **you** want. My Dell, *otoh*, doesn't have a Windows problem anymore (hah!), but my laptop does <grumble>.

But before you go any further, take a look at the HOWTO link below.  I think you want to put Grub on /dev/sdb1 and use the Windows XP boot loader to boot the machine.  If you follow the instructions on the link, you should have a boot menu in Windows XP (or you may already have one that asks you if you want to boot from the Dell utility).

So two things.  Read the HOWTO link that I mentioned above (and pasted below if I didn't shut my brain off) and *ALSO READ* the man pages for "dd" and use that to back up your master boot record (MBR).  If you happen to have an MS-DOS 6.22 boot disk with FDISK on it, FDISK /MBR will reset your master boot record properly and you won't need to "dd" your MBR (or PhD your MBA, for that matter).

HOWTO link:
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

"dd" link:
[http://www.debianhelp.co.uk/ddcommand.htm](http://www.debianhelp.co.uk/ddcommand.htm)

---

