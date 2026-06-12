---
title: "How do I tell Ubuntu to install on this partition?"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by eXSBass on 2005-11-26
Hi! I'm new here. First i'd like to appologise if this topic has been covered.
Okay, here's the picture (sorry about the size):
[[IMG]http://img111.imageshack.us/img111/4671/linux0028es.th.jpg[/IMG]](http://img111.imageshack.us/my.php?image=linux0028es.jpg)

How do I tell Ubuntu Linux to install on "#7 logical 31.2 :) ntfs /media/sda7"?

I don't want to install on #1 primary because that's my Windows Partition. #5 is my Work partition and #6 is my multimedia partition. I created partition #7, when I was installing Windows as some room for Ubuntu.

If anyone could shed some light I would appreciate it.
Thanks

---

### Post by Xian on 2005-11-26
[QUOTE=eXSBass]How do I tell Ubuntu Linux to install on "#7 logical 31.2 - ntfs /media/sda7"?[/QUOTE]
Highlight that partition and hit enter, format it as a Linux FS like ext3, reiserfs, etc., and set the mountpoint as "/". Then save changes by writing to disk.

---

### Post by Xian on 2005-11-26
oops...double post.

---

### Post by eXSBass on 2005-11-26
[QUOTE=Xian]Highlight that partition, format it as a Linux FS like ext3, reiserfs, etc., and set the mountpoint as "/". Then save changes by writing to disk.[/QUOTE]

Thanks for the quick response. Before I switch the machine off just one last question. How do I set the mountpoint as "/"? Cheers

---

### Post by Xian on 2005-11-26
It will be from an option line in the partition menu.
Then a menu list is presented.

---

### Post by aysiu on 2005-11-26
[QUOTE=eXSBass]Thanks for the quick response. Before I switch the machine off just one last question. How do I set the mountpoint as "/"? Cheers[/QUOTE] Click on the mount point (which is probably "Do not mount") and then it'll bring you to a new screen with several mount options (/boot, /home/, /var...). Select the one that's just a forward slash (/)

---

### Post by bwog on 2005-11-26
You need to select more options in that partition menu, if you cant figure it out, break of installation and come back here to ask questions. I have this:

root partition; use as Ext3, format yes, mount point /, mount options default, bootable flag on, size x GB.

Swap partition; use as swap, bootable flag off, size (less than 2 GB). It doesnt matter when swap gets formatted.


home partition; use as ext3, mount point /home, etc.

---

