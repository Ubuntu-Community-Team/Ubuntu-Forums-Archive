---
title: "Dual boot woes - unusual setup anyway"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by richrock on 2007-11-22
This is an unusual situation IMHO.  I've run Ubuntu before, but a mad decision during a PC upgrade meant I returned to Windows XP Pro for about 6months.  Now I'm back, but I still use XP primarily for gaming.  I love using Ubuntu and Linux apps for everything else, so thats the way I want it.

My system is setup thus:
1 160gb SATA drive, Windows XP Pro
1 80gb SATA drive NTFS, used as a media drive (accessible by both Windows and Ubuntu)
1 120gb IDE drive, with Ubuntu 7.10 installed.

Now, I already had Windows XP installed, I installed Ubuntu on to the new drive, and Grub recognised the Windows XP install.  BUT... :(

I cannot boot Windows from the Grub menu.  It always comes up with NTLDR is missing.  Yet when I switch the hard drive on the BIOS, I can run XP fine.

I checked the Grub manual (no help there), searched a bit, but now it comes to this... FWIW, here's the relevant section of the menu.lst:

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=0ba9f0b6-82f8-4f09-93fe-89328a1e9662 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=0ba9f0b6-82f8-4f09-93fe-89328a1e9662 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title           Microsoft Windows XP Professional
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1
```

Any ideas how I can get Grub to talk to XP and let it boot?

---

### Post by davebridges on 2007-11-22
i have had a similar problem, and have been trying to work it out for a while too.  i tried a format/reinstall of the windows xp and that seems to be working (i tried it briefly before work this morning).  if you need to recover files from xp before doing this, there is a good usb/floppy/cd fix to bypass the ntldr is missing here:

ntldrismissing.com

let us know if you find anything.  ill repost once i can test my setup again

---

### Post by louieb on 2007-11-22
Since you can boot XP by switching drives in BIOS my guess is you need to play with the **map  (hd#) (hd#) **statements. The purpose of them is to make XP think its on the 1st hard drive in the boot order. The other thing you need to look at and maybe play with is /boot/grub/device/map
The Dual Boot link in signature has some more info. also this thread has some fixes for dual booting sata / ide drive mixes.  [Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by Posterus on 2007-11-22
There also might be an error in the way you set up the dual boot...did you overwrite the MBR??? cuz that's not a good thing :P

---

### Post by richrock on 2007-11-22
Actually, I came back to say it was solved - the install had mapped to hd2,0 yet I changed this to hd1,0 (and 0,1, etc) and it works!  Now, on to f-spot (which loads, dies, and my hdd goes mental - but that's another thread) thanks!

---

### Post by White-Wolf52 on 2007-11-28
hi, im having a simaliar problem as the guy who started this post except that i cant start ubuntu, grub shows it as(says something along the lines of for the ubuntu startup) unrecognized install(but more wordy and all, the jist of it being it does not recognize ubuntu).
when i choose it, nothing happens. i think it may be because windows is not on the first partion on the harddrive, and im wondering if u happent o know a way that i can make it think it is from the windows side/or if i should just use the live boot/use the partioning program to move the partion, thanks for ur help :D

---

