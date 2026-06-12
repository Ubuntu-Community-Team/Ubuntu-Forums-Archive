---
title: "upgrade: error 18: selected cylinder exceeds maximum supported by bios"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by eric28805 on 2007-10-21
This is an older (800Mhz) computer with a 320gb hd, but it was working just fine before the upgrade (which appeared to go very well).

 Any ideas?

---

### Post by eric28805 on 2007-10-21
I can boot the old kernel, but not the new one.

---

### Post by motio on 2007-10-21
you have to make a boot partition this wail solve the problem
 look in search sumbaby ask the before

---

### Post by bungee_70 on 2008-05-10
I had the same problem and I must say that I have found a very simple way to get rid of the error if it is caused by an upgrade of the kernel. 

The way I understand it is that the new kernel is in a range of the hard disk that is unreachable for the BIOS. This is why some advocate the creation of a /boot partition at the beginning of the disk. However, if you can boot from an earlier kernel, why not simply swap the old and the new kernel on the physical hard disk space?

To do so, copy all kernel data to a temporary place:
```
sudo mkdir /boot2
sudo cp /boot/* /boot2

```
Then remove everything from /boot (except the /grub sub-directory). Be careful to not reboot until the end because you could not anymore.
```
sudo rm /boot/*
```

Then copy back only the most recent kernel file to /boot. This takes the first empty space of the hard disk left by the old kernel files. That's why you can't simply move (mv) the files from one directory to another because it would not physically move the file on the hard disk. Here for example, I copy the recent 2.6.24 kernel to /boot:
```
sudo cp /boot2/*.24*generic /boot
```

You may then copy the other old kernel files back to /boot, but I suspect they would inherit the error 18 code.

You may now try to boot using the latest kernel. If everything goes right, you could remove the temporary folder. Note that we haven't touch the /boot/grub/ folder. If you removed older kernel, it could be a good idea to edit the /boot/grub/menu.lst in consequence to remove the old options.

---

### Post by BLTicklemonster on 2008-07-01
Just decided to see if I could get as much out of the onboard nvidia 6100 as the pci-e 8500 gt, and when I started up, I saw that message and a blinking cursor. Sat and waited a long time to see what would happen, and nothing happened.

Rebooted, and now I don't see grub, but boot straight in to XP.

This can't be good, right?

:)

Heeeeeelp!!!

---

### Post by BLTicklemonster on 2008-07-01
It gets worse: 

I flashed my bios seeing as how there was an update for it, and I love living on the edge anyway... and rebooted, and still no grub, straight to windows.

Well, what the heck, load ubuntu on one of the empty partitions.

No good. After installation, no grub/straight to windows.

I'll have to run YaREG in windows and see if the reiserfs partitions even appear, though I doubt they will because there's no grub, which tells me the ... what? the mbr is dweebed?

Anybody got any ideas where to go to from here?

*Edit:
went home for lunch, went to the bios, set "boot from other device" to disabled, and it booted to grub. I have a Wolking Trooper usb gaming mouse that has it's own software in mouse, and I don't get it, but perhaps the system was seeing this and freaking out?

---

