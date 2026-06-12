---
title: "Dual boot vanished after trial to repair Windows"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by umeboshi80 on 2011-03-08
Hi,

I initially had a dual boot where I could decide to either boot into Windows 7 or Ubuntu 10.04. It work seamlessly. At some point, however, when I booted into Windows, it just
seem to only load it "half" in the sense that the desktop just turned black (but when ctrl-alt-del was hit I did receive a screen with the different options). 

I suspected there was a problem with grub and proceeded to restore the Windows bootloader by booting into the Windows CD and repairing the computer by entering
the commands:
bootrec.exe /fixboot
and
bootrec.exe/fixmbr

After restarting I suddenly do not have the option to boot into Ubuntu (where did it go?) and booting automatically into Windows the original problem persists.

Any idea what happened here and how I can restore things?
Thanks a  lot!

---

### Post by Grenage on 2011-03-08
By fixing the Windows MBR, you overwrote Grub2, which is why you have no dual-boot menu.

The easiest solution would be to boot from a live CD (ubuntu CD will do), and reinstall grub2; I believe it would be:
```

sudo grub-install /dev/sda
```

Where /dev/sda is your primary boot drive/first hard drive.  There are many guides in Google for reinstalling Grub2, if not.

---

### Post by umeboshi80 on 2011-03-08
Hi,

Thanks for the quick answer. Indeed reinstalling Grub2 solved the issue. Windows, however, is still not fixed. How can I fix it without destroying the Grub or possibly
even overriding Ubuntu?

Thanks a lot for any hints.

---

### Post by Grenage on 2011-03-08
Don't worry too much about the boot record getting overwritten, you know now that it has an easy fix.  While I have limited experience with Windows 7 problem solving (it never goes wrong at home), have you tried 'rolling back' to a period where it did work?

The presence of Grub, and the Windows 7 problems are almost certainly not linked.

---

### Post by garvinrick4 on 2011-03-08
Once you installed grub2 and was success then run in Ubuntu terminal
```
sudo update-grub
```
so as to get os-prober in grub to go out and search for other Operating System to put
in grub-config and as a menu entry.
* Below is a few links for grub problems of different varities:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099") 
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

---

### Post by Mark Phelps on 2011-03-08
> **umeboshi80 said:**
> Hi,

Thanks for the quick answer. Indeed reinstalling Grub2 solved the issue. Windows, however, is still not fixed. How can I fix it without destroying the Grub or possibly
even overriding Ubuntu?.

What do you mean by "not fixed"? 

In your other post, you left us with the impression that after you did the repairs, Win7 booted OK.  You were only left with having to redo the GRUB stuff to get back access to Ubuntu.

---

