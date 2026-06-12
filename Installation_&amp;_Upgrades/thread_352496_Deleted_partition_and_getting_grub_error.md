---
title: "Deleted partition and getting grub error"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by Notclive on 2007-02-03
I've deleted my old windows partition which was hda1 to make more room for my ubuntu partition which was hda2 and is now hda1. I had grub as a bootloader after deleting the partition I didn't get the grub splash screen and get error 22. I think the problem is grub is trying to find /boot/ on hda2 which doesn't exist. I'm currently using the live cd and have read lots of forums but nothing works.

---

### Post by Theimon on 2007-02-03
Have you tried reinstalling Grub?

---

### Post by Notclive on 2007-02-03
I tried
$ grub-install /dev/hda1
and got:
Could not find device for /boot: Not found or not a block device.

Is that what you mean by reinstall?

---

### Post by Theimon on 2007-02-03
Yes, that's what I meant.

Check [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html) and especially section 3.2. Maybe that will help you get Grub to point to the right device.

---

### Post by Notclive on 2007-02-03
I tried root (0,0) which I thought would be hda1 and got "Error 22: No such partition", then I tried root (0,1) and I got no error so I assume thats pointing to hda1, I then did setup (hd0) and got " Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found"
But I'm sure that file exists in /boot/grub/stage1

---

### Post by rsambuca on 2007-02-03
In a terminal type:  sudo grub (from the liveCD)
the grub will open and you will see: grub>
enter: find /boot/grub/stage1

let us know what it says.

---

### Post by Notclive on 2007-02-03
I've fixed it, I wasn't running grub with sudo before but when I saw your post I relized what I'd done wrong. Thanks.

---

### Post by Theimon on 2007-02-03
Happens to the best of us :)

---

### Post by rsambuca on 2007-02-03
Only reason I knew was because I have done the same thing myself.  Guess it happens to the worst of us too - me!

---

