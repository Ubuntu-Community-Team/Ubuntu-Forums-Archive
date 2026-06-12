---
title: "Live USB Pendrive Persistent!"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by memoo on 2007-01-24
[COLOR="Purple"]I have created a Live-CD on my USB Flash Drive (1 gig) by downloading "ubuntu-6.10-desktop-i386.iso" and followed the instructions from: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent?action=show&redirect=LiveUsbStick](https://wiki.ubuntu.com/LiveUsbPendrivePersistent?action=show&redirect=LiveUsbStick)

I have followed the instructions to the T!

The problem is that the "persistent" is not working. When the boot menu appears, if I choose custom, the boot starts up, then hangs (black screen with a blinking cursor top left)

My only way around this is to select "live" from the boot menu then, I can boot all the way to the desktop. The bad thing is that I lose the "persistent" feature.

All I want to do is be able to keep the downloaded software that I have installed and save my desktop settings.

ps. I am booting without the live cd in my cd drive. I am just using my USB flash drive.

Thank you in advance!  [/COLOR]

---

### Post by memoo on 2007-02-02
[COLOR="Purple"][FONT="Arial Black"]Anyone? Please?[/FONT][/COLOR] ):P

---

### Post by dcstar on 2007-02-16
> **memoo said:**
> I have created a Live-CD on my USB Flash Drive (1 gig) by downloading "ubuntu-6.10-desktop-i386.iso" and followed the instructions from: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent?action=show&redirect=LiveUsbStick](https://wiki.ubuntu.com/LiveUsbPendrivePersistent?action=show&redirect=LiveUsbStick)

I have followed the instructions to the T!

The problem is that the "persistent" is not working. When the boot menu appears, if I choose custom, the boot starts up, then hangs (black screen with a blinking cursor top left)
........

Did you make the syslinux.cfg exactly as the Wiki specifies (with the various edits as specified in the comments afterwards)?

I just used those instructions on a 4GB USB stick, and it seems to work ok on my PC.

Also double check the partition name (and available space) of the second partition - that is where all of your "dynamic" data is stored.

---

### Post by hsuominen on 2007-06-17
I was wondering if you ever figured it out.. as i seem to have the exact same problem???

---

