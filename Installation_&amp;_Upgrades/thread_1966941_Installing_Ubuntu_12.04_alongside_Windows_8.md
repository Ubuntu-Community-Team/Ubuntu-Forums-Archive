---
title: "Installing Ubuntu 12.04 alongside Windows 8"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by phoda on 2012-04-27
0 down vote favorite
share [g+] share [fb] share [tw]
	

I've installed Windows on half of my hard disk space. Only one partition. I would like to install Ubuntu into my free disk space. The question:

In Ubuntu Installer, when I choose "Install Ubuntu alongside Windows", what's the next step: installer will realocate my NTFS partition, ignoring my free space or it will install Ubuntu into my free disk space, automatically?

Thanks in advance.

---

### Post by newbie-user on 2012-04-27
It would be better to go into Windows, use Disk Management to shrink your partition, then install Ubuntu into the newly created free space.

---

### Post by oldfred on 2012-04-27
I never trust auto anything, so I always partition in advance and use manual install (Something Else) to choose / (root) partition. It auto finds swap. You also need to use manual install if you want a separate /home or want to install the grub2 boot loader to another drive.

Is Windows 8 in BIOS/MBR or UEFI/gpt boot mode?

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

