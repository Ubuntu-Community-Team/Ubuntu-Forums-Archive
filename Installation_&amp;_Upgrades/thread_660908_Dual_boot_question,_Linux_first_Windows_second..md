---
title: "Dual boot question, Linux first Windows second."
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by tylerdurden15 on 2008-01-07
I already have Linux installed and want to install Vista on my machine for a dual boot.  My hard drive is already partitioned, am I gonna have a problem putting vista on second?  Someone already said i will not be able to boot Linux any more if i do it that way, if so what would be the fix for this? 

Thanks in advance!

---

### Post by codesplice on 2008-01-07
You should be fine.  Installing Windows will boot directly to Vista's BCD bootloader (bypassing your GRUB), but you can use EasyBCD ( [http://www.neosmart.net](http://www.neosmart.net) ) to configure BCD to boot your Linux installation.

Alternatively, after installing Vista, use a Linux LiveCD to reinstall GRUB:

```

sudo grub

>root (hd0,0)
>setup (hd0)
>quit

sudo reboot
```

Should do it, assuming your Linux install is on the first partition of your first harddrive.

---

### Post by tylerdurden15 on 2008-01-07
New Problem now i am getting this message from the vista install:

Windows could not assign a drive letter to a partition on disk 0. The error occured while preparing the computers system volume. Error code 0x80004005.

---

### Post by codesplice on 2008-01-07
How is the drive partitioned?  You have your Linux partitions (/swap and /).... then do you have a Vista partition or just free space after those Linux partitions?

---

### Post by tylerdurden15 on 2008-01-07
Just free space its not allocated to anything

---

### Post by codesplice on 2008-01-07
Hmm.... at which point in the installation do you get that error?

---

### Post by tylerdurden15 on 2008-01-07
right in the begining, probably the second prompt when it was asking where do i want to install it.  Linux was on the first partion and next to it said primary, next was nothing were i wanted to install vista, and a small 3rd that said logic or something next to it. number 1,2,3 in the order i said

---

### Post by codesplice on 2008-01-07
Hmm.  I'm not familiar enough (yet) with Vista's installation to really be able to provide much more input.  Hopefully someone else can chime in :)

---

### Post by APVangeliLMS on 2008-01-07
on  my laptop, i can press f2 during boot and choose my operating system, i dont know yet if linux will show, i just found ubunto. :)

---

### Post by tylerdurden15 on 2008-01-07
thanks apv but my problem right now is actually getting Vista to install, but thanks for the tip

---

