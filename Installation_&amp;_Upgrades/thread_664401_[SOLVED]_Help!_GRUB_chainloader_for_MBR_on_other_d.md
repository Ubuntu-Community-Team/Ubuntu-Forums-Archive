---
title: "[SOLVED] Help! GRUB chainloader for MBR on other disk"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by starfry on 2008-01-11
Hello, Could someone tell me how to tell GRUB on one physical disk to load the MBR on a second physical disk ?

I have a system with Windows on the primary hard disk. I can not change the MBR on this disk, one reason being there is a whole disk encryption system on it (SafeGuard Easy).

I have swapped the boot order in the BIOS so the system boots the second physical disk, where I have installed GRUB into the MBR and it happily boots Gutsy installed on the second physical disk.

I want to chainload the MBR of the first physical disk but I can't work our how to do it - All I can manage with chainloading is to load from the partitions.

Pointers greatly appreciated...

---

### Post by esteckis on 2008-01-11
I am a newbie, but you might want to look into Startup Manager?

[http://web.telia.com/~u88005282/sum/index.html]("http://web.telia.com/~u88005282/sum/index.html")

It is listed in the Synaptics Repo.

---

### Post by logos34 on 2008-01-11
> **starfry said:**
> I have swapped the boot order in the BIOS so the system boots the second physical disk, where I have installed GRUB into the MBR and it happily boots Gutsy installed on the second physical disk.

I want to chainload the MBR of the first physical disk but I can't work our how to do it - All I can manage with chainloading is to load from the partitions.

If you want to use grub to boot windows on a second disk (i.e. second in the Bios boot order), you need to add map commands to the menu.lst entry:

[http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)

---

### Post by starfry on 2008-01-12
Thank you for those links, they led me to the "map" command.

Here's what worked for me:


```

title      WIndows XP
rootnoverify  (hd1)
map              (hd1) (hd0)
chainloader  +1

```


The machine boots off the SECOND disk (/dev/sdb) but Grub sees it as hd0 for some reason.
I therefore refer to the first disk as hd1. The above does what I need: it launches the MBR on the primary hard disk.

---

