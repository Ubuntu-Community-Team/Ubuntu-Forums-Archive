---
title: "Vista shows in grub unknown partition type 0x7"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by orb9220 on 2006-09-19
Installed vista in place of my xp and knew it would erase my grub,

So I boot livecD and

sudo grub
find /boot/grub/stage1
grub> find /boot/grub/stage1
 (hd0,1)

grub>root (hd0,1)

Then at this point I don't remember if i setup (hd0,0) or setup (hd0,1)

However now when I try to boot vista it loops back to first entry and boots ubuntu. 

grub> find /boot/grub/stage2 should stage2 be the same as stage1 ?
 (hd0,1)

Grub loader complains vista (hd0,0) is unknow type 0x7 would that cause it to kick back?

I have gone back and fixmbr and then it boots to vista. Then when I try redo the grub I get the loop to first entry.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Any Help if it is something I am doing wrong.

---

### Post by lha on 2006-09-19
When you do "setup (hd0,0)", you install Grub into the boot sector of hda1. As a result. Windows' boot code gets overwritten. So, a "root (hd0,0);
chainloader +1" just reloads Grub. You should install Grub to (hd0), the master boot record.

Another option might be to install Grub into (hd0,1) and then set hda2 as bootable. I can't guarantee that this will work because I don't know if Vista uses similar boot code on mbr as older Windows' do.

---

### Post by orb9220 on 2006-09-19
Tried setup (hd0) still looping to first entry.

 Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1594    12802048    7  HPFS/NTFS
/dev/hda2            1595        3553    15735667+  83  Linux
/dev/hda3            3554        3642      714892+  82  Linux swap / Solaris
/dev/hda4            3643        9964    50781465   83  Linux

---

### Post by confused57 on 2006-09-19
I don't if this link will help or not:

[http://www.ubuntuforums.org/showthread.php?t=207870](http://www.ubuntuforums.org/showthread.php?t=207870)

---

### Post by lha on 2006-09-20
> **orb9220 said:**
> Tried setup (hd0) still looping to first entry.

 Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1594    12802048    7  HPFS/NTFS
/dev/hda2            1595        3553    15735667+  83  Linux
/dev/hda3            3554        3642      714892+  82  Linux swap / Solaris
/dev/hda4            3643        9964    50781465   83  Linux

Did you repair Vista's boot code before installing Grub into MBR?

---

### Post by orb9220 on 2006-09-20
Yes vista disc has a pretty nice one at that. Suprise Surprise!
But I said Ah Hell I don't care about that much because I do Have my real system Ubuntu!

Going to be builing a new mATX system this weekend and redoing everything anyway.

---

