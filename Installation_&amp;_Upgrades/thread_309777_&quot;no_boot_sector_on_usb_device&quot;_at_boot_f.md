---
title: "&quot;no boot sector on usb device&quot; at boot from usb flash"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by lewinb on 2006-11-30
Hi, I sure hope someone here can help with this.
I'm trying to put a bootable linux on a Sandisk cruzer 1GB.
I've been able to duplicate this problem with both a ubuntu and slax-killbill usb install. I followed both sets of install instructions for flash drive explicitly. When I reboot, I press F12 to load the boot menu. I choose USB device from the list, and I get the message "no boot sector on usb device". This displays twice, then the computer defaults to windows on the hd.
this is on a Dell Latitude laptop.

My guesses: the computer is trying to read this as a superfloppy, and thus is looking for "bootsect.bin"; or the "boot" setting I make using fdisk isn't working.

Oddly, if I remember correctly, I was able to get puppyos to boot from the usb flash drive.

Many thanks in advance for all help!](*,)

---

### Post by lewinb on 2006-12-01
I took this to a Costco this afternoon and tried the flash usb that I had (supposedly) put ubuntu on, on the computers there. I got the same result on both HP and Compaq tower systems as I had on the Dell laptop. Later this evening, I tried installing both Ubuntu and Fedora to an external usb hard drive. Both installations went fine (after I just let the installer use the entire disk), but when I rebooted and tried to boot from USB device, I ran into problems. On both systems, Lilo loaded, and the system seemed to be booting. But in the middle of the boot, it hung with these as the last few lines:

```
/bin/sh: can't access tty; job control off
(initramfs) [17179579.54000] usb 5-6: new high speed usb device using ehci_hcd and address 2
[17179574.804000] usb 5-6: configuration #1 chosen from 1 choice

```


I tried every configuration possible, but grub would absolutely *not* be installed on any part of the usb disk I was trying this on. I had to skip to Lilo.
Does this  sound familiar to anyone?

Many thanks in advance for any expert help!

---

