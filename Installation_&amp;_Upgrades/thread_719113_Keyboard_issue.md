---
title: "Keyboard issue"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by yromance on 2008-03-08
Why is my USB Keyboard not working on the Start-up screen the one where it counts down from 30? Because I think it many fix my other problems if I can press F6..It works fine in the Busybox  area a little later on....

---

### Post by yromance on 2008-03-09
Well I guess its back to Winblows its really too bad from what I read this OS should rock,but  if something as basic as a keyboard won't work in ubuntu on my machine, and no sugestions as to why....Maybe I'll try again with the next version 8.04.

---

### Post by yromance on 2008-03-09
Has anyone tried "Super Grub Disk" and do you think it would help my problem??

---

### Post by skippyhacker on 2008-03-09
> **yromance said:**
> Why is my USB Keyboard not working on the Start-up screen the one where it counts down from 30? Because I think it many fix my other problems if I can press F6..It works fine in the Busybox  area a little later on....

I'm seeing the same issue with the latest i386 desktop CD image I just downloaded and burned.  PS2 keyboard exhibits the same behavior.

---

### Post by confused57 on 2008-03-09
> **yromance said:**
> Why is my USB Keyboard not working on the Start-up screen the one where it counts down from 30? Because I think it many fix my other problems if I can press F6..It works fine in the Busybox  area a little later on....
Have you tried going into your bios setup and enabling something like "Legacy USB"?

---

### Post by yromance on 2008-03-09
Thanks confused57 that worked nicely.:KS

So I'm one step closer to ubuntu...

But I'm no where closer to getting around my next error:

(> intramfs) [   97.145689]ata3.00: failed to set xfremode (err_mask=0x40)
(intramfs) [  132.228405]ata3.00: failed to set xfremode (err_mask=0x40)
(intramfs) [  167.311125]ata3.00: failed to set xfremode (err_mask=0x40)
[  197.904761]ata4.00: failed to set xfremode (err_mask=0x40)
[  232.987477]ata4.00: failed to set xfremode (err_mask=0x40)
[  268.070214]ata4.00: failed to set xfremode (err_mask=0x40)

There's alot of posts for it *(lately from me)* but I can't find or figure out the right solution for it(7.10). ](*,)

---

### Post by confused57 on 2008-03-09
> **yromance said:**
> Thanks confused57 that worked nicely.:KS

So I'm one step closer to ubuntu...

But I'm no where closer to getting around my next error:

(

There's alot of posts for it *(lately from me)* but I can't find or figure out the right solution for it(7.10). ](*,)
Even though you're not getting the busybox error, you may want to try some of the suggestions here:
[http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

You could also try press "F6" at the live cd install screen and try adding boot options, for example:
```
irqpoll
all_generic_ide
```

---

### Post by MeduZa on 2008-04-09
u need to activate usb sopourt on system bios. good luck

---

