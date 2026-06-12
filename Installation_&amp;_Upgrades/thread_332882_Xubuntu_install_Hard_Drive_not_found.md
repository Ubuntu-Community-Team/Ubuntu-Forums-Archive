---
title: "Xubuntu install: Hard Drive not found"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by timski on 2007-01-06
I'm back trying Linux again. My last attempt some 6 or 7 years ago got bogged down in partitions I didn't understand and hardware that wasn't supported, so I went back to Windows. I'm trying Xubuntu 6.10 on a 6 year old laptop (433MHz Pentium Celeron/192MB RAM/12GB HD), installed via an .iso/DVD.

I can start up the OS fine. It finds my network (router/internet, at least). It even finds a USB memory stick. But it doesn't find the hard drive. This, understandably, prevents full installation.

The machine had Windows 98 installed until fairly recently. It was quick formatted (format c: /q) to wipe the old OS. The drive itself contains bad sectors, probably picked up over years of being physically thrown about. These sectors never prevented the previous OS from operating. Before loading up, Xubuntu flagged up handful (5-6) of these sectors before loading the main GUI. It didn't stop, so I assume they are not fatal.

Are there any tools available to help find/fix/reformat my hard drive - presumably something outside of Xubuntu itself? Please assume no knowledge of the operating system.

Edit: The disk is listed by name under /dev/disk/by-label in the File Manager, but isn't being recognised as a partition-able or accessible disk.

Edit a bit more: Initially I had an "unable to locate RSDP" error too, but that disappeared using some combination of acpi=off apm=on irqpoll pci=irqbios in the boot options. But that didn't help find the disk. The sector errors mentioned earlier are all "[numbers] Buffer I/O error on device hda, logical block 4".

---

