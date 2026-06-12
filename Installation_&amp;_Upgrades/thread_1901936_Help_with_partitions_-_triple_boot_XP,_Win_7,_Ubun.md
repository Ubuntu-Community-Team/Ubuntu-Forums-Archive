---
title: "Help with partitions - triple boot XP, Win 7, Ubuntu 11.10 on one harddisk"
date: 2011-12-29
forum: Installation &amp; Upgrades
---

### Post by dadonka on 2011-12-29
Hi!
I'm a newbie, so I'd appreciate a bit of help with partitioning:
I  have a Samsung RF510 64-bit laptop with Windows 7 preinstalled. Samsung  has a built-in  recovery solution. I would like to start the whole  installation from scratch first XP, then Win 7 then Ubuntu. I've been  searching ... but I'm not really getting satisfactory answers.

These are the current partitions:

no drive letter   20 GB            Primary  (recovery partition)
no drive letter   100 MB           primary  (System, Active)
C:                    231 GB NTFS   primary (boot, page file, crash dump)
D:                    344 GB NTFS  Ext/logical

Sooo my question:

How  should I partition the harddisk? Obviously, I would like a back door in  case it all goes wrong. Apparently I'm supposed to leave the recovery  partition, then allocate a primary to each windows OS and then use  logical partitions to install ubuntu. Can that be right? But I can only  use 3 primary partitions and I need one to boot, right? Now I've been on  a few sites to look for advice and this is my incomplete partition  table

Sda?   Primary – ext3 boot    Grub ?
 Sda?    primary?        recovery partition (recovery partition? Remove this part and create    rescue                 CD?)
 Sda2     primary NTFS     -  for XP (not concerned about the size for now)

 Sda3    primary NTFS     -   for win 7  
 sda5    logical  ext4         - /root   50 GB
 sda6    swap 2 GB
 sda7    logical  ext4         -   /home


I'm  a bit confused about the boot partition ... and what do I do about the  recovery partition? I am aware that you can only have a max of 4  primaries or 3 primaries and a number of logical partitions.

Another  tricky bit for me is getting the windows installations sorted. Now  apparently, I can download a win 7 iso and use my license key to  activate which will hopefully mean I get a clean install without all the  Samsung bits. My XP version is ancient and will not recognise the SATA  disk. I will slipstream XP and SP3 to a bootable CD using nlite. I've  done that before on an older laptop and that worked. 

Right now I'm a bit worried that I end up with an unusable laptop ...

... so any help, tips or links would be fantastic!

Thanks in advance
dadonka

---

### Post by darkod on 2011-12-29
1. You don't need a boot partition. One primary less.

2. I suggest making DVDs from the recovery partition and deleting it.

If current partitions are in the order you wrote them, that means you could have something like:
Primary 20GB for XP (is this sufficient for you?)
Primary 100MB win7 boot files
Primary 231GB Win7
Extended with NTFS, ext4 for /, optionally ext4 for /home, and swap partitions.

Depending how much space you need for the win7 system partition, I would suggest shrinking it a bit and you can make the extended larger including one NTFS partition inside it which win7, XP and ubuntu can access and share. No need C: to be 231GB unless you really need all that space.

As for downloading win7 dvd, I am not aware of any legal download even when you do have licence that came with your laptop. I think your only option is the recovery DVDs. If there really is legal download, even better for you.

---

### Post by dadonka on 2011-12-29
Wow, that was quick. Thanks very much. I'll give it a try before I mark this as solved.
Regarding the Windows 7 iso - I'll check whether that is legal before I go ahead.
Thanks again
Dadonka

---

### Post by darkod on 2011-12-29
Just make sure the restore software offers the possibility to create the DVDs. Most time it does but it can be different for different manufacturers and machines. Create them before deleting the partition.

---

### Post by dadonka on 2011-12-29
Hi Darko! Thanks.

I checked the windows ISO. I also found a windows 7 iso download on CHIP.de linking to the same source (CHIP is a very well-known German computing site - highly unlikely they would be offering illegal downloads). They have German versions. Anyway, I got the version I need and checked the hash codes (from two different sources). I don't think there's much more I can do to check.

Dadonka

---

