---
title: "install from harddisk using a mounted image"
date: 2005-05-16
forum: Installation &amp; Upgrades
---

### Post by testure on 2005-05-16
Hi!

I've been using Arch Linux for some time now, but after reading all those positive reviews about Ubuntu, I've decided to finally try it out (allthough I'm not going to erase Arch :)).  I've downloaded the latest Ubuntu release (i386), mounted it in /mnt/ubuntu and copied the following files to /opt/ubuntu: vmlinuz and initrd.gz (which can be found in the install directory on the iso image).  I edited my GRUB boot file to point to these files using:

title Ubuntu Install
kernel /opt/ubuntu/vmlinuz rw root=/dev/ram
initrd /opt/ubuntu/initrd.gz

I can't boot however, and I'm left with the advice to use an init= option.  Has anyone got an idea what option I should be using?  I've never done an install from harddisk (yet), and most topics I find only deal with installing it from in a Windows installation.

Kind regards,

---

