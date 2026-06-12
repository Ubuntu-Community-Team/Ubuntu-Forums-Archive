---
title: "Grub Difficult issues"
date: 2006-03-03
forum: Installation &amp; Upgrades
---

### Post by VanillaEyeSky on 2006-03-03
:-k I installed the ubuntu 10.4 on the SATA HD along with the XP, installed the GRUB to the MBR, everything was peachy, rebooted and the grubloader works. Great. Then if you do few reboots, and the grubloader disappears and goes straight to XP, I reinstalled the ubuntu, and such, same problem popped up again on several reboots.

So, I tried the live CD and went into the grub menu and saw that the grub was set up right as i read it.

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
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
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


Any advice? I am thinking that I should change the HD to SD? since the hard drive is SATA drive.. not IDE. :-k

---

### Post by R3linquish3r on 2006-03-03
U have windows set in there twice? Apparently the windows MBR overwrote the GRUB one which is why Windows is majoring in the boot. Try deleting that second Windows line. If that don't work you'll probably have to re-install GRUB.

---

### Post by VanillaEyeSky on 2006-03-03
Apparently i looked at the partition which only showed one partition of XP, I will try to delete the 2nd line of xp.. and reinstall grub and see.. At the first time i did this, it did not show the 2nd line before until i reinstalled grub and such. Hm. let me report back to you on that

---

### Post by VanillaEyeSky on 2006-03-03
Okay, i tried it, and still has trouble with the GRUB. Apparently some reason it recongized two XP even tho theres only one XP..?:confused: 

any help? and i cant install grub into it from live cd tho. 

I am frustrated at the moment.. :-k

The HD was formatted clean and installed XP, and then installed Linux.. so, I am not sure what to do about the grub problem?

---

