---
title: "update-grub does not update GRUB"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by rykel on 2011-05-15
After upgrading Maverick (perfect!) to Natty, I was unable to boot into anything. (kernel 2.6.38 )

However, through much PITA, I was able to boot into an older kernel. (2.6.35)

I completely removed 2.6.38, rebooted, reinstalled it and ran update-grub.

However, 2.6.38 is no longer available no matter how many times I run update-grub, and the only option left is 2.6.35.

Please help?

btw, in my humble opinion, the Natty upgrade experience is rubbish. (blank screen, total PC hangs, boots into a blank screen with only a blinking cursor, NVIDIA official driver not working, bootable only into older kernels etc.)

---

### Post by Quackers on 2011-05-15
Graphics-wise Natty is a big upgrade with many changes. It seems many people are finding this.
How did you re-install 2.6.38?

---

### Post by rykel on 2011-05-19
I removed and reinstalled the kernel using Synaptic, that was all.

However, GRUB does NOT update its menu...   :confused:

---

### Post by mhgsys on 2011-05-19
try;
```
sudo update-grub2
```

(debian over here)

---

### Post by Quackers on 2011-05-19
Did you install all the packages in synaptic for the newer kernel? I believe there are 3.

---

### Post by rykel on 2011-05-19
No luck with update-grub2 either...

[INDENT][B]$ sudo update-grub2
[sudo] password for aen: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.32-30-generic
Found initrd image: /boot/initrd.img-2.6.32-30-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
[/B][/INDENT]

I enabled Natty-Proposed in repository and then have Update Manager upgraded to kernel 2.6.38-9-generic.

Not sure what else I have to do.

btw, Natty really fails compared to Maverick!

---

### Post by rykel on 2011-05-22
Hi, I just removed 2.6.35, made sure that ubuntu-desktop is completely purged and reinstalled, and GRUB no longer display ANY kernel. That is, no more Linux for me. Please help!

---

### Post by meliniak on 2011-07-19
In case you are still struggling with this problem, here is the solution i found useful:

[http://ubuntuforums.org/showpost.php?p=11060719&postcount=2](http://ubuntuforums.org/showpost.php?p=11060719&postcount=2)

---

