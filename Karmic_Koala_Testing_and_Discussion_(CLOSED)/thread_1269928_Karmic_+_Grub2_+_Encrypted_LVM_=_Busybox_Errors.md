---
title: "Karmic + Grub2 + Encrypted LVM = Busybox Errors"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Arabica Bean on 2009-09-18
Hi all. I stupidly upgraded my production machine from Jaunty to Karmic A5, and I rebooted, to which I was greeted by busybox (imitramfs).  Here is the output....

```

(initramfs) Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modues (cat /proc/modules; ls dev)
ALERT! /dev/mapper/advent-root does not exist. Dropping to a shell!

BusyBox v1.13.3 (...............)

(initramfs)

```
I have an encrypted LVM system, so I can't salvage precious files. 

```
(initramfs)cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-2.6.31-10-generic root=/dev/mapper/advent-root ro quiet splash
```

The biggest problem for me is that I can't even get to the grub menu as it cannot mount the boot partition (I think), so that I can run a recovery shell on it. I am not very familiar with Busybox, so any help here is greatly appreciated.

:)

---

### Post by mojorising on 2009-09-20
Hi. I had the same problem. 

Maybe this will be helpful to you: [http://ubuntuforums.org/showthread.php?p=7966235#post7966235](http://ubuntuforums.org/showthread.php?p=7966235#post7966235)

Following those instructions with some minor modifications will hopefully get you to a point where you can mount your encrypted drive and copy your data to removable or network storage. 

In that thread is also a "chroot" solution you may be able to follow to make your current OS functional again -- I couldn't do so because fsck ruined my filesystem (apparently it doesn't work so well on ext4). I had to run fsck.ext4 and then rebuild my journal with tune2fs -j in order to read the contents of my filesystem. 

Of course, it can't be said enough; always back-up your important data. 

Good luck!


Mike

---

### Post by QBX on 2009-09-23
Hi, joining the club here ... I also unwisely installed Karmic over my working stable Jaunty on encrypted LVM.

I was able to mount the encrypted filesystem booting from live CD and following the instructions from Peanut Butter (thanks!) on [http://ubuntuforums.org/showthread.php?t=611165](http://ubuntuforums.org/showthread.php?t=611165) - but now my question is - how do I handle it so the updated version of cryptsetup is on my hard drive installed or what do I need to do for grub to be able to mount my encrypted file system?

Best,

QBX

---

### Post by mojorising on 2009-09-25
QBX, have you looked at this thread: [http://ubuntuforums.org/showthread.php?t=1267657](http://ubuntuforums.org/showthread.php?t=1267657) ?    It may get you going. Of course, you have to unlock and mount your LVM volumes before doing the solution proposed. I actually just put the few files I wanted on a USB drive and then re-installed fresh because my filesystem was cooked. 


Mike

---

### Post by Psycho Game on 2009-09-25
I wouldn't recommend using Encrypted Home, LVM or Swap at all at the moment.
According to some benchmarks at phoronix.com this results in performance loss.
So if you have to reinstall your system reconsider if you want the encryption or the performance.

Greetz,
Psycho Game

---

### Post by mojorising on 2009-09-25
The impact on the performance actually is quite small on modern machines. I suspect most users would not notice a difference at all -- I certainly don't.

If I remember correctly, the Phoronix articles still recommended using encryption on netbooks/laptops despite the small performance loss. Regardless of what the article says, my system (Intel Dual Core Pentium with 1.5 GB RAM -- nothing special) is quite quick on encrypted LVM, running KDE 4.3 with compositing enabled. In fact my machine now runs faster than ever with the recent Ubuntu, KDE, and Intel video driver  performance improvements. 

Again, I can't even tell a difference, myself, between using LUKS and not doing so. 


Mike

---

