---
title: "Can't boot UBUNTU from a 1tb usb hard drive."
date: 2019-10-18
forum: Installation &amp; Upgrades
---

### Post by Tom's New Linux on 2019-10-18
I used Startup Disk Creator to create a portable USB hard drive on a 1 TB usb hard drive. Everything appeared to complete normally with no error messages, but UBUNTU 16.04 won't boot. I get a "no operating system found" message when I try.

I did the same thing using an 8.2 GB flash drive and it booted UBUNTU perfectly. Apparently GRUB is having some kind of problem, but with no error messages I don't know where to start troubleshooting. 

What's wrong, and what can I do about it?

---

### Post by oldfred on 2019-10-18
Using startup disk creator on a 1TB drive, converts it to about 2GB.
I would expect it to work as it should boot in either UEFI or BIOS boot mode.

Use your 8GB flash drive and do a full install to your 1TB drive. 
Since external, you need to partition in advance. And if UEFI, be sure to include an ESP - efi system partition using gpt partitioning.

[https://askubuntu.com/questions/638612/how-do-you-run-ubuntu-from-usb-on-a-windows-8-1](https://askubuntu.com/questions/638612/how-do-you-run-ubuntu-from-usb-on-a-windows-8-1)
Full install to external - sudodus   unplug internal drive(s)
[https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)
[https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers/1083577#1083577](https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers/1083577#1083577)
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312)

---

