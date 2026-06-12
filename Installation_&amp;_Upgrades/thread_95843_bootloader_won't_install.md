---
title: "bootloader won't install"
date: 2005-11-27
forum: Installation &amp; Upgrades
---

### Post by Guy2 on 2005-11-27
Installing Breezy Badger from a magazine coverdisc (Linux Format, FWIW).

All goes fine until it's time to instal the bootloader. I got a fatal error, "Unable to install GRUB in (hd0)." Tried again, same result.
Tried the option to instal LILO. Same problem.

I have partitioned my single second-hand HD into /, swap, and /home. I had to do a manual instal to create /home, as a logical partition.

Any ideas?

---

### Post by bwog on 2005-11-27
You can use the method here [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)
to restore grub.

If that doesnt work you can use the same method to put grub on floppy /dev/fd0 or on a bootable usb stick, and figure out later what went wrong.

---

### Post by Guy2 on 2005-11-27
did:
# grub-install /dev/hda
got:
/dev/hda does not have any corresponding BIOS drive.

trying other things got:
/dev/hd0: Not found or not a block device
and:
/dev/fd0 does not have any corresponding BIOS drive.

Edit:
Just noticed the CD is primary IDE and HD is secondary. Could be a bit of plug-swapping is in order...
Not sure why the floppy install failed. Not mounted?
Thx for the help anyway.

---

### Post by bwog on 2005-11-28
If you still have problems after checking bios settings, master/slave setting etc., post some info on your system and the partitions, (size,  filesystem, etc.).

---

### Post by No-Brain on 2005-11-28
Some BIOS have a setting that prevents virus from writing to the MBR.  Look for something that refers to Virus warning or prevention.  The problem you are having is exactly what happens when it is set.
Roger

---

### Post by Guy2 on 2005-12-17
For the record:

Turned out the HD was duff. DOS couldn't fdisk either. Replaced it, and all now fine.
</dumb bunny>

Thx all for your suggestions.

---

