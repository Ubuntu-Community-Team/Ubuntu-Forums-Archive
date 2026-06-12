---
title: "One more question concerning hda, sda, Uids and feisty"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by A-1337 on 2007-04-26
Hello!

Once upon a time I've rewrote /boot/grub/menu.lst and /etc/fstab by hand, wiping away all uids and put /dev/hdas on their place. Latter, during some updates and upgrade to feisty, I've been having a lot of "good time" rewriting these files again and again.

The question is there chance for redemption for me to get back to the uids or I'm condemned to rewrite them for eternity?

---

### Post by pxwpxw on 2007-04-26
Well, I just found that after upgrading from 610 to 704 feisty, what used to be /dev/hd-- is now /dev/sd-- thats for 2.6.20-15-generic image i386. so the only constant is the UUID, but it doesnt exactly roll off the tongue. Everything seems to be working. (so far).

---

### Post by A-1337 on 2007-04-26
[q]I just found that after upgrading from 610 to 704 feisty, what used to be /dev/hd-- is now /dev/sd-- thats for 2.6.20-15-generic image i386[/q]
Yep, that's right. There was another case also: I move /boot to another partition, correcting fstab and grub conf respectively. Then,after some update, I have grub configuration rolled back to the initial state and os unbootable.

---

### Post by silverbullet007 on 2007-04-26
So exactly how are you editting the menu.lst and fstab files?

---

### Post by A-1337 on 2007-04-26
I've changed uids to /dev/hdas. That's all.

---

### Post by silverbullet007 on 2007-04-26
So you were able to install or upgrade to 7.04 then this issue began happening after the reboot?  What Im wondering is if they're a file or set of files I could alter within the ISO to reflect changes such as this. So the LiveCD would correctly recognize my hardware and begin the install.

---

