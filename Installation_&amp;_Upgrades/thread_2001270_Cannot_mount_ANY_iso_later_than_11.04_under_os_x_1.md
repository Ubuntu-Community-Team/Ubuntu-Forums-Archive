---
title: "Cannot mount ANY iso later than 11.04 under os x 10.6.8"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by robotlovesyou on 2012-06-10
For clarity, my goal is to create a bootable install usb using the [instructions in the guide here]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick") but following this results in a non-bootable usb which will not even mount as a drive once the computer has booted up.

Furthermore every 12.x iso I have tried will not even mount using the OS X disk utility, instead showing an error message "Unable to mount the_iso_i_am_trying.iso (no mountable file systems)

I think this is the root of the problem

All the 11.x iso images I have tried work fine.

I have tried 

ubuntu-11.10-desktop-i386.iso
ubuntu-12.04-desktop-amd64.iso
ubuntu-12.04-desktop-amd64+mac.iso
ubuntu-12.04-dvd-i386.iso
precise-desktop-amd64+mac.iso
quantal-desktop-amd64+mac.iso

All of which fail

I have also tried

ubuntu-11.04-desktop-amd64.iso
ubuntu-11.04-desktop-amd64+mac.iso

This seems really strange. I'm sure I'm not the only person trying to do this under os 10.6.
Maybe I broke my mac in some way. Any insight or suggestions as to how to proceed gratefully received.

My optical drive died a long time ago so the bootable usb root is my only option.

---

### Post by jonas2012 on 2012-06-10
Have you tried refit? It is an alternate EFI thingie. Something like a bootloader only for macs.

---

### Post by robotlovesyou on 2012-06-11
Hello

I'm pretty sure refit wouldn't help my particular problem. The issue I am having is with the installation iso images which are not mountable, and therefore create unbootable disks.

---

### Post by tlucyk on 2013-01-09
having the same problem with ubuntu 12.10 iso on osx 10.6.8

---

