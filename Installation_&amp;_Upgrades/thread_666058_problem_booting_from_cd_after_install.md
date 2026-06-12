---
title: "problem booting from cd after install"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by johns747 on 2008-01-12
I am relatively new to ubuntu, and have encountered two problems on install.  I installed ubuntu on a second harddrive, and have the grub boot loader installed.  (xp is on the first drive)  Problems:  (1)  The installation worked fine, but I have discovered that I can no longer boot from a cd.  I have set, and re-set, my bios to set the cd to boot first, and even tried changing the order in which the hard drives will boot.  I have read many other threads, and have found a few others with this issue.  It appears to be an issue with the grub loader.  (2) wireless network set up is unsuccessful.  I have a linksys (broadcom) card.  Pretty standard, and recognized by the os.  When I check to see if it's "on", it reports as disabled.  Wireless manager doesn't see it.  I think this must be simple, but I note others have similar issue.

---

### Post by tgalati4 on 2008-01-13
What version of Ubuntu did you try installing?

Also, post the output of:

>lspci -vv

and

>lsmod

---

### Post by johns747 on 2008-01-13
I installing 7.10.  in response to lspci -v, i get a summary of my hardware config.  in relevant part, it includes this: (the ethernet, and then the wireless card)

lspci -v

01:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: FIRST INTERNATIONAL Computer Inc Unknown device 9016
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at c400 [size=256]
        Memory at ed003000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 20000000 [disabled] [size=64K]
        Capabilities: <access denied>

01:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Linksys WMP54GS version 1.1 [Wireless-G PCI Adapter]  802.11g w/SpeedBooster
        Flags: bus master, fast devsel, latency 32, IRQ 19
        Memory at ed000000 (32-bit, non-prefetchable) [size=8K]

lsmod yields a long list of values, which in relevant part includes this (I believe bcm43xx is the broadcom driver):

bcm43xx               127336  0 
ieee80211softmac       31360  1 bcm43xx
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ieee80211              35656  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  1 ieee80211

---

### Post by tgalati4 on 2008-01-13
Here's something to try:

From a terminal:

>sudo modprobe bcm43xx

This reloads the broadcom module.  Sometimes it's tricky.  Also if it doesn't work, then you might need to load ndiswrapper and use a Windows driver.  Search the forum and you will find quite a few things to try.  The AirForce one is a troublesome card to set up but it generally works well once it is set up correctly.

Concerning GRUB, it will have problems if the CD drives are not listed in a particular order.  Look at the file:

>cat /boot/grub/device.map

Be sure it matches your actual device listing.  This can be found by:

>cat /etc/fstab

It should look something like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cca0328e-de95-435f-8587-4f7fe0a1f3a2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0a41cdc2-508c-406d-ab5c-125c20ab129f none            swap    sw              0       0
**/dev/scd0**       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


On my system the CD is located at device scd0.

My device.map looks like:

(hd0)   /dev/sda

You can add devices like:

(hd1) /dev/scd0
(hd2) /dev/scd1

You will have to figure out what your devices are called and GRUB needs a clue as to what they are called by reading device.map.

---

### Post by johns747 on 2008-01-15
Thank you very much for your fine advice.  The Linksys broadcom card is indeed troublesome, but I was eventually able to get the Windows driver to operate with ndiswrapper.  The GRUB problem was, in some respects, more interesting, because it gave me an opportunity to become more familiar with the OS file structure.  Simply coordinating the device map brought the CD back to life.  Brilliant.  Again, thanks for the advice.

---

### Post by Mr. Joe on 2008-01-15
well, if you are using an external hard drive with a usb connection, your bios may be booting automatically to usb before trying anything else (in my experience, this setting is seperate for the boot order).

You may have to unplug your external in order to boot a cd (thats what i have to do)

no worries though, as soon as it starts reading the disk you can just plug your hard drive back in.

At least thats my situation for the time being. I really think if you unplug it and start, it'll work fine.


Good luck!

---

