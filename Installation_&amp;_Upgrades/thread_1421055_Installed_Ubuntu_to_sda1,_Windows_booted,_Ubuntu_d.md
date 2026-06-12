---
title: "Installed Ubuntu to sda1, Windows booted, Ubuntu didn't. (SATA drives)"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by sibble on 2010-03-03
So I basically just erased a partition, that I thought my Windows OS was installed on.  Unfortunately, it was an archive of misc media...  Anyway, it was pretty fun waiting for the install to complete, reboot and I'm like crossing my fingers to see everything works fine, then I see Windows pop up hah.  It was funny and sad at the same time ;)

Anyway, this is how Windows displays my drives:

```
Hard Drives:

Maxtor 6L250R0 EIDE/Ultra ATA/133 7,200RPM 250GB
C: 214.22GB Primary Basic NTFS
19.54GB Unallocated

Maxtor 6H500F0 SATA 7,200RPM 500GB
F: 446.23GB Primary Basic  NTFS
19.53GB Unallocated

Maxtor 6L300S0 SATA 7,200RPM 300GB
H: 260GB Primary Dynamic NTFS
15.75GB Unallocated
```

GParted displayed /dev/sda1 as an unknown partition (with a size of 279.47GB... I thought I checked everything, but I guess I missed this.)

This is how GParted displays my drives:
```
Hard Drives:

/dev/sda - 279.47GB
  \/dev/sda1 - unknown - boot

/dev/sdb - 465.76GB
  \/dev/sdb1 - NTFS - 446.23GB
  \ 19.53 unallocated

/dev/sdc - 233.76GB
  \/dev/sdc1 - NTFS - 214.22GB
  \ 19.54 unallocated
```

I *believe* I've already tried installing Ubuntu to the unallocated spaces in sdb and sdc, however it's been a while.  (this is a custom built box that was built like 4-6 years ago.)  I can say that I'm not completely sad about loosing that partition, I was trying to free up space anyway and I can't think of anything specific that was on there :)

Anyway, what do I have to do to get Ubuntu to boot.  My original plan was to destroy the partition Windows was installed on, but now that I haven't done that and I've already screwed up a partition, I'm a bit fuzzy as to how/where I should have installed Ubuntu to begin with.

A point in either direction would be greatly appreciated!

EDIT:
```
BIOS - Primary Master - Maxtor 6L250R0 Ultra DMA-6 251GB
```

---

### Post by presence1960 on 2010-03-03
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by sibble on 2010-03-03
Actually read your post on another thread earlier and ran your script ;)  I came to find out I had enabled RAID options in my BIOS, disabling it fixed the problem.

Just booted LiveCD, /dev/sda1 is now showing MS Vista, 250GB, which is perfect.

Erasing partition now, thanks for the reply :)

---

### Post by sibble on 2010-03-03
Works perfectly.

---

### Post by presence1960 on 2010-03-04
Glad you got it working. Enjoy ubuntu!

---

