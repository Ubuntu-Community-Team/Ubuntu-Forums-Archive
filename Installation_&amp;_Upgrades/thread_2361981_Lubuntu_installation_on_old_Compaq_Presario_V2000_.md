---
title: "Lubuntu installation on old Compaq Presario V2000 laptop fails"
date: 2017-05-22
forum: Installation &amp; Upgrades
---

### Post by mukesh11 on 2017-05-22
I am trying to install Lubuntu Version 16.10 (32 bit) on old Compaq Presario V2000 laptop but not being successful.
The laptop originally had a PATA hard drive which was replaced with the following PATA/SSD:

[http://www.ebay.com/itm/2-5-PATA-IDE-SSD-128GB-for-DELL-D610-9300-D810-HP-V2000-IBM-T43-Alesis-Fusion-/171237136970?hash=item27de875a4a:g:JFAAAOSwu4BVmP~y](http://www.ebay.com/itm/2-5-PATA-IDE-SSD-128GB-for-DELL-D610-9300-D810-HP-V2000-IBM-T43-Alesis-Fusion-/171237136970?hash=item27de875a4a:g:JFAAAOSwu4BVmP~y)

The error I am getting is:

ata1: SRST failed (errno=-16)

This probably points to the fact that Lubuntu can't see my hard drive. I tried all combinations of the 4-pin jumper settings
but it didn't help.

Please post if you know the answer.

---

### Post by ubfan1 on 2017-05-22
Are you saying when you run lubuntu from the install media, you cannot see the drive?  Does it show up in the BIOS settings?  I could not boot an HP v3000 from a sata disk in a pata disk caddy, but the disk itself was usable as long as it was not scanned by grub in it's initial sequence.  I could boot from a USB, and run from the caddy though.

---

### Post by Autodave on 2017-05-23
Unless there is another HD in the machine, the jumper should be on pins A & B. Depending on how old the machine is, you may have to access the BIOS and tell it what size HD is in there. If the HD is not showing in the BIOS, recheck your connections. In still no good, you could have a bad drive or a failed motherboard.

What is/was the reason that you replaced the HD?

---

### Post by mukesh11 on 2017-05-23
Thanks for your post. Please note that I can run Lubuntu from DVD media but when I try to
install it then Lubuntu can't see my hard disk. 

The machine originally came with PATA disk which I have upgraded to PATA/SSD. 
This new disk was upgraded to make this old laptop faster. I have Windows 7 (32bit) installed on it
and it runs fine. I have created ext4 and swap partitions in free space to install Lubuntu to make it dual boot 
system. The BIOS can see the SSD. The laptop can take only one hard drive.

I have the jumper set to A and B and it doesn't work. I also tried BD, CD and AC to no avail. 
Please let me know what to do next.

---

### Post by ubfan1 on 2017-05-23
When running from the DVD, if you scan the system messages for disks, what do you see?  dmesg |grep sd
should have messages regarding the disk sda or maybe sdb.  Since you have only one hard drive, I'd expect sda to be the disk seen.  If you see it, maybe you can do the partitioning at this point, before the install, and see if that helps.

---

### Post by mukesh11 on 2017-05-23
I ran the dmesg | grep sd command but it doesn't show up sda or sdb. It clearly cannot see the hard drive.
Please suggest what to do.

---

