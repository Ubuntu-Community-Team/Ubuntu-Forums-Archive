---
title: "Boot Trouble"
date: 2012-06-20
forum: Installation &amp; Upgrades
---

### Post by NaOHman on 2012-06-20
For a variety of reasons I decided to reinstall Ubuntu on my Toshiba Satellite P755 today which dual boots with Windows 7 (64 bit). I went into Windows and deleted the Linux partitions and the guide told me that all I needed to do was to reboot with a windows recovery disc and then run a few lines through to command prompt to take control of the boot menu back from grub. However, every time I turn the computer on I get an error message that says

Error no such partition:
grub rescue>_

and I can't boot from the recovery disc or an Ubuntu installation disc. Preferably I would like to run Windows before I reinstalled Ubuntu but if that isn't going to work that's fine. I just want stuff to work again.

---

### Post by darkod on 2012-06-20
That message means you are booting from the hdd first, and is expected after you deleted the ubuntu partitions because the grub2 config files are gone now.

You need to set in BIOS to boot from cd-rom before the hdd, and in that case it should boot your windows disc.

On another note, if you plan to reinstall ubuntu is there a particular reason to boot windows first? You can just continue with the ubuntu install and it will install a working grub2 as part of it. Note that you will still need to boot from the cd-rom first so that it can boot the ubuntu cd too.

---

### Post by NaOHman on 2012-06-20
Thanks. Either booting option should be fine, but the thing is I can't seem to get into the BIOS.

Previously, I would only see the BIOS if I selected Windows as the operating system I wanted to load, otherwise I'd see the grub loader. Now when I restart, I only get the following:

error: no such partition.
grub rescue>

This is the first and only thing I see when I start the computer. I believe the key to enter setup in BIOS for my laptop is F2, but neither this nor any other F[x] key does anything.

Holding shift when starting the computer produces 

GRUB loading.
error: no such partition.
grub rescue>

I think my question now is how do I access the BIOS?

---

### Post by darkod on 2012-06-20
The key to enter BIOS depends on your computer. Usually it's F2, F10, sometimes F12 and Del.

---

### Post by NaOHman on 2012-06-20
OH. Apparently to access the BIOS when booting this laptop, because I had Fast Boot enabled, you need to hold F2 BEFORE turning the power on.

So, I have accessed the BIOS and changed the settings around to be sane. However, when the LiveCD I used to install Ubuntu originally is put in, all I'm getting is a blinking cursor line.

EDIT: This was a boot disc problem. Got Windows back up and running! Thanks so much!

EverythingWentBetterThanExpected.jpeg

---

