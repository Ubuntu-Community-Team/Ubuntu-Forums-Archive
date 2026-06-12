---
title: "SuperGrub says &quot;no&quot;"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Gregory@Feanor on 2008-04-26
I was installing Xubuntu using uNetBootin because my laptop doesn't have an optical drive and making a bootable USB Pen Drive seemed like a hassle. I'd run the program, restarted and selected uNetBootin from the windows bootup screen. While xubuntu was installing it froze. I restarted and now all I get after the BIOS is a flashing underscore.

After a suitable amount of panicking I installed SuperGrub on a USB Pen Drive. I can boot into the windows partition using SuperGrub and I have been trying to fix the Windows bootloader. When I select that option it says there is a disk error, and then afterwards the USB Pen Drive (containing SuperGrub) no longer works. What I think is happening is SuperGrub has a go at hd0 (which is the USB Pen Drive) and not hd1 (the laptop's hardrive containing the windows partition) when trying to fix the windows boot loader (I think this because there are loads of "hd0" on the screen but no "hd1").

How can I fix the windows bootloader? Is there a way to tell SuperGrub to focus on hd1 and not hd0? Is there another way to fix the bootloader? Is the bootloader even the problem? Could it be the Master Boot Record?

---

### Post by obidose on 2008-04-26
Which version of windows?

EasyBCD worked magic for me to fix my vista bootloader.

---

### Post by Gregory@Feanor on 2008-04-26
It's Windows XP. Can you fix the windows bootloader within windows?

---

### Post by obidose on 2008-04-26
I think you can use the installation cd/recovery console

commands fixmbr
fixboot might work too

Would not sort the Xubuntu out though, only the boot into windows.

---

### Post by Gregory@Feanor on 2008-04-26
>I think you can use the installation cd/recovery console

Which installation cd/recovery console? Are those commands for SuperGrub? I don't have a CD player so I can't use any LiveCD. And I tried for ages to make a bootable xubuntu USB Pen Drive with no success.

Cheers

---

### Post by obidose on 2008-04-26
The are for windows recovery console. Usually got at by using the windows cd. There is probably a program which can do what you need to fix the boot but I am unaware of it.

Is it possible for you to use supergrub to boot into recovery console?

---

