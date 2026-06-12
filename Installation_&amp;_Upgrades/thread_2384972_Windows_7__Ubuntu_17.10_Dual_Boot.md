---
title: "Windows 7 / Ubuntu 17.10 Dual Boot"
date: 2018-02-14
forum: Installation &amp; Upgrades
---

### Post by norcal618 on 2018-02-14
I'm taking a differential equations class at my local community college, and a portion of the class is held in a computer lab. We utilize the CAS software known as Wolfram Mathematica in this lab for the purpose of solving differential equations, as well as other mathematical calculations. The computers in the lab are Dell Optiplex, running Windows 7. The way in which Windows is configured on these computers is in such a way that allows them to boot into a fresh state, i.e. no persistence, every time they reboot. So any and all software on them stays at the state which it was when first installed. So everything is out of date. Things work so terrible that the system is almost unusable. Constant 'Not Responding' etc. 

I asked my professor if he would mind if I brought my own O.S. on an external hard drive and boot from that rather than use the provided Windows instance. He said okay as long as the computer is still able to boot Windows after I'm done with it. So I brought in a thumb drive installation media for Ubuntu 17.10, and an external usb 500 GB HDD. I was able to boot the installation media without incident. Ubuntu's installer informed me that the computer's bios/uefi wanted to install Ubuntu in uefi mode. The installer recommended against uefi mode if I intended to keep the ability to boot Windows, which I did. So I backed out of the uefi mode installation, and went with the installer's recommendation. I chose to install Ubuntu along side Windows. The installer chose my external HDD on it's own (I verified the drive with gparted prior), and installed Ubuntu to my HDD. 

What I ended up with is a computer that now boots into grub, which gives the option to boot into either Windows or Ubuntu from grub. But when I remove the external HDD which contains Ubuntu, and try to boot the computer all I get is a grub rescue instance. So, in essence the computer can boot either Ubuntu, or Windows, but the usb HDD must be present to boot either, because the only boot loader I can access now is grub. 

My questions: 

1. How can I fix this? Is there some way I can boot into Windows from the grub rescue and re-install, or re-initialize the Windows boot loader? (I think it is MBR). 

2. Could I have avoided all of this by just going against the installers recommendation and installing Ubuntu in uefi mode?

3. Did the Ubuntu installer actually install grub onto the computer's cmos or motherboard? (This seems to be the case because it boots into grub rescue even when the Ubuntu HDD is not present).

---

### Post by QIII on 2018-02-14
Hello!

First, you should not have attempted to install Ubuntu on the computer itself.  That does not sound like what you were given permission to do.  A USB with a bootable Ubuntu installed would have been highly recommended, as you could temporarily change the boot priority in the machine's BIOS/EFI to boot the USB drive without changing the Windows installation if you have permission to do so.

At this point, you should do nothing further to the machine.  You should take your hat in your hands and go to the IT department to ask them to set it straight.  Mucking around further might exacerbate the situation.  It is not our place to tell you how to do anything with the school's hardware.  Their hardware, their rules.

Closed.

---

