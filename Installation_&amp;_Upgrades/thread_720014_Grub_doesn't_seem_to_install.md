---
title: "Grub doesn't seem to install"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by Alarindris on 2008-03-09
My partition setup:

sda1 ntfs

hdb1 ntfs
hdb2 ext3
hdb3 swap

sda1 is my monster drive with all my media etc on it.
hdb1 is WinXP
hdb2&3 I partitioned long ago so I could eventually install linux.

The problem is, after I install from the live CD, I'm getting the same bootloader (MS) as I had pre-install.  Do I need to wipe it all and install Ubuntu first?  Or am I missing something in the partioning process?

Any help appreciated,

Alar

---

### Post by Pumalite on 2008-03-09
In step 8, use advanced tab and replace (hd0) for /dev/hdb1

---

### Post by Alarindris on 2008-03-09
Aha!  Missed that tab, I was actually a little concerned that I wouldn't have the option.

Thanks,

Alar

---

### Post by Pumalite on 2008-03-09
Or reinstall Grub to your Windows MBR 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by st0n3cutt3r on 2008-03-09
there are many guides available online (too many steps to copy here, and I am lazy, sorry), but here's one that I found that you should be able to follow to get your system working that expects a pre-existing XP install on the same hard drive that you're going to install Ubuntu to.   Sound right?

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html")

---

### Post by Alarindris on 2008-03-09
> **st0n3cutt3r said:**
> 
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html")

That's dead on, thanks for the link.

---

### Post by Alarindris on 2008-03-09
All your suggestions seemed like they'd work, and I thank you but I tried installing grub to hd0 and hd1, no luck yet.  Shouldn't it overwrite the MS bootloader?

Edit: I tried [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) and

"In step 8, use advanced tab and replace (hd0) for /dev/hdb1"

and no luck.

---

### Post by Alarindris on 2008-03-09
sudo grub
root(hd0,5) /* In my case */
setup(hd1)

Is that what I should be going for?

---

### Post by logos34 on 2008-03-09
> **Alarindris said:**
> sudo grub
root(hd0,5) /* In my case */
setup(hd1)

Is that what I should be going for?

No.  Your boot drive is hdb, and you say root is the second partition, so you want:

[B]root (hd0,1)
setup (hd0)[/B]

But it may not work given your previous troubles.  Something is preventing it from overwriting the windows bootloader.  

If it works, can you boot into windows via the grub entry? You may have another problem there.

---

