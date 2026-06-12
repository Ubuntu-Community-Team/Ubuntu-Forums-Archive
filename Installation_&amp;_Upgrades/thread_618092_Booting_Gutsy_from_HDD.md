---
title: "Booting Gutsy from HDD"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by singlemalt on 2007-11-20
I am in a bit of a predicament = I have been gifted a Panasonic CF-15 Toughbook I would like to run Ubuntu or Kubuntu on.

There is no onboard media drives and it cannot boot from an external CD drive (unless you have the specific Panasonic part no  XXXXXX).

What I want to do is copy whatever files are necessary to the HDD and then boot it from there.

Is this possible?

And how do I go about it? I'm sure there's a tutorial out there somewhere, but I haven't found it yet.

If worse comes to worse I may go out and buy a USB enclosure for the HDD and try to install from my desktop, but that's my fallback plan.


Any help appreciated.

---

### Post by tommcd on 2007-11-20
So there is no cdrom drive on the tough_book, is that correct? Can the laptop boot from a usb flash drive? If so you can install ubuntu from a bootable usb drive:
[https://help.ubuntu.com/community/Installation/FromUSBStick?highlight=%28from%29%7C%28partition%29%7C%28drive%29%7C%28hard%29%7C%28install%29](https://help.ubuntu.com/community/Installation/FromUSBStick?highlight=%28from%29%7C%28partition%29%7C%28drive%29%7C%28hard%29%7C%28install%29)
If you hava another linux on the system already  you can create a partition on that system, and put the contents of the ubuntu CD on that partition, and edit your grub menu to boot from that partition and install ubuntu from there:
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
I have no personal experience with this. I know that it is possible to install any linux from a partition on your hard drive or from a usb stick. There are many tutorials on the net. Here is one for Zenwalk (an excellent distro, btw), for example:
[http://wiki.zenwalk.org/index.php?title=Hard_disk_install_%28no_CD-ROM%29_with_GRUB_or_LILO](http://wiki.zenwalk.org/index.php?title=Hard_disk_install_%28no_CD-ROM%29_with_GRUB_or_LILO)

---

### Post by singlemalt on 2007-11-20
Correct, no CD Drive in the toughbook.

I don't think I can boot from a USB stick, it only supports floppy,  cdrom (the panasonic external cdrom only) or hd booting.

I'll check out the links

Cheers

---

