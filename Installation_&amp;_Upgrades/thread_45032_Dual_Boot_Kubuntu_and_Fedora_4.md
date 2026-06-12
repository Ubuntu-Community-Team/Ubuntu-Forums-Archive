---
title: "Dual Boot Kubuntu and Fedora 4"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by goldstone0 on 2005-06-28
What is the easiest way to add Fedora 4 as a 2nd OS on my PC which currently has Kubuntu installed? I have a single SATA drive. When I run the Fedora installer, it doesn't see Kubuntu. I'm not familiar with manually adding entries to Grub.

---

### Post by mingus on 2005-06-28
With a simple setup, and no W$, assume you want to install grub to your MBR . . .

Get into Kubuntu, and then do:
$sudo update-grub

then take a look at the file /boot/grub/menu.lst - hopefully there is a stanza added for Fedora

then do:
$grub-install /dev/sda

if you want a failsafe just in the event something goes wrong (it shouldn't), do:
$grub-install /dev/fd0
and
$grub-floppy

the first floppy will also dual-boot your system even if the other fails, and the second floppy starts the grub shell interactively for manually entering boot commands

---

### Post by goldstone0 on 2005-06-29
When I install Fedora, do I need to install a bootloader. I have tried putting it in the boot partition and not installing one at all. I cannot seem to mount the Fedora partition in Kubuntu in order to add the boot entries.

---

### Post by mingus on 2005-06-29
*When I install Fedora, do I need to install a bootloader. I have tried putting it in the boot partition and not installing one at all. *

It depends on the method you are using.  The Debian update-grub script, assuming it finds Fedora, creates a stanza that explicitly points to the Fedora kernel, just like the stanzas for Ubuntu.  In this method, the same installed grub loader is booting both.

The other method is called "chain-loading", where the grub loader hands off to another loader installed elsewhere, e.g., in Windows or in the boot sector wherever Fedora's /boot directory lives.

The second method requires installing the boot loader twice.  The first method integrates the dual-boot process, but changes in Fedora (e.g., kernel update) need to be made in Ubuntu's menu.lst.  Personal preference.

So if the Debian method is OK with you, and #update-grub works as expected, you don't need to install a boot loader in Fedora - Ubuntu's grub will handle it.

*I cannot seem to mount the Fedora partition in Kubuntu in order to add the boot entries.*

Again, if you use the Debian method, it isn't necessary to do this.  However, you should be able to mount that partition from Kubuntu.  We would need specifics on the error in order to answer the mount question.

---

