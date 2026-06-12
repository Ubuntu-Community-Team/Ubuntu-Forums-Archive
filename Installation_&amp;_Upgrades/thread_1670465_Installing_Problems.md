---
title: "Installing Problems"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by Luke35120 on 2011-01-19
Hi all,
I've managed so far to get a CD burnt that contains my Ubuntu. Everything works fine except when I boot into Ubuntu from my CD the splash saying Ubuntu (very sexy) with the orange dots just stays up there. I left it for awhile (10-15 minutes) and have tried several times over to reboot and try again. Any suggestions?

Thanks,
Luke

---

### Post by slooksterpsv on 2011-01-19
Reboot, hold down SHIFT before it goes past the <computer manufacturer> logo screen, and hold SHIFT until you get an item that tells you to select what to boot.

Press e, to edit, and remove quiet splash from the end, it'll look something like this:

```

	linux /boot/vmlinuz-2.6.35-23-generic root=UUID=60a36d1f-207a-4ee3-8029-97c296927321 ro quiet splash
	initrd /boot/initrd.img-2.6.35-23-generic

```

Then press CTRL+x to boot, wait for a few, and see if it freeze up, let us know what the error is. You can also remove quiet and splash and add:
nomodeset
acpi=off

Try those and see what happens

---

### Post by wormyblackburny on 2011-01-19
In my experience burning the ISO's, it has been fairly common to have to burn a few copies before it will work . I recommend inspecting the disk before/after burning it for any defects scratches etc. Worst case you can order one at [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/), If you do get an ISO that fully boots, always run the option to check it before doing the install (yes it is painfully slow, but better than getting all the way through it and not having it work ;))

---

### Post by slooksterpsv on 2011-01-19
> **wormyblackburny said:**
> In my experience burning the ISO's, it has been fairly common to have to burn a few copies before it will work . I recommend inspecting the disk before/after burning it for any defects scratches etc. Worst case you can order one at [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/), If you do get an ISO that fully boots, always run the option to check it before doing the install (yes it is painfully slow, but better than getting all the way through it and not having it work ;))

Now that you mention it, no offense, but I've had more problems burning to CDs than DVDs, DVDs have been more stable and I haven't had any issues, yet. I usually use USB drives most of the time with unetbootin.

---

