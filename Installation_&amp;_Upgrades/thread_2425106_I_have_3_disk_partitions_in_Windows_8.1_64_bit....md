---
title: "I have 3 disk partitions in Windows 8.1 64 bit..."
date: 2019-08-20
forum: Installation &amp; Upgrades
---

### Post by spi2 on 2019-08-20
I have 3 disk partitions in Windows 8.1 64 bit...


How I Create boot able Ubuntu 18.04.3 and with what utility, rufus I cannot..

---

### Post by Dennis N on 2019-08-20
> **spi2 said:**
> I have 3 disk partitions in Windows 8.1 64 bit...


How I Create boot able Ubuntu 18.04.3 and with what utility, rufus I cannot..

You have downloaded the ISO file for Ubuntu to your computer?
[https://ubuntu.com/download](https://ubuntu.com/download)
If not Rufus, try Etcher. Simple to use to make bootable installer.

---

### Post by TheFu on 2019-08-20
Perhaps running in a virtual machine would work for you?  It is much less risky and doesn't require dangerous partitioning.
As for partition help, we need to see the disk layout to help.  Is it a GPT or MBR partition table? How much free space is there?   Do you actually want to dual boot?

Google "create ubuntu boot install" to find step by step tutors for all the popular OSes: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows)  

Not all flash drives are compatible with all USB chips and BIOSes. Some cannot be used to boot.  Always use a USB2 port on the computer, not USB3 for boot.  If it has a built-in SDHC or MicroSD card, often we can boot from that just like a USB2 port.  Try different ports on your system. Try different flash drives from different vendors.  I've never had any issues using SDHC for boot.

I'm not a fan of etcher, but if it works for you, great!  It is extremely bloated.  Generally, I just dd/ddrescue the ISO file onto the flash drive directly. No extra download needed, but if you are new to Unix, this can be very dangerous. It will let you overwrite the HDD if the parameters are entered wrong, backwards, incorrectly.

Using a virtual machine is much safer, more flexible, and easier, really.  With dual boot, a few times a year MSFT will break the boot when they update their boot files.  The downside for using a VM is with GPU performance, which many Linux users don't care much about.  If you don't plan to game, it will be fine.

---

