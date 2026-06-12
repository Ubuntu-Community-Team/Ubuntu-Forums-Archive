---
title: "Grub problems"
date: 2006-05-26
forum: Installation &amp; Upgrades
---

### Post by OMRebel on 2006-05-26
I'm having a problem getting grub configured correctly.  I have a SATA drive with XP on it, and a IDE with Ubuntu on it.  

My /boot/grub/device.map has the following:
(hd0)	/dev/hdb
(hd1)	/dev/sda

My /boot/grub/menu.lst has:
title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


Previously, the entry for Ubuntu for root was (hd0,0), and I edited that to be (hd1,0), and that would allow Ubuntu to boot.  

How do I get grub configured right to allow me to boot into Windows?  

Thanks.

---

### Post by benblur4 on 2006-05-26
Make sure that the correct hard drive has the boot flag activated.  If the wrong one is flaged to boot then windows won't work.

Also, I'm no pro, but I have edited many grub menu.lst files and I have never seen:
" map (hd0) (hd1)
  map (hd1) (hd0) "
in the windows xp portion.
Maybe try saving a back up menu.lst file and then delete these 2 lines.

---

### Post by Sutekh on 2006-05-26
Again GRUB throws a wobbly.  I have no idea how root (hd1,0) is working for Ubuntu, if the device map says that /dev/hdb1 is hd0.  I would have thought that root (hd0,0) was correct for Ubuntu.

What you could try is going into the GRUB command line, by pressing 'c' at the GRUB menu.  At the GRUB prompt try using the root command and the <TAB> button to help you out.

Try this command from the GRUB prompt
```
cat (hd0,<TAB>
``` and see what filesystems come up.

Then try ```
cat (hd1,<TAB>
``` The output should tell you the type of partitions on the disc.  Can you confirm that (hd0,0) is NTFS (type 0x7 IIRC) and that (hd1,0) is ext2fs (type 0x83)?


As for the **map** commands.  They are used to confuse Windows into believing that it is on the first partition of the first disc.

If Windows *really* is on (hd0,0) then the **map** commands are unneccessary.  If Windows was on (hd1,0) then they would be needed.  

So try commenting or removing the map commands.

---

### Post by confused57 on 2006-05-27
Deleted original reply, I thought Windows root should be (hd1,0)?

---

### Post by Sutekh on 2006-05-27
Yes it should be based on the device map. Thats why i thought it wierd that ubuntu booted from (hd1,0).  Logically Windows should be (hd1,0) and Ubuntu (hd0,0)

Does the GRUB command prompt stuff help out and tell you a bit more about what is where and what GRUB thinks it is?

---

