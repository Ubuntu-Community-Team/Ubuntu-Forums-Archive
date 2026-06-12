---
title: "How To Install Lubuntu 14.04.1 with encrypted LVM using alternate CD on USB pendrive"
date: 2015-02-27
forum: Installation &amp; Upgrades
---

### Post by turtle-purple on 2015-02-27
It works! It was a long and windy path to find out how.
There's three bugs to bypass.
The solution is actually quite short:
1. Use the alternate CD (Its not offered for 14.04.2 at this time so use 14.04.1)
2. Select "Install" (from the Unetbootin-menu)
3. When you're asked to install grub to MBR select "No" and  specify the correct target device

That's it - gooday :]

A little more Detail:

1: There's a [Bug ]("https://bugs.launchpad.net/ubuntu/+bug/1241833")
in the Desktop installer. It affects Lubuntu 13.10 to 14.04.2 (I tried it with Lubuntu-14.04.2-Desktop-i386 and 14.04 and 14.04.1) and maybe more. There is a workaround, described [here]("http://askubuntu.com/a/546378/130556"):  But I had alrdy found my way using the alternate CD, and It might be a little more straightforward.

2. I was Using Unetbootin to install the iso on my usb-pendrive.
It creates it's own bootmenu and offers the options "Install" "Expert Install" and "Install Lubuntu" among others.
"Install Lubuntu" will fail at "select and install software" (this [bug]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1417918")  )
So better use "Install" (or "Expert Install") which will lead to another bug if you use a usb-pendrive for installation:

(heres a [bugreport]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1426219")  ) Grub will be installed to the MBR of the usb-pendrive and you can only boot your PC with the usb-pendrive inserted.

3: The MBR-bug is easy to solve though by selecting "No" when you're asked if grub shall be installed to MBR. This will not cancel the install of grub. You will be asked to specify the target device for grub-install.

That's it - was a pain to find it out, cause error-messages where always useless.
Anyway -  i hope it helps

---

