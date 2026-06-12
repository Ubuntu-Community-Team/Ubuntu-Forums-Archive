---
title: "Installed Ubuntu 16.04 along with WIndows 10. It only boots Win, no grub screen."
date: 2016-10-14
forum: Installation &amp; Upgrades
---

### Post by sanzybones on 2016-10-14
So, this is my first time installing Ubuntu along with Windows, before I only used VMs.
But I don't get a grub screen when I reboot, it just boots Windows. I have to press F12 and choose the option "Hard drive" or something to connect to Ubuntu.
I turned off the "Fast boot" option on Windows, nothing.
I then booted to Ubuntu through that method, and used the boot-repair tool thing, and it gave me this link: [http://paste2.org/vGdcHH69](http://paste2.org/vGdcHH69)
If someone could help me make sense of that and teach me how to repair this... Thank you.

---

### Post by ubfan1 on 2016-10-15
Looks like you installed Ubuntu in legacy mode instead of UEFI mode like Windows.  Set your BIOS/UEFI settings to boot UEFI mode, do the install again, selecting "something else" and select the existing / , /home and swap (of course back up /home if you have actually put anything there and don't format).  I think you can just ignore the legacy boot if you can set your BIOS to boot only UEFI or UEFI before legacy.

---

