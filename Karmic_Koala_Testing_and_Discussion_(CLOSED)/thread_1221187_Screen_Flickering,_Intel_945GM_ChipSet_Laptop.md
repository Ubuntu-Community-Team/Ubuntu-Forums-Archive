---
title: "Screen Flickering, Intel 945GM ChipSet Laptop"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2009-07-23
Anyone else having these flickering issues with this chipset, I'm using an Fujitsu-Siemens Amiloli1818 on Karmic Alpha 3.

Lee

---

### Post by mariner09 on 2009-07-23
I have a 965 but wasn't seeing any flickering.  Saw some other weirdness that might have been related to heat.

---

### Post by go7Ul1ai on 2009-07-23
Hmmm, I have noticed that it only flickers on the highest-resolution on my laptop which is 1440x900, I'm guessing I will have to stick with a lower resolution until an update hopefully fixes the issue.

I know it's a Karmic issue as everything works as it should on my Jaunty and Vista partitions.

Lee

---

### Post by buzzmandt on 2009-07-23
i945 here too, no flickering but still can't play nwn..... pretty sure it's kernel issue as nwn plays fine in 2.6.30-10 with all the same setting just booting a different kernel.  I get more time I'll get someone to help me trouble shoot it and maybe file a bug report.

---

### Post by buzzmandt on 2009-07-23
just installed 2.6.31 rc4 no improvment, gotta drive some more will deal with it later.

---

### Post by go7Ul1ai on 2009-07-25
I am still getting this issue, even after updating fully (and using an updated kernel).

Lee

---

### Post by Starks on 2009-07-25
I have a i945gm with a 1440x900 screen

No problems  here.

---

### Post by mattduckman on 2009-07-25
yeah, here's the bug report

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401399](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401399)

it hasn't really received any attention.

also, to restate my comment in the bug, adding 'nomodeset' to your kernel config line in grub should stop the flickering

---

### Post by go7Ul1ai on 2009-07-25
Thank you for the responces, how do I edit the grub menu.lst? I can't seem to find it.

Lee

---

### Post by jerrylamos on 2009-07-25
> **lee.jarratt said:**
> Thank you for the responces, how do I edit the grub menu.lst? I can't seem to find it.

Lee

It's much changed and tricky.

If you've got something simple, sudo gedit /etc/default/grub
and then do sudo update-grub.

If you really want to mess with Grub 2's version of menu.lst, then:

sudo chmod 644 /boot/grub/grub.cfg
sudo cp -dpu /boot/grub/grub.cfg /boot/grub/grub.cfg.save
sudo gedit /boot/grub/grub.cfg

Good luck.  First I'd recommend reading:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

I saw some hint somewhere that Grub2 is planning a graphical interface.

Jerry

---

### Post by jpeddicord on 2009-07-26
#[lpbug]399829[/lpbug] has a little more information on the problem and the fix ETA. (Duped 401399.)

> This bug hit people on certain chipsets with oddball combinations of dual channel memory running at certain speeds, but its a known problem and a fix is already out and testing.

The fix hasn't quite hit the ubuntu kernel tree yet. Probably will show up in -5.

---

### Post by go7Ul1ai on 2009-07-26
> **jacobmp92 said:**
> #[lpbug]399829[/lpbug] has a little more information on the problem and the fix ETA. (Duped 401399.)



The fix hasn't quite hit the ubuntu kernel tree yet. Probably will show up in -5.

Thanks for the heads up bud,

Lee

---

### Post by go7Ul1ai on 2009-08-05
This issue is still affecting me, fully updated etc.

Lee

---

### Post by taavikko on 2009-08-06
> **lee.jarratt said:**
> This issue is still affecting me, fully updated etc.

Lee

Booting with "nomodeset" are we?

---

### Post by go7Ul1ai on 2009-08-08
> **taavikko said:**
> Booting with "nomodeset" are we?

No need for the attitude.

Anyway, I would still rather like this to be fixed, rather than bototing with "nomodeset".

---

### Post by taavikko on 2009-08-09
> **lee.jarratt said:**
> No need for the attitude.

Anyway, I would still rather like this to be fixed, rather than bototing with "nomodeset".

Don't quite see how you could take that as an "attitude"?
Not meant as one.

Until it's fixed you just gotta boot with it.
Pretty certain that it's been worked on.
check the changelogs when it's fixed.
"libdrm, mesa, kernel, xorg-driver-intel" are the relevant packages.

---

