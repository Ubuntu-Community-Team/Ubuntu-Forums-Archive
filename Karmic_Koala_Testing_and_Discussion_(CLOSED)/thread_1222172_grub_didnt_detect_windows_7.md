---
title: "grub didnt detect windows 7"
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by agel1 on 2009-07-24
i installed a base system with the alternate cd of (karmic alpha 3) and grub didnt detect my windows 7, i did choose to install grub to MBR

then i did try the option to fix grub (i dont remember the exact name) in the safe mode kernel and still no option to for win 7

if somebody know how to fix it let me know

thanks

---

### Post by ghindo on 2009-07-24
This is a [known issue]("http://www.ubuntu.com/testing/karmic/alpha3#Known%20issues").  From [this bug report]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/402795"), it looks like running "sudo update-grub2" may get GRUB to detect Windows.

---

### Post by ELD on 2009-07-24
[http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)

That worked for me.

---

### Post by psyke83 on 2009-07-24
> **ELD said:**
> [http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)

That worked for me.

Most likely unnecessary. A simple "sudo update-grub2" fixes the issue for me as well (although it mislabeled Windows 7RC as Vista).

---

### Post by philcamlin on 2009-07-24
> **psyke83 said:**
> Most likely unnecessary. A simple "sudo update-grub2" fixes the issue for me as well (although it mislabeled Windows 7RC as Vista).

thanks that fixed it for me and now i got the new grub too !

---

### Post by ELD on 2009-07-24
> **psyke83 said:**
> Most likely unnecessary. A simple "sudo update-grub2" fixes the issue for me as well (although it mislabeled Windows 7RC as Vista).

No problem, was just posting what worked for me :)

---

### Post by dino99 on 2009-07-25
Here is my config with both grub-pc & os-prober on each distro:

- jaunty32
- jaunty64
- karmic32

When i add a new kernel, the grub menu is well updated on each
When i remove a kernel in synaptic, the grub menu is well updated on 32 bits releases but not on jaunty64 (the removed kernel is still in grub menu): cant see why.
I've tried "sudo update-grub", "sudo update-initramfs -u" but dont succeed.

---

### Post by ranch hand on 2009-07-25
> **dino99 said:**
> Here is my config with both grub-pc & os-prober on each distro:

- jaunty32
- jaunty64
- karmic32

When i add a new kernel, the grub menu is well updated on each
When i remove a kernel in synaptic, the grub menu is well updated on 32 bits releases but not on jaunty64 (the removed kernel is still in grub menu): cant see why.
I've tried "sudo update-grub", "sudo update-initramfs -u" but dont succeed.
I guess you must have done this after yesterdays update.

I have trouble now too.  I bet it gets fixed fast.

I have several variations of 9.10 installed and updated 2 into this problem.  Won't be doing the others until this gets straight on those 2.

---

### Post by Tsar on 2009-07-25
> **ELD said:**
> [http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/](http://blogs.koolwal.net/2008/12/28/windows-xpvista-dual-boot-does-not-boot-from-grub2-or-grub-pc/)

That worked for me.


Installed Koala late last night
and it would not see Windows xp 

followed the above and now in windows

thank you 

so it worked for and found windows first time

---

### Post by agel1 on 2009-07-25
> **ghindo said:**
> This is a [known issue]("http://www.ubuntu.com/testing/karmic/alpha3#Known%20issues").  From [this bug report]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/402795"), it looks like running "sudo update-grub2" may get GRUB to detect Windows.thanks, didnt fix it, im gonna wait for the next alpha.

---

### Post by tad1073 on 2009-07-25
[http://ubuntuforums.org/showpost.php?p=7678673&postcount=7](http://ubuntuforums.org/showpost.php?p=7678673&postcount=7)

---

### Post by Muhammad Ahmed on 2009-09-12
than x a lot worked for me

---

