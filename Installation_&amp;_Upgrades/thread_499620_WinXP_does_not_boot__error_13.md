---
title: "WinXP does not boot : error 13"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by jgb2185 on 2007-07-12
Hello, folks...

I'm not quite a newbie, but I do find myself out of my league with this one. I just upgraded my Lenovo 3000 c200 laptop's hard drive, and the Windows XP partition will not boot. Here's the short version of what I did:

1) Attached the new 160GB SATA drive in an external USB enclosure to the laptop.
2) Booted an Ubuntu Live CD.
3) Cloned the internal 40GB drive to the external 160GB drive using dd.
4) Shut everything down and swapped the drives.

The laptop now boots Ubuntu Linux (the default) just fine. Trying to boot Windows XP brings the GRUB error "Error 13: Invalid or unsupported executable format".

The research I have done so far suggests that there's something amiss either with GRUB or the Windows partition. I haven't yet figured out what. One odd thing is that fdisk shows /dev/sda1 to be NTFS, but gparted claims it is ext3. 

I am not able to mount the XP partition on the 160GB drive:

```
root@lenovo3000:/media# mount -t auto -o ro /dev/sda1 /media/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

The last messages in dmesg are:

```
[17182687.104000] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[17182687.104000] EXT3-fs: group descriptors corrupted !

```

The next post will be a list of links to the relevant config files, which I'll be uploading to pastebin.com shortly. Any suggestions for repairing this will be very welcome.

jgb

---

### Post by jgb2185 on 2007-07-12
The config files on my laptop:

[LIST]
[*][/etc/fstab]("http://pastebin.com/f78f46959")
[*][/boot/grub/menu.lst]("http://pastebin.com/f78bd9677")
[*][sudo fdisk -l]("http://pastebin.com/f3fca2f7d")
[*][/boot/grub/device.map]("http://pastebin.com/f31afc332")
[/LIST]

jgb

---

### Post by jgb2185 on 2007-07-12
And here is what gparted sees:

**/dev/sda**:
[[IMG]http://img128.imageshack.us/img128/2603/devsdagparteduv0.th.gif[/IMG]](http://img128.imageshack.us/my.php?image=devsdagparteduv0.gif)


**/dev/sdb**:
[[IMG]http://img128.imageshack.us/img128/3570/devsdbgpartedra9.th.gif[/IMG]](http://img128.imageshack.us/my.php?image=devsdbgpartedra9.gif)

---

### Post by jgb2185 on 2007-07-19
I can report that changing the relevant entry in [FONT="Courier New"]menu.lst[/FONT] to use [FONT="Courier New"]rootnoverify[/FONT] has no effect:

```
#
# This entry automatically added by the Debian installer for a non-linux OS
#
# on /dev/sda1
#
title           Microsoft Windows XP Home Edition
[COLOR="Red"]rootnoverify[/COLOR]            (hd0,0)
savedefault
makeactive
chainloader     +1
```

The system still displays '[FONT="Courier New"]Error 13[/FONT]' when attempting to boot from the WinXP partition.

I'm still in the market for a fix. Should I use the Windows [FONT="Courier New"]fixmbr[/FONT] utility on the WinXP partition?

Thanks...

jgb

---

