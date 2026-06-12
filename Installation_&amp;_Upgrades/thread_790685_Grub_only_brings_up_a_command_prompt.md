---
title: "Grub only brings up a command prompt"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by plr4ever on 2008-05-11
I've been trying lately to get a multi-boot running, and I've gotten windows installed on an 80GB hard disk, and my Linux setup is running on a 160 GB disk. For a while i was able to boot to Ubuntu by unplugging the windows drive until i could figure out how to get grub to recognize windows.

Anyway, now when i boot to Linux, i get a grub prompt, and i cannot figure out how to boot from that. my /boot is a separate partition, along with Ubuntu and opensuse partitions and a separate home. both distros share the same /home and /boot, but grub still wont boot.

When i attempt to use the command "kernel " followed by "boot", i get a kernel panic on the boot saying something about file system not synced. I am honestly at a loss as to how to boot either distro. Windows is beginning to get to me again!

Does anyone have ANY ideas. I'm willing to try everything, as i DO NOT want to wipe that disk AGAIN.

---

### Post by RATM_Owns on 2008-05-11
Try typing "startx" without the quotes.

If that doesn't work, I guess just reinstall Ubuntu on the partition.

---

### Post by plr4ever on 2008-05-11
> **RATM_Owns said:**
> Try typing "startx" without the quotes.

If that doesn't work, I guess just reinstall Ubuntu on the partition.

startx won't work without an OS loaded. Right now all that loads is the "grub>" prompt, meaning i can use one of about 30 commands. At this point the kernel will not even boot. 

I've also tried this to no avail:
```
setup (hd0,0)
root (hd0)
```

edit: the problem isn't with ubuntu itself, it is with GRUB.

---

### Post by ajgreeny on 2008-05-11
With both hard disks attached and wired up, run the live Ubuntu CD and show us the output of ```
sudo fdisk -l
```  This will show where your OSs are installed and it may then be possible to tell you what to edit your /boot/grub/menu.lst file to show.  What version of Ubuntu have you installed?  This will be needed in order to make sure the kernel version listed in that is correct

---

### Post by plr4ever on 2008-05-11
I've also posted this to [linuxforums.org]("http://www.linuxforums.org/forum/installation/121424-grub-brings-up-command-prompt.html#post586441") with the same information if you would rather go there.


fdisk -l:
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00096b18

Device Boot Start End Blocks Id System
/dev/sda1 * 1 131 1052226 83 Linux
/dev/sda2 132 8023 63392490 5 Extended
/dev/sda3 9259 19457 81923467+ 83 Linux
/dev/sda5 132 2043 15358108+ 83 Linux
/dev/sda6 2044 3955 15358108+ 83 Linux
/dev/sda7 3956 5867 15358108+ 83 Linux
/dev/sda8 5868 7780 15366141 83 Linux
/dev/sda9 7781 8023 1951866 82 Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b8a3b

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 4844 38909398+ 7 HPFS/NTFS



Anyway here is my partition translation:
sda1 -> /boot
sda2 - logical containing sda5-8
sda3 - /home
sda5 - ubuntu /
sda 6-7 - empty
sda8 - opensuse /

I've noticed that grub no longer boots to stage 1.5 like it used to, but boots to stage 2. im not quite sure of the exact difference, but i am sure that this is the root(hehe) of the problem.

Also, there is no /boot/grub directory under sda5, or a menu.lst under my /boot directory. I'm not quite sure where it went, but it was there not to long ago.

should i consider reinstalling grub?

---

### Post by ajgreeny on 2008-05-12
Before doing that let's see your /boot/grub/menu.lst.  I am assuming that you use grub from Ubuntu, not Suse, but whichever it is, you will need to check what the grub menu points to at the moment.
OK I've just noticed that you have no menu.lst as far as you know anywhere on the system; strange, but that is obviously where your problems stem from.  Reinstalling grub using the normal Live CD method will not work as far as I can see because you don't seem to have a menu.lst for grub to work from.  Can't help any more, I'm afraid.

---

