---
title: "Can't install grub to hda6"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by tlknv on 2008-04-16
Hi All,
I tried to install hardy ( beta ) to hda6. I didn't want to ruin my main boot loader ( lilo ). So at the latest step ( 7th ) I selected  "advanced" and chose to install grub into hda6. At the end of the installation ( copying files ) grub said that it can't be installed into hda6 and that's a fatal error. The error message didn't provide any other helpful information. I will try to install hardy without grub. I don't know if grub can be correctly installed into hda6 or not. Anyway it looks like an installer error. If grub can't be installed into hda6 installer shouldn't allow that choice and wait for the end of the installation process before showing the fatal message. Should I report that as a bug ?
Thanks.
Boris

---

### Post by dstew on 2008-04-16
It sounds like a bug in the installer. A similar bug occurred before in I think some Gutsy CDs, and the workaround was to create an ext2 filesystem in hda6 instead of the usual ext3. Then grub would install. Then, you could change the ext2 file system to ext3 using the tunefs utility. At least that's what I remember. I think you should report this as a bug. See the [Launchpad page.]("https://launchpad.net/ubuntu")

---

### Post by torgrot on 2008-04-16
hda6 is a logical partition, I don't think even Ubuntu can boot off a logical partiion.  I think Grub at least needs to be on a primary partition.

torgrot

---

### Post by dstew on 2008-04-16
No, Ubuntu can function on a logical partition, and grub can load its stage2 from a logical partition. The grub boot loader goes into the MBR of a drive, which is the first sector of track 0, and stage1.5 goes into the rest of track 0, if it will fit. Track 0 is reserved for boot loaders, and is never a part of any partition.

---

### Post by tlknv on 2008-04-16
Hi All,
Thank you for the replies. Actually I formated that partition as reiserfs. 
I wanted to keep lilo as my main boot loader. And the main reason for installing grub ( into hda6 ) was either 1) I need to know the parameters that should be passed to the kernel
or
2) I could try to use grub from lilo if it's possible.
Boris

---

