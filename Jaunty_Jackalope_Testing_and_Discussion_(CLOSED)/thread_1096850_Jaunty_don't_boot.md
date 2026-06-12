---
title: "Jaunty don't boot"
date: 2009-03-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by pomalin on 2009-03-15
Hi, I want to give a try to Jaunty, but, I can't boot, I try to boot on live cd, but it hang on loading the kernel, it just do nothing, and same thing with an upgrade from a fresh install of intrepid.
It's 64 bit version, on an asus p5kpl-am with an intelQuad9400.
Is there something I can do ? 
I will try the 32 bit version.

---

### Post by Marat89 on 2009-03-15
hi,
maybe you can try the Alernate CD, install it and look what happens

---

### Post by pomalin on 2009-03-15
the alternate cd don't boot, like the desktop cd in 64 or 32 bits.

---

### Post by pomalin on 2009-03-16
I filled a bug in launchpad;
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268")

---

### Post by pomalin on 2009-03-17
Am I the only one wich can't boot ?

---

### Post by taavikko on 2009-03-17
At grub, remove splash from startup options so we could see where it hangs...

Probably acpi=off could trigger the start...

---

### Post by pomalin on 2009-03-17
I have done all this, and nothing does it, it just hang at loading the kernel, after the Starting up ...
I just got the blinking cursor, and nothing.
I have tried to remove the uuid and replace it by /dev/sdb1  but, same thing.

---

### Post by pomalin on 2009-03-17
Ok, I have just compile kernel 2.6.29_rc8 from git, and it boot ok, will give a try to recompile the ubuntu kernel without MCE like I saw in a kernel mailing list.

---

### Post by nyarnon on 2009-03-17
Probably obsolete but do you run the newest bios for your system?

---

### Post by pomalin on 2009-03-17
yes I update my bios

---

### Post by Nullack on 2009-03-17
Try the debugging guidelines for kernel problems in the wiki

---

### Post by pomalin on 2009-03-17
I've tried this, but nothing does it, just un blinking cusrosr, no messages, nothing. I've just compile the ubuntu kernel from git 2.6.28-7 and, no boot.
so I will try to compil it with another option.

---

### Post by heli@work on 2009-03-25
I have experienced the same problem.
After updating from intrepid I cannot boot the current kernel 2.6.28-11-generic.

When resetting the PC I get:
Grub loading stage 1.5
Boot from (hd0,0) ext3 08dd... (the uuid)
Starting up ...

Then it stop there.

Luckily it boots with the older kernel 2.6.27-11-generic, although the grub settings (uuid) are the same. Strange.

Here some more detailed informations:

/boot/grub/menu.lst:

title       Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid        08dd9c63-37c3-4368-82cd-94ea9751d91e
kernel      /vmlinuz-2.6.28-11-generic root=/dev/mapper/vg1-root ro
initrd      /initrd.img-2.6.28-11-generic
quiet


title       Ubuntu jaunty (development branch), kernel 2.6.27-11-generic
uuid        08dd9c63-37c3-4368-82cd-94ea9751d91e
kernel      /vmlinuz-2.6.27-11-generic root=/dev/mapper/vg1-root ro splash
initrd      /initrd.img-2.6.27-11-generic
quiet

The hardware is a Dell 755 with:
Intel Core2 Duo CPU E8500@3.16GHz

lspci:
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:03.2 IDE interface: Intel Corporation 82Q35 Express PT IDER Controller (rev 02)
00:03.3 Serial controller: Intel Corporation 82Q35 Express Serial KT Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
03:00.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 54)

Some more information needed?
Did anybody solve this problem?

---

### Post by pomalin on 2009-03-25
Finally, I'm not alone in the world, have you try to boot the livecd ?
Join my bugreport

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268")

---

