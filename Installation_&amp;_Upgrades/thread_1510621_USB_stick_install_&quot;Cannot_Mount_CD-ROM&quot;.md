---
title: "USB stick install &quot;Cannot Mount CD-ROM&quot;"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by joshdb666 on 2010-06-15
I'm doing a USB stick install and when going through the installer, after selecting keyboard origin it tried to mount the CD-ROM drive instead of the USB port. I dont have any blank CDs so a live CD isnt an option. It's booting from the USB to get to the installer, just seems like the installer doesnt realize it needs to do the same.

---

### Post by cariboo on 2010-06-16
How did you create the Live usb device? What version are you trying to install?

---

### Post by wilee-nilee on 2010-06-16
> **joshdb666 said:**
> I'm doing a USB stick install and when going through the installer, after selecting keyboard origin it tried to mount the CD-ROM drive instead of the USB port. I dont have any blank CDs so a live CD isnt an option. It's booting from the USB to get to the installer, just seems like the installer doesnt realize it needs to do the same.

Are you using plop to boot the USB? Can you see the partitions with gparted.

---

### Post by konradst on 2011-10-12
I've got the same problem on the following machine:
AMD 1,3GHz/1gb ram
on both
xubuntu  11.04
ubuntu 11.04
2xhdd
while trying to use usb installs both installers unetbootin and universal usb installer
I had to use plop because my machine doesnt boot from this sandisk pendrive because although i managed to set it up in bios's boot sequency 
normally the bios would tell me that i have to load a proper media.
i've tried grub as mbr: it doesnt recognize my pendrive as hd2,0, nor any other up to 7,0 or 8,0  on the other hand, the diode on the pendrive is lit as if it tried to read something
wingrub's setup sees it after windows has loaded as hd2,0 although i haven't checked wingrub after windows loader
with plop, the installer says that it cannot mount dev/something and freezes (unetbootin) or tries ports from 0 to infinity (universal installer)
maybe my system is too obsolete to load from usb? however, oddly, it launches somehow but cannot mount after the menu and few first installer inits
btw my machine does not use usb 2.0 (windows keeps prompting about that)
unless you have a solution, I'll try the following:
- remove this usb from boot sequency in bios (maybe it mistakes it for cd-rom)
- try grub/wingrub under windows loader options
- try to use hd install from unetbootin, although on C i have got only 700mb free
- waste a blank cd;p

---

### Post by Hakunka-Matata on 2011-10-12
Sandisk and U3 software pre-installed on the usb.  If your sandisk usb has U3 software on it, remove it.  Check out the following link:  or search for "Sandisk U3 removal", 
[http://kb.sandisk.com/app/answers/detail/a_id/2550/~/removing-u3-launchpad-on-a-pc]("http://kb.sandisk.com/app/answers/detail/a_id/2550/%7E/removing-u3-launchpad-on-a-pc")

---

### Post by konradst on 2011-10-13
> **Hakunka-Matata said:**
> Sandisk and U3 software pre-installed on the usb.
Thanks, I've seen that one but my Sandisk does not have this software, it's even been formatted.

I've just installed Ubuntu from CD, though the problem with USB remains.

---

