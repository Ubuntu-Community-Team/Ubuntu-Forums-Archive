---
title: "Quick grub menu question."
date: 2005-07-29
forum: Installation &amp; Upgrades
---

### Post by xmastree on 2005-07-29
I've just rebuilt a friend's PC, as it 'went crazy' again. He actually phrased it more strongly than that...
First thing I did was use my ubuntu system to back up his important data, then I wiped his disk clean and started over. I want to show him linux as an alternative, as he always blames Windows viri for his problems.

It's a 40GB disk, so I made it 10GB primary ntfs for XP, 24GB secondary fat32 for data, shared with 6GB for ubuntu.

It all works well so far, but I want to remove some of the entries from the Grub boot menu, to make it look less daunting.

Right now it's:
linux kernel <number>.
linux kernel <number>. recovery mode
memtest
Other systems:
Microsoft Windows XP


I want to remove the memtest and recovery options, and change the names of the remaining ones. I edited /boot/grub/menu.lst but when I run update-grub it resets my changes, apart from the windows one which remained as I had left it.


I just want to give him two simple options, **linux or windows**. I want him to see linux as an easy option (even though it isn't really...)

Can it be done? Or should I try a different boot loader? Bear in mind that the machine isn't online yet, so it should preferably be something already on the installation disc.

---

### Post by Sam on 2005-07-30
Rename some parts (title) and comment others from the grub menu (/boot/grub/menu.lst):

linux kernel <number>. -> Rename as Linux
linux kernel <number>. recovery mode -> Comment
memtest -> Comment
Other systems: -> Comment
Microsoft Windows XP -> Rename as Windows

This should looks like that (this is from my config, yours is different):
```
title           Linux
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/sda1 ro console=tty0 quiet splash
initrd          /boot/initrd.img
savedefault
boot

#title           Ubuntu, kernel 2.6.10-5-amd64-k8 Default (recovery mode)
#root            (hd0,0)
#kernel          /boot/vmlinuz root=/dev/sda1 ro console=tty0 single
#initrd          /boot/initrd.img
#savedefault
#boot

#title           Ubuntu, kernel memtest86+
#root            (hd0,0)
#kernel          /boot/memtest86+.bin
#savedefault
#boot

#title           Other operating systems:
#root

title           Windows
lock
root            (hd0,2)
savedefault
makeactive
chainloader     +1
```

Edit the file manually, and don't run update-grub after.

---

### Post by xmastree on 2005-07-30
[QUOTE=Sam]Edit the file manually, and don't run update-grub after.[/QUOTE]Yeah, got it now. Thanks.

This is the first time I've used grub, I used LILO before, which doesn't respond to changes in the config file unless you run a program to actually tell it to look again.
I thought grub behaved the same way... ](*,)

---

