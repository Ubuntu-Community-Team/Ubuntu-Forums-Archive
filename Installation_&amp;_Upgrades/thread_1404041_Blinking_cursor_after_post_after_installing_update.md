---
title: "Blinking cursor after post after installing updates on Karmic"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by ninek on 2010-02-11
I recently ran the update manager on Karmic and rebooted. Now, after post, I'm taken to a black screen with a blinking cursor (no text). On this screen, the only thing I seem to be able to do is ctrl-alt-delete to reboot.

I grabbed a 9.10 LiveCD and this boots fine, and I can browse my boot drive.
I also tried to boot with SGD. It's able to read my grub settings and list the various kernels I have the option of booting from, but all of them hang on the blinking cursor (except for the most recent kernel, which immediately reboots my system). Even memtest86+ fails to load off my boot drive when run through SGD.
I also tried reinstalling the MBR with SGD, it got to the step where it said something like "install embed ..." and hung.

I'm not sure what to try any more. Guidance would be appreciated.

This is on an Athlon 64 machine with an nvidia card. I had the nvidia drivers installed before updating (mentioned because I've read about some issues with nvidia drivers and updating). I'm booting from an IDE drive (I have two other SATA drives in the system)

---

### Post by ninek on 2010-02-11
I figured it out. I was right to think that it was a problem with grub. The reason why SGD wasn't working was that I was booting it from a flash drive. It was recognizing the flash drive as /dev/sda and my boot drive as /dev/sdb. This was causing it not to be able to boot. I ran SGD from a CD, which booted my ubuntu partition successfully. I was then able to reinstall grub to the MBR.

---

### Post by darkod on 2010-02-11
If you only needed to reinstall grub2 and the Karmic cd was booting into live desktop without problems, why didn't you just reinstall grub2 like that?
I'm saying this because there is big chance now you have mixed up files of karmic grub2 and SGD. You don't need SGD as long as you can boot the live desktop.
But if it's working, I guess we can say the matter is resolved. Hopefully it won't give you any problems.

---

### Post by ninek on 2010-02-11
That can be mostly attributed to me not knowing what I was doing. : )

I didn't use SGD to restore grub though. I used the ubuntu installation on my hard drive (that I was able to boot into using SGD as a bootloader). That seems like everything should be fine.

---

