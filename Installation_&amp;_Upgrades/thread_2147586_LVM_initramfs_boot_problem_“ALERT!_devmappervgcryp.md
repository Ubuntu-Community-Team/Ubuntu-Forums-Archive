---
title: "LVM initramfs boot problem: “ALERT! /dev/mapper/vgcrypt-root does not exist.&quot;"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by klein4 on 2013-05-22
I followed the guide linked below to create a clean install  of Ubuntu on a LUKS-encrypted partition. The only differences are that I  used Ubuntu 12.04 rather than 11.10 and I made less LVs than that guide  does (I used 3: swap, root, and home).

  When I boot, I get the message quoted in the title, then get dropped into an initramfs shell. From that shell, I can run `cryptsetup luksOpen /dev/sda2 pvcrypt`,  then Ctrl-D to exit the initramfs shell, and everything boots as it  should. But I can't figure out how to make it prompt me to open that  LUKS archive automatically rather than dropping me into the initramfs  shell.

  The guide: [http://ubuntuforums.org/showthread.php?t=1867970](http://ubuntuforums.org/showthread.php?t=1867970)
  
Any suggestions would be greatly appreciated.

---

### Post by Herman on 2013-05-25
Have you taken a look at your /etc/crypttab file?
Take a look in the following links, '[[COLOR=#0000ff]Encrypted Filesystem LVM How-to[/COLOR]]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto")' - Ubuntu Community Docs, see especially this part: [[COLOR=#0000ff]final preparation[/COLOR]]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto#Final_preparation").

---

