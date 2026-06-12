---
title: "Where does GRUB go?"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Scooter_X on 2010-05-02
I was just going to install Lucid, but ran across something that I wanted to understand first. I have win7 and Ubuntu both on my laptop. I have a partition for windows, a partition for ubuntu, a swap space, and the rest is just for backup of all my stuff so I don't have to worry about dumping it all onto a bunch of DVDs and then putting it back on afterwards. Anyways, so I manually selected my partitions for Lucid, but then I noticed an option for installing a bootloader. Grub, I assume. But what partition should I install it in? I don't know where it was before. Any help appreciated. Thanks a bunch!

---

### Post by oldfred on 2010-05-02
Computers only boot from the MBR of the drive that is primary master. Now with SATA you just select boot drive. To use Ubuntu you have to install grub to the MBR, sda, sdb etc and choose that drive in BIOS to boot.

Many users now are installing grub2 to the windows partition that already has essential windows boot files and then prevents windows from booting. The have to then fix the boot partition for windows.

I do not know why they even opened up the choice to install to partitions. They do not want grub2 installed to partitions as it uses blocklists that can give issues later if any boot files get relocated. Only very advanced users that understand the risk should install to a partition and they know they have another boot loader to chainload into the partition. You cannot boot from a partition except chainbooting from another boot loader (that is how grub boots windows).

---

### Post by Scooter_X on 2010-05-02
Okay, I've been trying to understand exactly what it is you're saying. I don't really know much about MBR, sda, sdb and so on, but I got to thinking, and just now it hit me... (I've attached a screenshot of GParted on my laptop) If my 'Primary' partition is labeled 'boot', then grub should probably go there. I don't want necessarily to install grub2, but just want the option to boot one or the other. THEN I realized that grub is probably already ON my primary partition, and I wouldn't have to even re-install the dang thing!! Am I correct in my thinking?

---

### Post by oldfred on 2010-05-03
IF windows boots (as boot flag says) from sda1, windows has essential boot files in the partition boot sector (starts just before the partition). If you install grub on sda1 you destroy windows. I have responded to 20 or 30 folks who have done that since the upgrade from old version says (very incorrectly) to install grub everywhere. Repairs are possible but if grub is just installed to sda not sda1 or sda2 then there would not be any issues.

Just look at the pictures to get a general picture of how windows works. Read the entire site to fully understand windows boot process.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by efflandt on 2010-05-03
If you want to put grub on a partition instead of in the mbr, I would partition the drive differently.  The older boot loader lilo could boot from a primary or "extended" partition (I don't think from a logical partition).  I don't know if grub works on an extended partition, and not sure if a standard mbr would even find it on a logical partition.

But you do NOT want to put grub on your Windows partition, because that would mess up Windows.  So best options are either the mbr, or a primary Linux partition (in which case you need to change that partition to the boot partition with gparted or fdisk).

So I would leave the mbr alone, and partition it:

sda1 primary ntfs Win7
sda2 primary ntfs Linux (with grub, marked as boot from gparted or fdisk)
sda3 extended
sda5 logical swap
sda6 logical ntfs data

I did that with just 2 partitions, Win7 ntfs and Linux ext3 and was sure that I put grub on the 2nd partition.  But I still had trouble booting Win7 after removing Linux (something like could not find boot.ldr) and I had to boot the Win7 disk a couple of times to fix that.  I ended up putting Linux with grub on a USB drive instead (since the laptop was for someone else).

---

### Post by Scooter_X on 2010-05-04
Thanks, oldfred for that article. It helped quite a bit. So anyway, I was just about to try and see if it would work if I installed grub on the same (extended) partition as Lucid, and then if it didn't I'd just adjust my partitions a bit to something like efflandt suggested. I did notice something as I was about to install, that I wanted to check first. The choices it gave as my available partitions in which to install grub were as follows:

/dev/sda ATA TOSHIBA MK3252GS (320.1GB)
/dev/sda1 Windows 7 (loader)
/dev/sda5
/dev/sda7

Where I'm thinking "oh I can install grub on /dev/sda because then It'd be at the very first part of the hard drive and probably work wonderfully" BUT, why in the heck is there a 'partition' before my /dev/sda1 partition? According to GParted, /dev/sda1 IS the first partition on the drive. Why do I even have that other option of /dev/sda if it doesn't even exist according to GParted?

---

### Post by oldfred on 2010-05-04
The MBR is not a partition but just the first sector of a hard drive allocated for boot info. You cannot use it for anything else. 

The MBR dates back to the first IBM PC which had a minimal BIOS that was just barely smart enough to jump to the hard drive's first sector to continue booting.
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

If you install grub anywhere else you have to have another boot loader in the MBR that allows you to chainboot into the partition boot record  -PBR or boot sector.  This is exactly what grub does to boot windows as it has part of its boot loader in the windows PBR again another sector allocated for boot info not formated as part of the partition.

---

### Post by Scooter_X on 2010-05-04
> **oldfred said:**
> The MBR is not a partition but just the first sector of a hard drive allocated for boot info. You cannot use it for anything else. 

...so that first /dev/sda thing is the MBR?

---

### Post by oldfred on 2010-05-04
Well sda is the entire drive, but when installing a boot loader to a drive it has to be installed to the first sector or the MBR.

---

### Post by Scooter_X on 2010-05-04
If I select /dev/sda as my desired location to install GRUB to, it would be like selecting the MBR of the drive as the place I want to install GRUB to. Is that correct?

---

### Post by oldfred on 2010-05-05
Yes if you only have one drive. 

Of course the second drive is sdb, third sdc. Your BIOS then has to be set to boot from the drive with grub in the MBR. Defaults are usually BIOS boots sda or drive 0 and the boot loader in the MBR then starts the loading process. 

Old computers with IDE drives were are not able to set in BIOS but with jumpers on the drive and/or position on the cable for cable select. Computer BIOS then passed booting to primary master drive. Many old computers could have up to 4 drives, primary & secondary channels, and master & slave on each channel.

---

### Post by Scooter_X on 2010-05-05
Ah-HA! That makes sense. 

And I never knew what sda/sdb/sdc meant, just that it referred to a drive. That helps a bunch. Thanks.

Anyways, If anyone was following this to figure out what was wrong with THEIR setup, I wound up just scrapping my windows partition anyways, and now I don't run windows anymore. I'm trying Wine and CrossOver and such to run the games I was playing in windows. Not that I play much anyway. That's the only reason I wanted windows still.

...Maybe that was why the 'helpful' upgrade message says to just install grub to each partition, that way people get frustrated and just stick with Linux altogether? Dunno, but either way it worked. :D

---

