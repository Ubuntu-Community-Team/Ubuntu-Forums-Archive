---
title: "[SOLVED] Lost boot progress bar"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by jonofan on 2008-11-09
After upgrading to 8.10 through update manager, I had to play around with some things to get my boot speed back. Details here:
[http://ubuntuforums.org/showthread.php?p=6142036#post6142036](http://ubuntuforums.org/showthread.php?p=6142036#post6142036)

Basically I rebuilt the swap partition and boot image to get around a kinit issue.

This has removed my boot progress bar (not a huge issue I know) but I'd like to know how to get it back.

Any help would be greatly appreciated.

Jono

---

### Post by anystupidname on 2008-11-09
I suspect what you're talking about is usplash. Make sure the usplash package is installed and check the kernel line in your /boot/grub/menu.lst
It should have "quiet splash" at the end of it...

---

### Post by walawa on 2008-11-10
I also have this problem. I've checked my menu.lst file but I'm not sure which is the kernel line as many are entitled so. But I did see one with "quiet splash" at the end though.

I'd like to note that the splash screen isn't entirely absent. It appears at first when it's preparing to boot (small line going from one end of the bar to the other). It is replaced by text when the boot actually starts (when the line would usually start growing towards the end of the bar).

---

### Post by jonofan on 2008-11-10
I have usplash package at its latest version, and quiet splash is on the end of my kernal line.
```

title           Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=1b1038fa-9ac5-4ddf-b892-372f73c8243f ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
quiet
```

---

### Post by caljohnsmith on 2008-11-10
I think this thread might help you get your splash back:

[http://ubuntuforums.org/showthread.php?t=828578](http://ubuntuforums.org/showthread.php?t=828578)

Basically any time you resize your swap partition or something of that sort, its UUID changes, and you have to update some files. Not having the splash screen is just one of the strange symptoms. Anyway, let me know if that helps. :)

---

### Post by walawa on 2008-11-10
Thanks a lot! That worked for me. No issues with booting anymore.

---

### Post by jonofan on 2008-11-10
Same here, good job!

---

