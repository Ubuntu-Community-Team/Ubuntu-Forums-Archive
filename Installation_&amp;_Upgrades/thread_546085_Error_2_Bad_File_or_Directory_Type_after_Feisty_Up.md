---
title: "Error 2: Bad File or Directory Type after Feisty Upgrade"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by overkillm on 2007-09-08
I recently decided to upgrade from Edgy to Feisty.  I tried the official method, using the Adept upgrade tool.  The process ended with an error and didn't reboot (Unfortunately I've since re-imaged so I don't have the file with the exact verbage of the error message anymore).  

So I tried the method I read elsewhere, changing all instances of "edgy" to "feisty" in my /etc/apt/sources.list, and just doing apt-get update && apt-get upgrade.  That seemed to work a little better (no doom-and-gloom error messages, anyway), but when I next booted my machine, Grub failed to boot Ubuntu and gave the error message:

```

Error 2: Bad file or directory type.

Press any key to continue...

```

I only get this error when I try to boot using any kernel installed after my upgrade attempt.  I've tried it with 2.6.20-15, 2.6.20-16, 2.6.17-12, and 2.6.22-10, all with the same result.  I can boot just dandy with the previous kernels, 2.6.17-10 and 2.6.17-11.  I was even able to boot 2.6.17-12, if I used the backup initrd.img file... at least until I tried re-installing that kernel.

I don't think the kernel files are really "bad" because I can see them all right there in /boot/  and they've been freshly installed (and re-installed in some cases)...  I tried using mkinitramfs to make my own initrd.img for 2.6.20-15 (didn't overwrite the old one).  I went into the grub CLI, and grub didn't complain when I loaded the vmlinuz-2.6.20-15-generic file, but when I tried loading my homemade initrd.img I got:

```

Error 16: Inconsistent filesystem structure

```

Also, I've noticed that while the output of lsb_release -a indicates that I am using Ubuntu 7.04 Feisty, my hard drives are still showing up as /dev/hdxx.  When I boot using the Feisty LiveCD, they're /dev/sdxx, and I've read that one of the changes in Feisty is that even IDE drives appear as sdxx, so I was expecting that change after my upgrade.

I have a sneaking suspicion that these issues are directly related but I'm not sure how exactly, or how I can fix them.  I'm perfectly willing to reimage again and go back to Edgy to try again if I have to.  Maybe that first failed attempt was a fluke.  I'd rather not clean-install from the CD, though, unless I'm sure that's my only option.

Any help would be appreciated.   Please and thank you.    :)

---

### Post by Pumalite on 2007-09-08
I would recommend you backup your data and /home is you have it in a different partition and do a clean install of Feisty.

---

### Post by overkillm on 2007-09-11
I suppose I may have to do that, then.  I was hoping there would be another solution... just doing a clean install seems so Windows-y.  Plus I don't really learn anything from it... but, whatever works, works.  :)

---

