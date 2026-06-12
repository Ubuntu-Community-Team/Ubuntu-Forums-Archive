---
title: "ntldr missing"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by Furality on 2008-04-05
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8a1cb53f-8252-467d-b784-d5db63f82897 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8a1cb53f-8252-467d-b784-d5db63f82897 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Professional x64 Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



but it says ntldr is missing when i try and boot to windows.

i had to manually install grub because it didn't want to install on it's own.

commands i did were 

#sudo grub
#find /boot/grub/stage1
#      (hd1,3)
#setup (hd0)       /this is my sata drive. same partition as my windows.

but that didn't make grub load....
so i redid the setup command to 
#setup (hd1)       /this is my 80 gig ide drive.

That worked for grub, butlike i said, it says ntldr is broken now.
I think it's trying to find the windows NTLDR on my ide drive
and not the sata drive where my windows partition is. im really confused
on how to make this work. 

Thanks in advance

---

### Post by tubasoldier on 2008-04-05
I don't use Windows anymore so I can't help you much, but these articles may point you in the right direction:

[http://support.microsoft.com/kb/318728](http://support.microsoft.com/kb/318728)
[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

---

### Post by Furality on 2008-04-05
no no, all the files are all there in my c/ directory, so nothing should be wrong with that.

i think grub is looking for ntldr in my ide drive (hd1,0) but it should be in (hd0,0) my primary partition of my 250 gig sata drive. For some reason grub was all messed up over that.

i had to tell grub to look for my linux boot in (hd0,3) instead of (hd1,3) "which doesn't exist"

---

### Post by Furality on 2008-04-05
Also, i told grub to look for my windows partition on (hd0,0) where ntldr should be. but i still am getting errors. and if i look for the files in my first partition i find it right there.

c:\ntldr
so im really frusterated. 

could my commands that i did in the first post write over my MBR?? oh dang

---

