---
title: "Recognition"
date: 2005-07-05
forum: Installation &amp; Upgrades
---

### Post by profediego on 2005-07-05
I am wondering if i install Ubuntu in my PC, if it recognizes my windows partitios and setup a bootloader with the option to boot windows or do i have to do everything manually.

---

### Post by Xian on 2005-07-05
Yes, it should do all this with only some minor prompts for your approval. I would suggest that you throughly view the [Official Install Guide](http://archive.ubuntu.com/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/) and look over the [Hoary Newbie Install Guide](http://mrbass.org/linux/ubuntu/install/). Be absolutely certain to carefully read the [Mount Point Selection](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch06s03.html#di-partition) section.

Here's an excerpt: [i]"Before a boot loader is installed, the installer will attempt to probe for other operating systems which are installed on the machine. If it finds a supported operating system, you will be informed of this during the boot loader installation step, and the computer will be configured to boot this other operating system in addition to Ubuntu. 

Note that multiple operating systems booting on a single machine is still something of a black art. The automatic support for detecting and setting up boot loaders to boot other operating systems varies by architecture and even by subarchitecture. If it does not work you should consult your boot manager's documentation for more information.
 
Note: The installer may fail to detect other operating systems if the partitions on which they reside are mounted when the detection takes place. This may occur if you select a mountpoint (e.g. /win) for a partition containing another operating system in partman, or if you have mounted partitions manually from a console."[/i]

---

### Post by jasmuz on 2005-07-05
[QUOTE=profediego]I am wondering if i install Ubuntu in my PC, if it recognizes my windows partitios and setup a bootloader with the option to boot windows or do i have to do everything manually.[/QUOTE]
 Answer:

Ubuntu will recognize your windows partition, but you will have to add it the /etc/fstab so it gets mounted on every boot.

The bootloader will allow you to boot into windows from its menu.

---

### Post by profediego on 2005-07-07
Thank you Xian... i already install Ubuntu and rigth now playing with it... Thank you.

---

