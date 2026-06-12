---
title: "How would I go about removing old bootloaders?"
date: 2005-03-17
forum: Installation &amp; Upgrades
---

### Post by mostwanted on 2005-03-17
I'm really a novice concerning Linux. I've got Mandrake as well as Windows XP installed on my computer, and now I intent to install Ubuntu over my Mandrake partition.

Mandrake already came with an excellent bootloader - does anyone know if that will still be present after I've removed Mandrake? And how can I be sure I don't create some bootloader hell on my machine?

Thanks!

---

### Post by bored2k on 2005-03-17
[QUOTE=mostwanted]I'm really a novice concerning Linux. I've got Mandrake as well as Windows XP installed on my computer, and now I intent to install Ubuntu over my Mandrake partition.

Mandrake already came with an excellent bootloader - does anyone know if that will still be present after I've removed Mandrake? And how can I be sure I don't create some bootloader hell on my machine?

Thanks![/QUOTE]
 It won't . It will recognize mandrake and xp and whatever else you have there. The boot loaders arent made by the distro, they are lilo or grub, just like MDK .

---

### Post by Xian on 2005-03-17
Yeah, when you install Ubuntu it will just set-up the bootloader again. No biggie.

---

### Post by mostwanted on 2005-03-17
Ok, great.

---

### Post by ploosh on 2005-03-17
Another question to this thread.......

I just installed Ubuntu (Hoary install) on an existing dual-boot system. I installed it over the previous WinXP partition. Ubuntu wanted to use Grub as the bootloader, but it failed on the install. It did however present me with Lilo which was already listed because I had been dual-booting with WinXP/Mandrake. Should I replace lilo with grub? And if so, how to do this?

The newb problem.
Ubuntu loads fine (love it), but I'm not presented with a menu to choose to boot into Mandrake, which I had hoped for. I checked the partitions to see how things were listed and it looks like:
```
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031  27862.734  primary   ext3        boot
2      27862.734  38154.375  extended              lba
5      27862.765  37636.655  logical   ext3
6      37636.686  38154.375  logical
``` I then brought up the lilo.conf file and edited it to be (not listing the comments):```
boot=/dev/hda
root=/dev/hda1
install=menu
map=/boot/map
delay=40
vga=normal
default=Linux
image=/vmlinuz
	label=Linux
	read-only
	initrd=/initrd.img
image=/vmlinuz.old
	label=LinuxOLD
	read-only
	optional
	initrd=/initrd.img.old
other=/dev/hda5
	label="Mandrake 10.1"
``` When I then /sbin/lilo I receive a message:
```
Warning: LBA32 addressing assumed
Reading boot sector from /dev/hda
Warning: Kernel & BIOS return differing head/sector geometries for device 0x80
    Kernel: 65535 cylinders, 16 heads, 63 sectors
      BIOS: 1024 cylinders, 255 heads, 63 sectors
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/evms/hda1'
    Name change: '/dev/dm-1' -> '/dev/evms/hda5'
    Name change: '/dev/dm-2' -> '/dev/evms/hda6'
Using MENU secondary loader
Calling map_insert_data

Boot image: /vmlinuz -> boot/vmlinuz-2.6.10-4-386
Mapping RAM disk /initrd.img -> boot/initrd.img-2.6.10-4-386
Added Linux *

Skipping /vmlinuz.old
Boot other: /dev/hda5, loader CHAIN
Fatal: First sector of /dev/hda5 doesn't have a valid boot signature

``` Now there are a bunch of useful Ubuntu comments in the lilo.conf file, but I don't think they'd be causing a problem (although I haven't tested that yet). Any idea of what I am missing or doing incorrectly? Thanks for the help.  :D

---

### Post by bored2k on 2005-03-17
[QUOTE=ploosh]Now there are a bunch of useful Ubuntu comments in the lilo.conf file, but I don't think they'd be causing a problem (although I haven't tested that yet). Any idea of what I am missing or doing incorrectly? Thanks for the help.  :D
[/QUOTE]


 This will work on GRUB [you can reinstall it now safely]
[http://ubuntuguide.org/#addwindowsentrygrubmenu](http://ubuntuguide.org/#addwindowsentrygrubmenu)

Similar values should work .

Lilo
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=294025&highlight=lilo+add+entry](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=294025&highlight=lilo+add+entry)
[http://www.linuxquestions.org/questions/search.php?s=&action=showresults&searchid=3695916&sortby=lastpost&sortorder=descending&perpage=35&pagenumber=2](http://www.linuxquestions.org/questions/search.php?s=&action=showresults&searchid=3695916&sortby=lastpost&sortorder=descending&perpage=35&pagenumber=2)

---

### Post by ploosh on 2005-03-17
>  This will work on GRUB [you can reinstall it now safely]
[http://ubuntuguide.org/#addwindowsentrygrubmenu](http://ubuntuguide.org/#addwindowsentrygrubmenu)

Similar values should work .

Lilo
[http://www.linuxquestions.org/quest...=lilo+add+entry](http://www.linuxquestions.org/quest...=lilo+add+entry)
[http://www.linuxquestions.org/quest...35&pagenumber=2](http://www.linuxquestions.org/quest...35&pagenumber=2) Just trying to understand fully. I guess I really have no reason to assume that Lilo is the current bootloader (although when the Grub install failed it said something about Lilo). So is this something where I have the choice of choosing Grub or Lilo? What is done to tell the system which bootloader to use?

I followed the first link suggestions, but can't seem to access the /boot/grub/menu.lst (no such file/directory). "Grub" is listed, just not menu.lst.

Also checked the lilo spec from the second link (listed at the bottom of the thread) but i'm not sure where the difference are in the way I've edited my own lilo.conf file. Any more detail or ideas? I appreciate the help so far.

---

### Post by ploosh on 2005-03-17
```
grub> root (hd0,0)
 Filesystem type unknown, partition type 0x7
```
Not sure why the filesystem is unknown or how to remedy that. Thoughts?

---

