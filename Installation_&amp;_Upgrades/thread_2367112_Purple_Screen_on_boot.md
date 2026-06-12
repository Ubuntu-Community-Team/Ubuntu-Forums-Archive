---
title: "Purple Screen on boot"
date: 2017-07-26
forum: Installation &amp; Upgrades
---

### Post by bradon on 2017-07-26
Hi guys,

I'm having a problem since I tried to install Linux on  my new laptop. At the beginning I though it was a simple one (I read a  lot of topics regarding this problem), but nevertheless I didn't find  any solution so far.

First of all: I bought some weeks ago this  Laptop: Acer TravelMate X349. which came with Intel HD Graphics 520 as  Graphic adapter (without a dedicated graphic card) and the processor  Intel i7-6500U. The operating system was Windows 10 Pro 64 bit.
After  a couple of weeks I've really got upset using Windows, so I decided to  get totally rid of it and put Linux as I already did in the past with my  old laptops. 

The first distro I downloaded was Manjaro 64bit  (Arch Linux based). Anyway, with the Secure Boot option disabled I was  not able to install it due to the black screen on the boot (after the  grub), and the same happened with Antergos 64bit (Arch-Linux based too).  I read some articles about the problem, but I decided to try Linux Mint  64bit before, just to see if I would have got the same problem. Here  the first successful step (I burned the ISO with Rufus on Windows 10 as I  did with the other distros): I could boot the live version of Mint and I  also installed it! I got rid of Windows totally and the result was 3  partiton: 
dev/sda1 35MB EFI Partition
dev/sda2 500GB Mint
dev/sda3 8GB Swap

I  got some problem in order to get the Grub (I added grubx64.efi as  trusted UEFI file from the BIOS) and then, when I tried to boot Linux  Mint...black screen again!

I tried today with Ubuntu and, of course, the behaviour is the same, I can run the live version, I can install it, but after the grub I get the purple screen! (It's curious that I can at least install these distros but with the Arch-based distros I get the problem before).

I thought it was a graphic problem, I  tried almost everything I found here on this forum regarding the grub  options (i915.modeset=0, nomodeset, grub_gfxmode, acpi=off, etc.).  Honestly I think that this is not a graphic problem but something else  and I was not able to figure out what it is. One really curious thing  from my point of view is that when I try to boot it in recovery mode the  system hungs on "Loading initial ramdisk", so I cannot even boot it in  recovery mode.


Does anyone of you have any suggestions?

---

### Post by BenginM on 2017-07-26
Which ubuntu version you tried to install with the liveusb/cd .. The hanging can be caused by many things. ..! So you;ve tried disabling modesetting (KMS) ... are there other media devices atached beside the live us/cd .. you may want to try addin' kernal debug options ignore_loglevel is particularly useful and shows how far the boot actually got. or earlyprintk=efi

[URL="https://www.kernel.org/doc/Documentation/admin-guide/kernel-parameters.txt"]https://www.kernel.org/doc/Documentation/admin-guide/kernel-parameters.txt

[/URL][https://wiki.ubuntu.com/Kernel/Debugging](https://wiki.ubuntu.com/Kernel/Debugging)

---

### Post by bradon on 2017-07-27
> **BenginM said:**
> Which ubuntu version you tried to install with the liveusb/cd .. The hanging can be caused by many things. ..! So you;ve tried disabling modesetting (KMS) ... are there other media devices atached beside the live us/cd .. you may want to try addin' kernal debug options ignore_loglevel is particularly useful and shows how far the boot actually got. or earlyprintk=efi

[URL="https://www.kernel.org/doc/Documentation/admin-guide/kernel-parameters.txt"]https://www.kernel.org/doc/Documentation/admin-guide/kernel-parameters.txt

[/URL][https://wiki.ubuntu.com/Kernel/Debugging](https://wiki.ubuntu.com/Kernel/Debugging)

Yesterday I firstly fixed that using the acpi=off parameter (I don't know why I wasn't working before, but probably I used it in a wrong way). But, then, I got a lot of problem regarding WiFi, Touchpad, and so on...

At the end, I figured out the most simply workaround to the problem: installing the 32bit version.

---

