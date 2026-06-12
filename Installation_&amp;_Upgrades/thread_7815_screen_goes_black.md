---
title: "screen goes black"
date: 2004-12-11
forum: Installation &amp; Upgrades
---

### Post by rejean on 2004-12-11
Hi all!
I have a Penthium II (500Mhz), 256 Mb RAM with 2 hds. On the first I have installed XP then Mandrake 9.0 then Xandros and tried installing Debian/Gnu. On the 2nd hd I have installed Ubuntu. I used Lilo in Xandros and Grub in Ubuntu and Mandrake. I can boot in Xandros and XP but when I boot into Mdk it goes as far as Postfix and then the screen goes black. If I try booting into Ubuntu the kernel gets initiated, the Xandros Lilo fades and the screen goes black.
If I reinstall Ubuntu I get an Error 18 message and I have to flash my BIOS to get out of it.
Could you have a look at my Lilo and Grubs and tell me if you see something wrong?
Lilo:
```
boot=/dev/hda
install=/boot/cboot.b
message=/boot/splash.lilo
timeout=300
map=/boot/map
prompt
fix-table
lba32
read-only
disk=/dev/hda bios=0x80
disk=/dev/hdc bios=0x80
image=/vmlinuz
label=[]s_Desktop_2.0
vga=0xf04
root=/dev/hda8
initrd=/boot/initrd-2.4.22-x1.gz
append="rw acpi=on noagp "
image=/vmlinuz
label=Safe_Video_Mode
vga=0xf04
root=/dev/hda8
initrd=/boot/initrd-2.4.22-x1.gz
append="3 rw acpi=on noagp "
image=/vmlinuz
label={}ure_(Expert)
vga=normal
root=/dev/hda8
initrd=/boot/initrd-2.4.22-x1.gz
append="single rw acpi=on noagp "
```

with the Ubuntu part here:
```

image=/disks/ubuntu/boot/vmlinuz-2.6.8.1-3-386
label=Ubuntu_4.10
vga=normal
root=/dev/hdc1
initrd=/disks/ubuntu/boot/initrd.img-2.6.8.1-3-386
append="root=/dev/hdc1 ro quiet splash"
image=/disks/mandrake/boot/vmlinuz-2.4.19-16mdk
label=mandrake
vga=788
root=/dev/hda6
initrd=/disks/mandrake/boot/initrd-2.4.19-16mdk.img
append="devfs=mount hdd=ide-scsi"
other=/dev/hda3
label=MS_W<>
other=/dev/hda7
label=Linux_on_hda7


```

and here is my Mdk Grub:

```
timeout 10
color black/cyan yellow/cyan
i18n (hd0,4)/grub/messages
keytable (hd0,4)/us.klt
altconfigfile (hd0,4)/grub/menu.once
default 0

title linux
kernel (hd0,4)/vmlinuz root=/dev/hda6 quiet devfs=mount hdd=ide-scsi vga=788
initrd (hd0,4)/initrd.img

title linux-nonfb
kernel (hd0,4)/vmlinuz root=/dev/hda6 devfs=mount hdd=ide-scsi
initrd (hd0,4)/initrd.img

title failsafe
kernel (hd0,4)/vmlinuz root=/dev/hda6 failsafe devfs=nomount hdd=ide-scsi
initrd (hd0,4)/initrd.img

title windows
root (hd0,2)
makeactive
chainloader +1

title windows2
root (hd0,3)
makeactive
chainloader +1

```

By the way why is it that I have 2 Mdk partitions; a Mdk and a Mdk/boot?

and finally my Ubuntu Grub:

## ## End Default Options ##

```
title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hdc1 ro
quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hdc1 ro
single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd1,0)
kernel		/boot/memtest86+.bin
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items
below from the Debian
# ones.
```
title		Other operating systems:
root
```


# This entry automatically added by the Debian
installer for a non-linux OS
# on /dev/hda3
```
title		Windows NT/2000/XP
root		(hd0,2)
savedefault
makeactive
chainloader	+1
```


# This entry automatically added by the Debian
installer for an existing
# linux installation on /dev/hda5.
```
title		[]s_Desktop_2.0 (on /dev/hda5)
root		(hd0,4)
kernel		/vmlinuz root=/dev/hda5 ro rw acpi=on noagp
initrd		/boot/initrd-2.4.22-x1.gz
savedefault
boot
```


# This entry automatically added by the Debian
installer for an existing
# linux installation on /dev/hda5.
```
title		Safe_Video_Mode (on /dev/hda5)
root		(hd0,4)
kernel		/vmlinuz root=/dev/hda5 ro 3 rw acpi=on noagp
initrd		/boot/initrd-2.4.22-x1.gz
savedefault
boot
```


# This entry automatically added by the Debian
installer for an existing
# linux installation on /dev/hda5.
```
title		{}ure_(Expert) (on /dev/hda5)
root		(hd0,4)
kernel		/vmlinuz root=/dev/hda5 ro single rw acpi=on
noagp
initrd		/boot/initrd-2.4.22-x1.gz
savedefault
boot
```

Any suggestion will be greatly appreciated!
Réjean

---

### Post by Rancoras on 2004-12-11
That's a rather complicated setup.  My only question is: You are using both lilo and grub?  I wasn't aware that was possible.  (Side note: If you wrap your lilo and grub text in code tags, it's much easier to read.)

---

### Post by rejean on 2004-12-11
Good news everyone!!!
I just changed the settings for the Mdk vga from "788" to "normal" and I can now boot into Mandrake. All I have to figure out is Ubuntu and see if I can install Debian Gnu/Linux or Suse and I will be a happy pinguin.
The problem is that I have a fairly old machine and a somewhat primitive graphic card (S3 Trio 3D/2X 368). If you have any clue don't hesitate to post it!
Thanks again!
Réjean
P.S. Rancoras what do you mean exactly by code tags? I'll be more than happy to edit my post if you don't mind telling me how to do it. :confused:

---

### Post by Dko on 2004-12-11
Here is some info on tags.  Hope it helps ^^
[http://www.ubuntuforums.org/misc.php?do=bbcode](http://www.ubuntuforums.org/misc.php?do=bbcode)

---

### Post by rejean on 2004-12-11
Thanks Dko!
It looks a lot better this way! \\:D/ 
First time I go on a forum where I have seen it being used! Still, if someone can figure out how to make my Ubuntu work I would appreciate it. It did last week when all I had were XP and Ubuntu.
Thanks again!
Réjean

---

