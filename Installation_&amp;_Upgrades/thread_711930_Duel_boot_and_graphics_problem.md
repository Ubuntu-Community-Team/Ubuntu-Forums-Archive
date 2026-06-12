---
title: "Duel boot and graphics problem"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by damfoose on 2008-03-01
I built a new PC around christmas time.

HD's are raid 0 (stripe) for 2 x 320 gig sata 2 hd's which are partitioned 50 gig Xp 50 gig Vista and 3 other partitions for my games programs and documents.
 I have a second 500 gig sata drive for other stuff generally iso backups of my apps as my boy has a habbit of borrowing disks and scratching them.

 Also have an 80 gig standard ide drive just for linux.

 The mother board is an XFX 780I nvidia chipset.

  The problem I am having is I cant use the graphics install disk so i grabed the text install one which worked and installed on the 80 gig ide drive but it did not see the other M$ installs when grub checked for other operating systems. Upon reboot my pc came up with the standard M$ choose xp or vista screen with no mention of the grub choice first. 

 I think it is because Grub could not read the Raid 0 drive which shows as scsi in the disk management / partitioner when installing ubuntu. So it installed itself in the mbr of the 80 gig IDE drive which is I why ubuntu wont boot by the looks of things.

 the only way I have found of booting ubuntu is to change the HD boot order in the bios which is a bit of a pain but it works.

  Errmmmm help please.

---

### Post by reyhan on 2008-03-01
maybe you must install in safe graphic safe mode

---

### Post by damfoose on 2008-03-02
> **reyhan said:**
> maybe you must install in safe graphic safe mode

 Sorry mate but I really think you should have read what I wrote properly as ubuntu is installed its the duel boot im having problems with.

  graphix is installed BTW found an easier way just do

 Goto nvidia and DL the linux driver bung it on a pen drive or a drive accessable from your ubuntu install

then

 ctrl-alt-f1 drops you to tty1

 then

sudo /etc/init.d/gdm stop

then 
./NVIDIA (packagename) .run

Dont let it Download a new Kernal make it build a new one

 let it auto configure X 

reboot when done and see your desktop as its supposed to be.

---

