---
title: "The classic...Dual boot with Win 10, windows gets a blank screen and does nothing"
date: 2015-11-24
forum: Installation &amp; Upgrades
---

### Post by timonoj on 2015-11-24
So...Here I am having this issue I thought was long fixed. I had a working Lenovo with a very similar setup, but somehow with my new Dell laptop I'm having issues again.
This is my fdisk -l:
> Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7deb12ef

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048   1026047   1024000   500M  7 HPFS/NTFS/exFAT
/dev/sda2         1026048 211654655 210628608 100.4G  7 HPFS/NTFS/exFAT
/dev/sda3       211654656 460507135 248852480 118.7G 83 Linux
/dev/sda4       460509182 468860927   8351746     4G  5 Extended
/dev/sda5       460509184 468860927   8351744     4G 82 Linux swap / Solaris

And this is what boot-repair did, but without solving the issue:
[http://paste.ubuntu.com/13497748/](http://paste.ubuntu.com/13497748/)

Basically, Kubuntu boots OK, but Windows gets a blank screen when selecting it from Grub. If I use Hiren's BootCd and manually choose the option to boot from the second partition, Windows boots OK, but I'd like the option to work from Grub instead of having to attach a pendrive and go through several options to get Windows to work.

Thank you guys!

---

### Post by oldfred on 2015-11-25
Grub only boots working Windows, or Windows cannot need chkdsk nor be hibernated.
And Windows 10 is always hibernated, if its fast start up is on.

Not sure then why grub cannot boot a hibernated Windows if Hirens can, but Hirens is more Windows like.

       Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by timonoj on 2015-11-25
Thanks! I found in the end it was a bit more complicated...
The Windows install was an image from an old MBR partition. Restored to a GPT partition. A cluster**** ensued with the little EFI partitions at the beginning of the SDD. I spent the whole afternoon yesterday with this...Installed the image now properly to GPT, converted to GPT (macrium reflect solves this easily), then dust off the DVDRW unit so I could boot Kubuntu installer from the DVD so it works in EFI at install, since the USB mode won't. I have now a fully UEFI install, which is what I was aiming for. However it took waaay longer than needed!

---

