---
title: "HDIO_GET_IDENTITY failed for /dev/sdb"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by DillerDaller on 2011-10-22
Hello,

I installed Lubuntu 11.10 on my new external HDD (Western Digital, My Passport, 1 TB).
After installing and booting from the USB-HDD, my system stop while booting. I get the following message text:

**HDIO_GET_IDENTITY failed for /dev/sdb : invalid argument**

Then I installed Ubuntu 11.10, but it brings me to the same error message.... Any ideas, how to solve this problem? I searched the internet for this problem and I only find out that Western Digital has a lot of "disadvantages" with LINUX....

Thanks for help!

---

### Post by maestrobwh1 on 2012-03-04
I have the same problem.  Maverick kernel still boots system along with natty kernels but 3.0.0-16-generic gives this issue.  I think it might be a bug and specifically for me it has something to do with VIA_AGP and I have it blacklisted.  I have had the same thing with puppy linux until recently where something with VIA blocks the USB, sound and wifi.  Will just use maverick with Oneric until 12.04 comes out

---

### Post by agavras on 2012-03-24
Did you find a solution to this problem?

I am getting entries in /var/log/syslog every 5 minutes
ata_id[5845]: HDIO_GET_IDENTITY failed for '/dev/sdb': Invalid argument
ata_id[5863]: HDIO_GET_IDENTITY failed for '/dev/sdc': Invalid argument

Both disks are external 1.5TB USB disks

Most annoying is that if this happens during a write operation to the disk then I get thousands of "Buffer I/O error on device sdc1, logical block ..." entries and the filesystem is remounted read only

EXT4-fs error (device sdc1): ext4_put_super:818: Couldn't clean up the journal
EXT4-fs (sdc1): Remounting filesystem read-only

It looks like some process/script is probing the devices and is probably issueing the hdparm command that returns this error. Just guessing ... 

Thanks for any hint

---

### Post by PayPaul on 2012-04-28
I have a similar problem and it's also my external drive, a Western Digital Green 2 TB drive. Gparted was handy in identifying it. It's also attached to an open ended external box where the drive just slips into the SATA slots without it being a true enclosure. Easily hot swapped and I know that Windows sometimes has a bit of lag time seeing it. Why would this totally stall the boot as the hard drive isn't absolutely vital to the boot sequence? I imagine that Ubuntu, unlike Windows, doesn't have autoplay when it starts. All that recognition of drives occurs at boot level only. The message is similar to the above. 

ata_id[463]: HDIO_GET_IDENTITY failed for '/dev/sda': Invalid argument

Does my hard drive need a grammar check? LOL! 

It doesn't seem like anyone has an answer to this problem yet it seems common. I at first thought I was the only one. 
Of course I also get the busybox problem as well on top of it. I am, eventually able to boot into Ubuntu but it's time consuming to do so. Is there a boot diagnostic program that can be downloaded and installed to pinpoint the source of the problem and correct it?

---

