---
title: "Error reading from CD-ROM during USB stick install of Ubuntu Server 10.04"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by Thornsten on 2010-06-06
I downloaded the Ubuntu Server 10.04 64bit ISO and the universal USB installer, created a USB install disk and booted from it. I started the installation and right after keyboard setup I got an error saying Unable to read from CD-ROM, retry/abort. Looking at the alt-f4 log it was unable to find a file, fs-secondaryblahblahblah.udeb

I hit alt-f2 and cd'd to /cdrom/pool/main/l/linux (I think, this is all from memory) and found that file.... almost. The file there was fs-secondaryblahblahblah.ude, no b on the end. I tried renaming it but the filesystem was mounted read-only.

So, cd back to /
Type mount and hit enter.
Take note of the cdrom entry, at the beginning of that line it will say /dev/?????  Mine was like /dev/svd0 or something like that. Remember whatever that is.
Then type umount /cdrom
Then type mount -t vfat /dev/????? (whatever your device was from earlier) /cdrom
That will mount the cdrom rw so you can rename the file to .udeb

Then press alt-F1 and press enter to retry and the installation will continue like normal.

---

### Post by ermannob on 2010-06-27
Thanks mate. You saved my afternoon!

---

### Post by syuzh on 2010-06-28
Another simpler option is to just go into your USB drive with all the installation files and rename the file there, prior to the actual installation.

pool\main\l\linux

---

### Post by Cavillis on 2011-02-10
this issue happened to me while installing 10.10 server - have you opened up a defect? I think the cause is the program the documentation recommends for making ubuntu installable from USB. I would bet that the names are getting truncated due to an arbitrary limit on the length of file names

---

### Post by gadikas on 2011-03-02
yea thanks 
g:\pool\main\fs-secondary-modules-2.6.35-22-generic-di_2.6.35-22.33_amd64.udeb
missed the b at the end :/

---

