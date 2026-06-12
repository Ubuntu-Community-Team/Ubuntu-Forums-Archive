---
title: "Grub2 - Dual boot Karmic/Archlinux"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by AgedP on 2010-02-15
After installing karmic with Grub2 I am unable to boot into Archlinux partition. Grub2 has removed the last line of the Archlinux boot stanza! 
It used to read:-
title    ArchLinux on /dev/sda2
root     (hd0,1)
kernel   /boot/vmlinuz26 root=/dev/sda2 ro ga=773
initrd   /boot/kernel26.img         <-- THIS LINE REMOVED BY GRUB 2

Following the Grub2 tutorials I have tried editing /etc/grub.d/40_custom as follows:-

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Arch (on /dev/sda2)" {
set root=(hd0,2)
linux /boot/vmlinuz26 root=/dev/disk/by-uuid/6658acf8-e7b6-43dc-      b7c7-9213909d297c
initrd /boot/kernel26.img
}
  
But no luck.  Only way into Archlinux is to get into the edit shell and manually add the missing line and remove other stuff not needed.

I have spent hours trying to resolve this issue and I am fairly p----d off!    Please tell me that it will be solved in Lucid

---

### Post by zvacet on 2010-02-16
Try with 

```
sudo update-grub
```

or [reinstall grub.]("https://help.ubuntu.com/community/Grub2")

---

### Post by AgedP on 2010-02-16
Thank you zvacet for your suggestion.
I have used update-grub each time I edit 40_custom but it does not complete properly.   Here is the output

elassed@elassed-desktop:~$ sudo update-grub
[sudo] password for elassed:
Generating grub.cfg ...
Found Debian background: Windbuchencom.tga
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Arch on /dev/sda2   <-- THIS ENTRY FAILS
Found Linux Mint 7 Gloria - x64 Edition (7) on /dev/sda6
/etc/grub.d/README: 2: All: not found
/etc/grub.d/README: 4: 00_*:: not found
/etc/grub.d/README: 5: 10_*:: not found
/etc/grub.d/README: 6: Syntax error: "(" unexpected

Can you explain what the last four lines mean?

Here is the part of /boot/grub.cfg parsed by 30_os-prober which relates to ArchLinux - note that the last line is absent - should be
initrd  /boot/kernel26.img

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Arch (on /dev/sda2)" {
        insmod ext2
        set root=(hd0,2)
        search --no-floppy --fs-uuid --set 6658acf8-e7b6-43dc-b7c7-9213909d297c
        linux /boot/vmlinuz26 root=/dev/sda2 ro vga=773
}

I have found that Karmic has become a bit unstable when booting since I have tinkered with Grub.

I have not tried reinstall grub yet.  I will wait to see if you have some helpful advice.  Thank you again.

---

