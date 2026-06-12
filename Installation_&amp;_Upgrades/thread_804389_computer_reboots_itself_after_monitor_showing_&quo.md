---
title: "computer reboots itself after monitor showing &quot;no signal&quot;"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by realbuntu on 2008-05-23
I completed installation of ubuntu desktop.  It rebooted, after loading bios, the screen says 'no signal', a few seconds later it reboots itself again and this repeats untill I turn off the computer.

What can I do to get the system to start?

Feedback is appreciated. 
Thank you!

---

### Post by PmDematagoda on 2008-05-23
Do you manage to reach the GRUB menu before the PC restarts?

---

### Post by kellemes on 2008-05-23
> **realbuntu said:**
> I completed installation of ubuntu desktop.  It rebooted, after loading bios, the screen says 'no signal', a few seconds later it reboots itself again and this repeats untill I turn off the computer.

What can I do to get the system to start?

Feedback is appreciated. 
Thank you!

This is assuming you do see your bootloader (Grub)..
Boot to singe/safe-mode and try to reconfigure your X-setup like so..
```
dpkg-reconfigre xserver-xorg
```

---

### Post by realbuntu on 2008-05-24
No I was not able to reach the GRUB.  Another kind forum member suggested this.

Can you reach the BIOS settings? (should be one of the F1, F2, ..., F(n) keys)
If so, change to boot from CD, dowload and burn the Super Grub Disc and boot the computer with the disc in the tray. That should restore your system.

Trying it soon.

---

### Post by realbuntu on 2008-05-24
It can boot up using the Super GRUB. I choose auto fix. Even it said success, then I remove the CD, rebooted. Same problem occured. So I try the advance option, got to the part where it says "Partition to Boot"

The screen came to the following:

Booting '1 hda1 sda1 (hd0,0) hd0s1 ext2fs Ubuntu 8.04 \n \l'

set out_device=(hd0,0)
set out_hurd_hd-hd0
.
.
.

Error 30: Invalid arguement 

Any advice is appreciated!

---

### Post by realbuntu on 2008-05-24
Here is some thing I found, again I have no idea where to go from here. 

Booting command-list

findf /grub/stage1 /boot/grub/stage1
root (hd1,0)
Filesystem type is ext2fs, partition type 0x83
setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes 
Running "ebmed /boot/grub/e2fs_stage1_5 (hd0)"... failed (this is not fatal)
Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
Running "install /boot/grub/stage1 d (hd0) /boot/grub/stage2 p /boot/grub/menu.lst " ... failed

Error 17: Cannnot mount selected partition

---

### Post by realbuntu on 2008-05-24
[http://ubuntuforums.org/showthread.php?p=5032846#post5032846](http://ubuntuforums.org/showthread.php?p=5032846#post5032846)

More discussion is here at this thread. 
Im still working on this!

---

