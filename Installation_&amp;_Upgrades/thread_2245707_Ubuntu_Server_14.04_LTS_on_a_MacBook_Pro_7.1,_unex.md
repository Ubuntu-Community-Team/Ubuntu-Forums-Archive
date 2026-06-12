---
title: "Ubuntu Server 14.04 LTS on a MacBook Pro 7.1, unexpected shutdown happens"
date: 2014-09-25
forum: Installation &amp; Upgrades
---

### Post by jcdejournett on 2014-09-25
Hi all,

I'm trying to setup a webserver on an old MacBook Pro to be able to securely, and remotely, manage our home network stuff. The end goal is to be running Ubuntu Server 14.04 LTS, running an apache2 webserver with webDAV, and pfSense running Snort for attack detection. Overkill, I know, but it's an exercise I want to undertake.

Using rEFInd as my boot manager. I've got an EFI partition, OSX partition, OSX recovery partition, grub partition, Ubuntu partition, and some swap space. When I try to boot into Ubuntu, it goes through the normal boot sequence and then, inexplicably, switches over to a screen with a bunch of "Starting soandso  [OK]" and "Stopping foo [OK]" before shutting off. 

If I boot from the Linux FAT on rEFInd (which I assume is how rEFInd sees the grub partition), I get to use the grub loader, and even login before the shutdown happens. I've done several clean installs with varying partition setups, LVM, etc, and I just can't seem to get it right.

I know the two bootloaders probably conflict, but when I don't use rEFInd, and just have grub, the computer always boots into OSX.

I've got some pictures of the "starting" and "stopping" lists if those would help.

video: [https://www.youtube.com/watch?v=O4JnuK1U18E&feature=youtu.be](https://www.youtube.com/watch?v=O4JnuK1U18E&feature=youtu.be)

---

