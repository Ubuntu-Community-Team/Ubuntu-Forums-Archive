---
title: "installing on a pentium 233"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by blagger on 2007-02-17
Hi all,

Just trying to install Ubuntu Server 6.06 on a pretty old box:

Pentium II - 233
192 MB RAM
4 GB HDD

I boot fine from the installation CD, then I set kernel option noacpi, and proceed with install flawlessly.

But... then I reboot, and after loading the kernel, it hangs and reboot.

How can I know what is happening? If it can load the kernel to make the install... why can't load it after it? Any grub options to try?

Thanks!

---

### Post by Peter76 on 2007-02-17
noacpi option doesn't exist afaik... you probably mean acpi=off. Try to boot with the following options: acpi=off noapic nolapic.

Good luck

---

### Post by blagger on 2007-02-17
adding those grub options doesn't work, it doesn't boot.

I've noticed that the installation CD loads the linux kernel 386, but it installs the linux-image-server kernel. maybe the installed kernel is compiled with options not compatible with my CPU.:confused: 

is there a way to force the installation of the linux-image-386 ??

i've found it is on the cd under /pool/main/l/linux-meta/linux-image-386_2.6.15.24_i386.deb

thanks.

---

### Post by blagger on 2007-02-18
okay i found the solution:

-boot from CD and make a LAMP install (or whatever you want)
-reboot, oops it hangs!. the processor is too old for the kernel linux-image-server.
-boot again from the CD but select Rescue Mode
-after a while, you're prompted for some options. just choose "start a shell in the selected partition"
-you'll have login in your system. now install the right kernel:
   # apt-get install linux-image-386
-reboot. you're done!

hope it helps for someone.:KS

---

