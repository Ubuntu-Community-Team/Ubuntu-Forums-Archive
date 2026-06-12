---
title: "Can't install grub on floppy"
date: 2005-08-20
forum: Installation &amp; Upgrades
---

### Post by Gesu` on 2005-08-20
Hi all!
I'm unable to install grub on floppy.

This is what I get with **grub-install**:
```

root@Phoenix:/etc # grub-install '(fd0)'


    GNU GRUB  version 0.95  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word,
   TAB lists possible command completions.  Anywhere else TAB lists
   the possible completions of a device/filename. ]

grub> root (hd0,5)
 Filesystem type is ext2fs, partition type 0x83
grub> setup  --stage2=/boot/grub/stage2 --prefix=/boot/grub (fd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (fd0)"... failed (this is not 
  fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is 
  not fatal)
 Running "install --stage2=/boot/grub/stage2 /boot/grub/stage1 d (fd0) 
/boot/grub/stage2 p /boot/grub/menu.lst "... failed

Error 21: Selected disk does not exist
grub> quit

```
And if I use **grub-floppy**:
```

root@Phoenix:/home/petrax # grub-floppy '(fd0)'

Can't find /lib/grub/i386-pc
/lib/grub/x86_64-pc/stage1, aborting 

```

(And my system is a 32bit one, an old PIII450)

I used also the procedure described [here]("http://ubuntuforums.org/showthread.php?t=6195"), but with no luck. At startup system reads the floppy but then it uses the grub installed on MBR, and I can't understand why.

Suggestions?

TIA


PS: I cant' login this forum using Opera :(

---

