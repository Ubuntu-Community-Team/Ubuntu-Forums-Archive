---
title: "Unique Grub Issue"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by kpurcell on 2006-08-02
I can't find a solution or answer.

I am trying to edit GRUB so that I can boot into either Windows or Ubuntu.  Sounds easy, edit GRUB right.

Well I have Linux on my USB drive.  And when I hit F12 I get my system menu and choose USB and it boots Linux.  When I hit HDD it boots WinXP.

I would like to set up GRUB to show windows XP on my HDD.  My GRUB looks like this:

```

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

You see it thinks my USB drive is hd0.  This works so no big deal.  But what would I enter for my WinXP entry to get it to load the hard drive instead of the USB drive?  My Hard drive is SATA so it is /dev/sda in linux instead of hda.

---

### Post by gva on 2006-08-02
I'm certainly no expert, but in my /boot/grub/menu.lst I have:

title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1

Apparently my Windows sits on /dev/sda2, if it was yours was on /dev/sda1 you would probably want to change the above to (hd0,0).

Hopefully this might work for you?

---

### Post by kpurcell on 2006-08-02
> **gva said:**
> I'm certainly no expert, but in my /boot/grub/menu.lst I have:

title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1

Apparently my Windows sits on /dev/sda2, if it was yours was on /dev/sda1 you would probably want to change the above to (hd0,0).

Hopefully this might work for you?


Thanks but if you read my GRUB above, hda0,0 is the USB disk that has Ubuntu.  It books this way just fine.  I just wanted to add a link to my XP on the internal drive and can't figure out what to add.  Anyone have an idea?

---

### Post by Tomosaur on 2006-08-03
If it finds your USB drive as hd0, then it'll probably be thinking that your REAL hard drive is hd1. If you know the correct partition onto which windows installed, it should be fairly simple. Let's say Windows is on partition 2 of your hard drive, you'd use root (hd1,1) since Grub counts from zero.

---

### Post by kpurcell on 2006-08-04
> **Tomosaur said:**
> If it finds your USB drive as hd0, then it'll probably be thinking that your REAL hard drive is hd1. If you know the correct partition onto which windows installed, it should be fairly simple. Let's say Windows is on partition 2 of your hard drive, you'd use root (hd1,1) since Grub counts from zero.

Thanks for your help.

I added the following to my GRUB menu.list
```

title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1
boot
```

I did this because as you said, it is probably seeing my actual hard drive as hd1 instead of the customary hd0 since it sees the USB drive as hd0.  there is only one partition on the internal hard drive with windows xp.

Problem is when I did this and selected it in the boot up menu it does nothing.  It displays the makeactive and chainloader lines and then freezes.  When I do a boot via the bios boot menu it works.  Did I enter the wrong thing in the menu.lst for Windows XP?

---

