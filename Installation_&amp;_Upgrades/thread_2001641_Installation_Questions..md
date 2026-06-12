---
title: "Installation Questions."
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by Insert Cool Username Here on 2012-06-11
Hello, I have an old system that I'd like to install Linux on, how ever It's pretty old and I'm unsure as to whether or not it will actually run Ubuntu more efficiently than Windows XP (current OS). But that's not my main concern, the biggest problem for me is actually finding a way to install an OS such as Ubuntu 12.04 without a USB or CD. This computers BIOS does not recognize usb devices, I'm fairly certain it will install from CD but I can't get a hold of any CD's for a few days. So my main question is, is there another way to install Ubuntu onto this system, and my second question would be what distro would run best on an old 3.0 p4, 512mb ram system. Lubuntu perhaps? 

I've heard Unetboot will alow me to install an .iso to my hard drive?

---

### Post by black veils on 2012-06-11
you will need either cd/dvd or usb. the ram is too small to install virtually.


you could use Lubuntu or Bodhi Linux, there are others though. Lubuntu will perhaps  be easier to understand than Bodhi Linux. you could try Xubuntu, that might work ok on 512 ram.


Edit:

what is the harddrive size?

---

### Post by snowpine on 2012-06-11
Pentium 4 should be able to boot from USB, check your BIOS options and try pressing the Fn keys, Esc, Del, etc. to get the boot option menu. (On my Dell it is F12.)

The system requirements for Ubuntu are well-documented here: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Lubuntu sounds like a good choice to me. :)

---

### Post by sudodus on 2012-06-11
It is worth testing if you can boot from USB. It should work on a computer with P4.

Another option is to remove the hard drive and connect it to another computer '2', and install running that computer. As long as you don't install any proprietary drivers, it should work in 'any' computer.

This way I have made a portable system on a USB drive, and it works fine (except on computers that need a proprietary driver for graphics or wifi).

If you choose this method, it is easier if you remove or at least disconnect the internal hard drive of computer '2', that you use for installation. Otherwise the boot information and grub installation might be mixed up.

But the simplest method is to wait and burn the iso file to a CD.

Edit: I also vote for Lubuntu

---

