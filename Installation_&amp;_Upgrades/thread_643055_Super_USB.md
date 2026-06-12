---
title: "Super USB"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by freakalad on 2007-12-17
Hi guys,

I've been scouring the net for some info for a project I want to start, and I'd like to get your input. (Let me know if this is the wrong forum/section for this).

The idea is to have as complete a working system as I can get onto a USB flash drive.
Ideally, I'd like to implement the following features:
*  Live USB (ref: USBuntu, Linux Pen Drive)
*  Separate my /home/mymobileuser into a separate partition to protect it from FUBAR's, ease of backup
*  Separate vfat/FAT32 partition for my regular flash-disk stuff available to all OS's (docs)
*  Implement a OS-independent VM, such as QEMU
*  Shared persistent user environment. Can I realtime-synchronise multiple open sessions? (optional bonus)
*  Centralised automated backup/sync of profile (only /home?)
*  Do all mounting by volume identification, as USB could be plugged into any port/hub at any time

The idea is to have everything I need on a portable drive:
If I get to a machine (presumably an x86), I want to pop in my portable media & be ready to rock & roll. Could work as as live boot option, or log into a linux box & load my profile (mount cheat?), start it in a VM on Win/Mac, or simply access my common shared partition on simpler devices (such as my home theatre). Of course, I'd like to have stuff backed up to my central server regularly, so as to recover from 'bad crashes' or some such. Ideally I'd like access to my Thunderbird mail & FireFox links & add-ons/profile wherever I go. Also some 'security tools', like those found on the Backtrack2 distro

I have a few machines that I'd like to (k)ubuntuwise: MacBook Pro (will have to wait for now), Asus Eee 701, PS3, Multimedia 'server'/storage/streamer, a couple of work laptops (running win @ moment)

Some stuff to look out for is to do away with swap-space avoid/minimise constant disk writing when hosting from the USB, as this wears the flash media out (something I did not know before). I know this will impact performance, but data preservation is more important at the moment.

If all goes well, I'll probably implement it into my iPod 5G, as this is disk-based, and usually carry it with me (luv doze tunez). We'll see.

Now, I've seen most of this info scattered all over the web, but hope to bring this together into a single reference

Your 2c worth would be appreciated

- J :guitar:

---

