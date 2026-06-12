---
title: "Grub can't read RAID array after install."
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by Keatonguy on 2008-11-13
I'm trying to build an Ubuntu LTSP server, something I've done before, though on a smaller scale, and I'm trying to put it on a server with a RAID array. Raid's already configured, so I just run through the installation as usual, it goes off without a hitch, but when I try to boot, I get this error:

ALERT! /dev/mapper/longstringofnumbers does not exist. Dropping to a shell!

Then it drops me into busybox. I'm not quite sure where to go from here, can anyone offer some insight into getting this thing to work?

EDIT: Okay, it's not grub, it's Ubuntu. The boot screen comes up, bounces around for a while, then drops me the aforementioned error and leaves me in busybox. Any ideas why it wouldn't be able to find it at boot time, despite installing without a hitch?

---

### Post by caljohnsmith on 2008-11-13
I saw a thread recently of someone with a similar RAID problem, and their solution was to add "rootdelay=130" at the end of their kernel line in /boot/grub/menu.lst, similar to:
```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d0b10c15-66ed-4d1c-b7f6-c1fc131636f7
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash [COLOR="Red"]rootdelay=130[/COLOR]
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

```
How about giving that a shot and letting me know how if it helps.

---

### Post by Keatonguy on 2008-11-18
No dice. It just sits there longer, then gives me the same message. This happens after the boot screen though, so GRUB is obviously grabbing the kernel just fine.

---

### Post by Keatonguy on 2008-11-19
I may have a new lead on this. If I understand how raid works correctly, the operating system shouldn't need any sort of special drivers to interface with it, because the mirroring is handled in the BIOS, the operating system should read it just like any other hard drive. But when I'm running the installer, just before the partitioning options come up I see what looks to be some sort of raid-related library loading up. Is this library perhaps clashing with the internal setup?

---

### Post by psusi on 2008-11-20
You might want to read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).  Also when you are at the busybox prompt, try running dmraid -ay and see if it activates the array.  If it does, exit and the boot should continue.

---

