---
title: "using a Mypassport usb hdd for ubuntu 18.04"
date: 2020-07-19
forum: Installation &amp; Upgrades
---

### Post by justnip on 2020-07-19
i have been trying to install 18.04 on  a western digital usb ext hdd (mypassport)
never got it to boot on the my HP laptop which is what i want, but it did boot on my other desktop pc just fine
laptop has windows 10 and i don't want the ubuntu on the internal drive so i got the usb
every time i get through the installation it never boots up i tried many variations of partitioning also
booted the live user dvd in uefi , and used the efi for the bootfiles, yet when i attempt to boot i always
 get the grub bash command screen. How do i resolve this issue?

---

### Post by TheFu on 2020-07-20
Some of the initial Passport USB devices had incompatible USB devices that needed a seldom used USB driver.

The standard USB boot issue solutions are:
[LIST]
[*]try a different port on the same machine. Often, USB2 ports work better than USB3 for some machines.
[*]not all USB devices support booting. Have you checked whether your specific model does in the specs?
[*]ensure there is sufficient unallocated/free space on the device; that includes the ability to create at least 2, if not more, partitions. They can be primary or logical and the partition table can be either GPT or MS-DOS.  Other partition table types are not allowed.
[*]update the UEFI firmware for the system.
[/LIST]

To begin, probably need to get the USB device number.

For example, lsusb on one of my systems, shows this:
```
Bus 004 Device 005: ID **1058:1140** Western Digital Technologies, Inc. My Book Essential (WDBACW)
```

While on another system, 
```
$ lsusb
Bus 004 Device 004: ID 1058:25fb Western Digital Technologies, Inc. 
Bus 004 Device 003: ID 1058:25fb Western Digital Technologies, Inc. 
```

But I promise the 3 and 4 devices ARE very different to my Linux system.  When I web search using "1058:25fb usb3 boot", it is clear that many other people can't boot from that model USB device either.

Those are my guesses.

---

### Post by sudodus on 2020-07-20
The problem might also be that you installed the system in one boot mode, say BIOS mode alias CSM alias legacy mode, but the problematic computer is booting in UEFI mode (or vice versa). Please check if that is the problem! There are ways to fix that problem, but we must know the problem before we can fix it.

---

### Post by ActionParsnip on 2020-07-21
If the file system is NTFS then be sure to run a full chkdsk on it in Windows to make sure the file system is complete and consistent

---

