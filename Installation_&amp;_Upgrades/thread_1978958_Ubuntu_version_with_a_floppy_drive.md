---
title: "Ubuntu version with a floppy drive?"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2012-05-12
I can boot into Win7 and I see and use a floppy drive. Boot into any Ubuntu since about version 9 and I see a device under [Menu]Computer -> (icon) Floppy Drive. If I try to open that icon with a floppy inserted, Ubuntu asks to 'Insert media'.

I would take the floppy drive out of my tower box, but then I don't have the faceplate to cover the hole.

Has anyone else tried to use a floppy with Ubuntu version 10+ ?

---

### Post by Frogs Hair on 2012-05-12
I have an external floppy and every version of Ubuntu since 9.10 has listed a floppy drive under computer weather it is plugged in or not . I last used it on 11.04.

---

### Post by lkraemer on 2012-05-13
Assuming you have udisks installed:

To mount a USB Floppy in Debian "Squeeze" I use:
```

sudo blkid
/dev/sdx: SEC_TYPE="msdos" UUID="2113-1602" TYPE="vfat"

``` 
Where x is the located floppy drive.  Then do:
```

udisks --mount /dev/sdx

```

When you are finished copying etc., just unmount the drive with:
```

udisks --umount /dev/sdx

```
Then remove the 3.5" Floppy Disk & Physical USB Drive.

The same commands should work in Ubuntu.

> 
I've also got this note saved on my Laptop from some posting on the Internet:

PROBLEM:  Can't mount Floppy in 10.04 LTS

To summarize, reading (and writing) a floppy disk in Lucid Lynx (10.04) requires three steps:

1. Allow yourself to use the floppy by going to System->Administration->Users and Groups->Advanced Settings->User Privileges
and click on "Use floppy drives"

2. Use the old version of udisks () by going to System->Administration->Synaptic Package Manager, find the udisks package,
mark udisks for reinstallation, click on Package->Force Version, and select the 1.0.1-1build1 version (which is the old version).
Then click on apply to finish the installation.

3. Remember to unclick udisks whenever Update Manager wants to install new updates, or you'll get the new version and
floppy disks won't work anymore!

After the old udisks is installed (and the machine is rebooted), when you insert a floppy a cute little icon comes up on the
desktop and in Nautilus (and on Disk Mounter if you have that installed). Left clicking on the icon and select Mount Floppy Disk
will put an icon in Nautilus, and then you read, write, and format the floppy just like any other drive.



lk

---

