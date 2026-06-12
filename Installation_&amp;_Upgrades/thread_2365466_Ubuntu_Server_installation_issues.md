---
title: "Ubuntu Server installation issues"
date: 2017-07-07
forum: Installation &amp; Upgrades
---

### Post by jc3iii77 on 2017-07-07
Hello, I am new to Ubuntu forums and new to Ubuntu Server. I am having a issue installing Ubuntu 16.04. every time I install it and reboot the system. I get a black screen, with nothing on it. I have looked on other forums and other resources online, but I still haven't solved the problem yet.

I have a Supermicro x8dth-i Server computer
2 Intel Xeon X5680 3.33GHz
ECC memory: 49GB
2 TB Hard Drive
180GB SSD
125 M.2 in PCI slot. Not trying to boot from this.
I have a BIOS

I have installed Ubuntu on the SSD and one of the regular hard drives, with the same problem. I also tried install with LVM. I used the standard system utillities, and Open ssh server.

When I get to the install grub part. I see this:[IMG]https://ubuntuforums.org/attachment.php?attachmentid=275899&d=1499405676&thumb=1&stc=1[/IMG]

I assume this could be the problem. I don't know. If anyone can help, I would be very appreciative.

---

### Post by SeijiSensei on 2017-07-07
If the machine already boots another operating system like Windows, then the Linux boot manager called grub will need to take over the boot management role.  That's the meaning of the warning in that screenshot.  grub knows how manage multiple operating systems, so you should say yes when asked.  At boot Linux will become the default, but you'll see a menu that will let you select Windows instead.

Dual-boot arrangements are very uncommon on servers.  After all, the server is expected to be running the same OS and services 24/7.  If you're just trying out Ubuntu server, that's okay.  However in that case I'd recommend installing [VirtualBox for Windows]("https://virtualbox.org/") and installing Ubuntu Server into a "virtual machine."  It's possible, using so-called "bridged networking," to have the virtual server appear directly on the network as if it were running on a physical machine.  Using a virtualization product like VB makes trying out operating systems much easier than installing directly to the physical hardware.

---

### Post by jc3iii77 on 2017-07-07
Thank you for the response. However, I only want to install Ubuntu only. I don't have another operating system on the server. Actually, I want to do the opposite and run virtual machines on Ubuntu.

---

### Post by jc3iii77 on 2017-07-07
I used unetbootin and it worked correctly for some reason, even though it said on the installation it might not.

---

### Post by jc3iii77 on 2017-07-07
It worked, but I had problems after I started using it. I am now trying to reinstall using another boot software.

---

