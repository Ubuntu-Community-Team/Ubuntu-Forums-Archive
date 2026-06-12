---
title: "Dual Boot - Grub issues"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by PureLoneWolf on 2007-10-26
Hi all

I have tried searching but can't find any similar issues.

I have the following drives:

hda (IDE 80gb)  <--Ubuntu 
hdb (IDE 500gb)
sda (SATA 120gb) <-- 20gb Windows XP partition, 100gb NTFS volume)
sdb (USB 320gb)
sdc (USB 160gb)

Windows XP has been running for a long time, but I decided to dual boot to ubuntu to see if it is plausible for me to make a complete switch.  So I installed to hda and told ubuntu to have the whole disk.

On rebooting, no boot loader, XP booted as if Ubuntu never existed.  I realised that this was likely to happen because my motherboard insists on booting from SATA if SATA is connected.  I guess ubuntu installed grub to what it believes is the first disk (hda).

So I re-ran the installation from the live CD, but this time told it to install Grub to hd2 (sda).

Now when I boot, I get the word GRUB repeated indefinately across the screen and it never stops.  If I insert the live CD and tell it to boot from the 1st Hard Disk, I get the word GRUB in the top left corner, and nothing more happens.

I can fix the MBR and get my XP back and running (I even took a ghost image to be safe), but I would like to figure out what is going on.  I have so far resisted fixing it and am running from the Live CD at the moment....

I am pretty new to linux, but am at a very high level with MS based products.

Any suggestions would be greatfully recieved.

Many thanks
Dave

---

### Post by dabl on 2007-10-26
Basically, while it may appear superficially that you're still alive, you've actually gone to Hell!  :lolflag:

Here's a pretty good link for Grub work:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

Good luck with it!  :)

---

### Post by siralphred on 2007-10-26
here is another help [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by PureLoneWolf on 2007-10-26
Many thanks

I have ended up upgrading my bios - This allows me to select hda as the default boot device now.

This means Grub works and allows me to boot Ubuntu, however, when I tell it to boot XP it gives me an NTLDR error.

If I switch the boot order back to the sda in the bios, XP boots as normal.

Any suggestions?

---

### Post by PureLoneWolf on 2007-10-26
Additional Information:

The entry for XP within /boot/grub/menu.lst:

```
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

I ran sudo fdisk -l and got this:

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9fd6ec66

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9327    74919096   83  Linux
/dev/hda2            9328        9729     3229065    5  Extended
/dev/hda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/hdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcef94476

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23410c86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       14593    96245415    f  W95 Ext'd (LBA)
/dev/sda5            2612       14593    96245383+   7  HPFS/NTFS

```

Everything seems ok - Although I will admit to not understanding the map statement in menu.lst

Does this help?

Its not a huge deal for me to change the boot order when I want XP and vice versa, but it would be preferable to select from Grub on bootup and not have to mess around.

Thanks in advance for any help

---

### Post by louieb on 2007-10-26
All the map statements are for is to fake out XP - that is make it think its on the 1st boot device. Don't have the sata ide mix so don't know the specifics but have see lots of threads about dual booting with a sata ide mix. 
[Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

The above has some links to sata ide fixes. 
Good Luck.

---

### Post by logos34 on 2007-10-26
That link louieb suggested is really good.

But you could try this:

**gksudo gedit /boot/grub/menu.lst**
> 
title		Microsoft Windows XP Professional
root		(hd**1**,0)
savedefault
map		(hd0) (hd**1**)
map		(hd**1**) (hd0)
chainloader	+1

And then change **/boot/grub/device.map** to match:

> (hd0) /dev/hda
**(hd1) /dev/sda**
(hd2) /dev/hdb

any luck?

---

### Post by billrad1 on 2007-10-26
I had a problem like this a long time ago. Turned out the IDE drive had to be on the middle ide ribbon connector, not the end.

Even when I updated my bios, etc etc, this was an issue.

hope this helps

Bill

---

### Post by PureLoneWolf on 2007-10-27
> **logos34 said:**
> That link louieb suggested is really good.

But you could try this:

**gksudo gedit /boot/grub/menu.lst**


And then change **/boot/grub/device.map** to match:



any luck?

Superb, that did it - Changing the device map so that hd1 was the windows drive and it all works.

Ta muchly - Now if I can just get my twinview behaving itself I will be onto a winner :)

Thanks

---

