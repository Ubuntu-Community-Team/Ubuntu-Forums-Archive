---
title: "Issues installing Ubuntu 12.04 (x64)"
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by VFQuake on 2013-01-04
>>>> **VFQuake said:**
> Update:

Installed succesfully with "no splash"

Reboot after install, followed guide regarding graphics issues, though I'm stuck.

I'm in recovery mode, though when I try to edit with "sudo nano  /etc/default/grub , it says it's "read only". if I try to use "vbeinfo"  or any variation, unkown command, and "gksu gedit" gives me  ""Gtk-WARNING **: cannot open display: .

I'm running a GTX 550 ti, and this problem is common, but I'm at a brick  wall. Once I get the drivers installed, I should be fine, but without  being able to edit the grub so I can actually boot to desktop, I'm at a  loss. Any help is greatly appreciated.

---

### Post by 2F4U on 2013-01-04
> Computer A: Flashing cursor after clicking anything but "memtest" at Ubuntu install menu, (this occurs on either ISO/DVD)

Sounds like a problem related to graphics. Is this the computer in the profile above?

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

> Computer B: Doesn't even recognize that I'm attempting to install.

Does that mean, computer B doesn't boot from the DVD you created? Does this machine have the same hardware specs as computer A?

---

### Post by VFQuake on 2013-01-05
I've attempted to use nomodeset, to no avail. Same with ACPI=off.
Computer B has different specs, and does not even attempt to boot Ubuntu dvd. (Note: I was only attempting to install on the other computer, to see if the DVD was functioning, after that failed, I checked the ISO, and it was consistent with Ubuntu.)

I just attempted to install Wubi, at first restart, I had no options to boot from either OS, I repaired Windows bootloader (recboot /fixboot) which allowed Windows 8 bootloader menu to appear, allowing me to choose from either Windows 8 or Ubuntu (wubi). I chose "Ubuntu", but got stuck a purple screen with nothing on it. I restarted, and am now back in Windows 8. Could this be an issue with my bootloaders? Or is it more than likely the graphics issue?

And yeah, Computer A is the computer posted in the above image.

---

### Post by 2F4U on 2013-01-05
Maybe an issue with the new secure boot option?

---

### Post by VFQuake on 2013-01-05
Update:

Installed succesfully with "no splash"

Reboot after install, followed guide regarding graphics issues, though I'm stuck.

I'm in recovery mode, though when I try to edit with "sudo nano /etc/default/grub , it says it's "read only". if I try to use "vbeinfo" or any variation, unkown command, and "gksu gedit" gives me ""Gtk-WARNING **: cannot open display: .

I'm running a GTX 550 ti, and this problem is common, but I'm at a brick wall. Once I get the drivers installed, I should be fine, but without being able to edit the grub so I can actually boot to desktop, I'm at a loss. Any help is greatly appreciated.

---

### Post by VFQuake on 2013-01-05
Runnning in recovery:

sudo apt-get update

sudo apt-get upgrade

and then attempting to install nvidia drivers through terminal.

---

### Post by VFQuake on 2013-01-05
> **VFQuake said:**
> Runnning in recovery:

sudo apt-get update

sudo apt-get upgrade

and then attempting to install nvidia drivers through terminal.

Everything is working flawlessly now.

---

