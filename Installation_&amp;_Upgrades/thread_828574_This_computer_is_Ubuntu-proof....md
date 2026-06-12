---
title: "This computer is Ubuntu-proof..."
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by PiGeek31415 on 2008-06-13
Okay, so my friend brought me an old Dell Latitude LS laptop. Someone put XP on it, and it runs very, very slowly.

Right now, it has a 500 mHz Pentium III processor and 128MB of RAM.

The problem lies in how to get ubuntu to install to this computer, as it lacks a CD drive, doesn't have a floppy drive, and seems to be unable to boot to its only USB port. I've rearranged stuff in the BIOS, but nothing seems to work. It didn't even recognize that I had a bootable flashdrive in the port.

I put the Xubuntu desktop install disk in the USB cd drive and installed via WUBI and the "--skipmemorycheck" option.

It boots fine, up until Ubiquity (the ubuntu installer) tries to load, where it freezes indefinitely. 

Is there a way to get the alternate install disk to work? I can't think of anything.

Any and all help is greatly appreciated.

---

### Post by Pumalite on 2008-06-13
You could try Xubuntu Alternate CD:
[http://cdimage.ubuntu.com/xubuntu/releases/8.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.04/release/)

---

### Post by PiGeek31415 on 2008-06-13
> **Pumalite said:**
> You could try Xubuntu Alternate CD:
[http://cdimage.ubuntu.com/xubuntu/releases/8.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.04/release/)

How would I go about doing that, since it doesn't have WUBI?

I can't boot from CD, since there isn't a CD drive in the computer, and it won't boot from USB.

Is there some way I can make it work with the current WUBI installation?

Thanks,
-PiGeek31415

---

### Post by Pumalite on 2008-06-13
Sorry, I don't know anything about wubi. Someone will come to your rescue.

---

### Post by PiGeek31415 on 2008-06-13
Thanks anyway; I'll keep googling in the meantime.

---

### Post by Rhubarb on 2008-06-13
While this thread is a bit old, most of it is correct:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=74386](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=74386)

Basically, just take out the hard drive, buy an IDE 2.5" laptop to 3.5" hard drive converter, then install Ubuntu (perhaps Xubuntu would be better) on the laptop hard drive from a desktop computer.
Then put the laptop hard drive back into the laptop.

There's a lot of threads out on the internet that can assist you to do this.
My server is an old laptop that can't boot from USB, has no optical drive, has a broken screen, is incompatible with the ubuntu server linux kernel.
Ubuntu server 8.04 runs just fine on it (after installing it on another PC to it's hard drive, and changing the kernel to use linux-generic).

---

### Post by hi-phile on 2008-09-19
Hi,
At first, I thought the same way you did.  But because Linux and Ubuntu are awesome, it can work if you keep at it and find good advice and help.

What I did with my friends Dell Latitude LS with 128MB RAM and PIII 400Mhz without any CDROM or Floppy was used the Ubuntu TFTP Netboot installation method.  I have another Ubutu system that I used to do this with.  I had to spend time installing and configuring TFTPD and DHCP3d and while I could get the DHCP server working, TFTP was not working.  I kept getting errors about not finding the pxelinux.0 file.  I finally found a page that actually helped me get past this and finally was able to install Ubuntu 8.0.4 on this system using PXE diskless network installation with the tips from the following site.

[http://www.r3uk.com/index.php/tech-tips/38-software/13-pxe-diskless-ubuntu-installation](http://www.r3uk.com/index.php/tech-tips/38-software/13-pxe-diskless-ubuntu-installation)

---

