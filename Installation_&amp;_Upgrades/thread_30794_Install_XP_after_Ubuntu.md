---
title: "Install XP after Ubuntu"
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by Lord C on 2005-04-30
I am a 100% Ubuntu user, and I need to install XP as dual boot.

I know when I install XP it is going to overwrite my MBR, erasing Grub - and I won't be able to boot into Ubuntu.

What can I do to prepare, and how can I fix the dual-boot after I have installed XP?

Thanks in advance.

---

### Post by TravisNewman on 2005-04-30
If you have the live cd handy, you can install Windows, boot off the live cd, mount your ubuntu partition, and execute
chroot /path/to/mounted/ubuntu/partition #*obviously change that to the real path*
sudo grub
root (hd0,0) *#or wherever your /boot is. if you have a separate boot partition, it's that one, and if not, it's just your ubuntu partition. subtract one from the last number though, so if your ubuntu partition is on /dev/hda1, grub sees it as (hd0,0), hda2 will be seen as (hd0,1), and so on.*
setup (hd0)

Then after booting into ubuntu to make sure it works, you'll have to edit /boot/grub/menu.lst to add Windows. That file is well documented and will tell you how to add Windows

---

### Post by Lord C on 2005-04-30
[QUOTE=panickedthumb]If you have the live cd handy, you can install Windows, boot off the live cd, mount your ubuntu partition, and execute
chroot /path/to/mounted/ubuntu/partition #*obviously change that to the real path*
sudo grub
root (hd0,0) *#or wherever your /boot is. if you have a separate boot partition, it's that one, and if not, it's just your ubuntu partition. subtract one from the last number though, so if your ubuntu partition is on /dev/hda1, grub sees it as (hd0,0), hda2 will be seen as (hd0,1), and so on.*
setup (hd0)

Then after booting into ubuntu to make sure it works, you'll have to edit /boot/grub/menu.lst to add Windows. That file is well documented and will tell you how to add Windows[/QUOTE]
 My hda1 is my downloads partition.

sda1 is infact my ubuntu partition, so would I use "root (sd0,0)"? :S

The only reason I ask is because I saw someone saying something about sd0 translating to hd0

Thanks for your help.

---

