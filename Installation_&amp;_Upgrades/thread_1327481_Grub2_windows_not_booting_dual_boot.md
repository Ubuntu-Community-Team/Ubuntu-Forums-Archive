---
title: "Grub2: windows not booting dual boot"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by eekie on 2009-11-15
I have installed Ubuntu 9.10 on 4 machines. Two x64 version on 64 bits machines, One netbook remix x86 and One 32 bits version on a 32 bits machine. Dual booting is no problem for x64 and netbook versions. /boot/grub/menu.lst still exists there, However the 32 bits version only installs grub2. And with this one windows does not start.
In all except the netbook windows was installed on  striped disks. Only on this one ubuntu was installed on a sata disk, the other two on the striped disks.
In grub.cfg the entry for windows reads:
menuentry "Windows 7 (loader) (on /dev/mapper/nvidia_dfifbcea1)" {
	chainloader +1 
When I edit this entry in the boot menu: chainloader +1 is echoed.
When booting with cntrl x the message appears:
grub2 no mapping exists for `nvidia_dfifbcea1

Editing in grub.cfg seems to be prohibited. So it turned out to be. Even when booting as root the file was read only.
This looks like a bug in grub2.
Could anybody tell me what I can do to make windows bootable?

---

### Post by ajgreeny on 2009-11-15
First check all the files in **/etc/grub.d** are executable, particularly the files starting with a number **00_header** to **40_custom**.  Then run ```
sudo update-grub
```and windows should now appear in the menu.

---

### Post by darkod on 2009-11-15
mapper/nvidia sounds like trouble. I was just helping someone else here with same problem, he gave up. I need someone with more ubuntu experience to jump in.

What I figured out: mapper/nvidia means there are remains of raid on the sata drive. Don't know how, haven't used these software raids on desktops (just proper raids on servers).

You can clearly see this executing:
sudo blkid

The drive will be reported nvidia_raid_member. That is why instead of being "called" sda it is called mapper/nvidiablabla and grub2 obviously can't handle that.

It seems dmraid package can be used but have never used it and don't know what to tell you. Bottom line, this raid leftover has to be removed, somehow.

---

### Post by eekie on 2009-11-15
I already tried update-grub. No use!
Of course I do know that the trouble is caused by the software raid. I did a dual boot with ubuntu 9.10 32 bits and windows 7 on a machine with just sata disks, no problem.
I wonder why they replaced a good working program like grub, handling all software raid, by grub2?
Multi booting with windows and other linux distro's was so easy before grub2!

---

### Post by darkod on 2009-11-15
Well I didn't know you know that. :)
But if you know a way how to remove the nvidia_raid_member by dmraid or whatever, I would appreciate the advice. I will pass it on to the other person having the problem with the raid setting, he wants to get rid of it.

---

### Post by eekie on 2009-11-15
Hello Darkod,
If he wants to get rid of the raid partitions he must install gparted and just delete them. Then in the raid bios he should remove the raid configuration.

---

