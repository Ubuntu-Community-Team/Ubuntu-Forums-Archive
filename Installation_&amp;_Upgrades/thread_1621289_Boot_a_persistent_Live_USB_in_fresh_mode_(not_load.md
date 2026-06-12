---
title: "Boot a persistent Live USB in fresh mode? (not loading saved configuration / session)"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by plari on 2010-11-14
Hello:

I have a persistent pendrive of Ubuntu:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

It has a file where it saves the configuration of my computer:
casper-rw

But if I boot this USB flash drive in another computer I would like to do it in a fresh way, that is, without loading the configuration of my computer (saved in the casper-rw file).

For example, in Puppy Linux this can be done easily, just putting pfix=ram in a boot option of syslinux.cfg and selecting this option when booting.

I think this is important because I think that otherwise the Ubuntu (at least in some cases) cannot open if used in a computer different to the one where casper-rw was configured. It happens to me that I cannot run Ubuntu with my pendrive when inserted in a different computer (I think the reason is what I've said).

Any ideas?

Thanks

---

### Post by searchfgold6789 on 2010-11-14
You will have to ask a programmer how to add a menu entry to the Boot Screen that bypasses the casper-rw file.

---

### Post by plari on 2010-11-14
I think that someone around here may know it. I hope so ....

---

### Post by C.S.Cameron on 2010-11-14
With versions previous to 10.10 you could press F6 at the first screen and delete the word persistent to temporarily boot non persistent.

I'm not sure about 10.10 though, I'll get back to you.

However unless you have added proprietary drivers such as Nvidia video, your persistent flash drive should work in any computer that will boot flash.

Edit:
With 10.10 you need to quickly hit Esc when booting, this will bring up the old screen. then you can press F6, hit Esc again and then delete "persistent" in the line of text, then press enter to boot non persistent for the current session.

Edit again:
If you wish to boot the Ubuntu iso using grub2, you can add a menu item to grub the same as the first menu item and add <space>persistent after ...quiet splash --.
But you need a casper-rw partition or copy a fresh casper-rw file to the drives root directory for persistence to work.
(The casper-rw partition is a good option if you want more than 4GB persistence).

---

### Post by beew on 2011-02-03
A very handy and newbie friendly way to accomplish what you want would be to create a liveusb using the multisystem utility. [URL="http://liveusb.info/dotclear/"]http://liveusb.info/dotclear/
[/URL]
You can choose to create a persistence layer when you make the usb,--provided the distro supports persistence, it is supposed to work with many distros besides Ubuntu, though apparently didn't work with Fedora14 despite what it advertises. If you do that when you boot the liveusb it would have two options, the default is without persistence, but you can also choose the persistence mode.

---

### Post by vezolmi on 2011-04-21
There is useful info about this in [http://ubuntuforums.org/showthread.php?t=1734965](http://ubuntuforums.org/showthread.php?t=1734965)

---

