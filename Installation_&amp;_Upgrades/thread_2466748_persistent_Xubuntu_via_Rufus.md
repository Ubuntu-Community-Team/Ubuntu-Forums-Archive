---
title: "persistent Xubuntu via Rufus"
date: 2021-09-04
forum: Installation &amp; Upgrades
---

### Post by pc-cobbler on 2021-09-04
I freely admit that I am abusing Xubuntu, but this is an educational experiment.

I used Rufus to "burn" a USB flash drive with Xubuntu (I set 6 GB for the persistent partition). Rufus instructions state that only Ubuntu and Debian work with Rufus in this manner, and the developer is not kidding, as Debian spins (Sparky) and Ubuntu spins (Linux Mint) do not work, but Xubuntu does. I have been able to update, add packages, and change settings, with them being reflected on the next boot.

But I have created a Frankenstein. Things are persistent, but every time I boot, I see the "Try Xubuntu Or Install Xubuntu" popup. Things would be so much faster if I could save the setting to "Try Xubuntu." I have no idea where to look for this setting, but I am willing to play around with the relevant file. Any hints?

---

### Post by mikewhatever on 2021-09-04
If you hit any key (say, the space key) as soon as the logo+background appears, you should see a menu with several options, try or install among them. Select one with arrow keys, and hit Enter.

---

### Post by pc-cobbler on 2021-09-05
Thanks for the reply. Okay, so I pressed the spacebar during boot. I was asked for my language choice and then how I wanted to start Ubuntu. The boot was much faster than waiting for the Try/Install dialog. However, after booting, it became clear that all of my saved settings had been reset to default. So booting that way does not recognize the persistence that Rufus created, which may very well be a Rufus bug. Oh well, it was an interesting experiment.

---

### Post by tea for one on 2021-09-05
I assume that you used Rufus because you use Windows 10 and do not have Ubuntu installed.

If you have another USB stick to use as a target device:-

Boot into your existing Persistent Xubuntu session
Download mkusb[COLOR="#0000FF"][/COLOR] [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
Use [COLOR="#0000FF"]mkusb[/COLOR] to make another Xubuntu persistent device.

See if the boot process via [COLOR="#0000FF"]mkusb[/COLOR] is better for you.

I've always appreciated the elegance of the boot process and Grub menu of a [COLOR="#0000FF"]mkusb[/COLOR] live session.

---

### Post by C.S.Cameron on 2021-09-05
**Eliminating Try/Install screen:** 

Remove **maybe-ubiquity** from the /boot/grub/grub.cfg file.
With Rufus you can do this from Windows or from a second Ubuntu Live USB, not from the running Rufus USB.

---

