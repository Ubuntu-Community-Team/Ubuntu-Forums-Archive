---
title: "Failure Message During Boot-up"
date: 2005-11-11
forum: Installation &amp; Upgrades
---

### Post by Ubuntist on 2005-11-11
I've recently installed Breezy and have been pleased with it, particularly as I'm a newbie.  Whenever I boot up, however, the following error messages appears during the boot process:
[INDENT]
[4294687.607000] drivers/usb/input/hid-cor.d: usb_submit_urb(ctrl) failed
[/INDENT]
although the numbers in brackets change from one boot to the next.  My first thought was to look for hid-cor.d, so I ran
[INDENT]
sudo find / -name hid-cor.d
[/INDENT]
It found no such file, but did produce a warning message:
[INDENT]
find: WARNING: Hard link count is wrong for /proc/9627: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
[/INDENT]

Is this something I should worry about?  If so, what can I do about it?

If it matters, I'm running on a Dell 8300 with a P4, and I've installed the 686 kernel.  Thanks for any hints -- this one's got me completely puzzled.

---

### Post by Kyral on 2005-11-11
Hmm, does it boot though, and work normally?

---

### Post by Ubuntist on 2005-11-12
Yes, the boot completes without any other problems and the system seems to run just fine except for the error message produced by find.

---

