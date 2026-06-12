---
title: "After Feisty upgrade: Kernel 2.6.20 doesn't find hard drive"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by Putzlappen on 2007-04-26
Hi there,

tried to solve this in the German forums already, to no avail. So here's your chance to prove that those bloody krauts don't know a thing :-D

I recently upgraded from Edgy to Feisty and everything seemed to go just fine, until the reboot with the new kernel 2.6.20-15: I was greeted with the familiar Kubuntu loading screen and its progress bar - just that the progress bar didn't move a bit....  so I switched to the console and just stared at...

```
Starting up...
Loading, please wait.
```

...and after a looong time of waiting this was added:

```
[  80.982506] ata 5.00: failed to set xfermode (err_mask = 0x40)
[  95.892554] ata 5.00: failed to set xfermode (err_mask = 0x40)
[ 131.002613] ata 5.00: failed to set xfermode (err_mask = 0x40)
    Check root= bootarg cat /proc/cmdline
    or missing modules, devices: cat /proc/modules   ls /dev
ALERT! /dev/sda7 does not exist. Dropping to a shell!
```

...and then it falls back to BusyBox :-(

A quick "cat /proc/partitions" just showed an empty list.

Luckily, I still got the Edgy kernel (2.6.17-13), otherwise I couldn't post this. Doesn't play much of a role if I try the 386- or generic kernel, the result stays the same. Edgy kernel seems to work fine with Feisty, though.

On a side note, even the vanilla Edgy kernel did not work 100% out-of-the-box on my machine: I had to manually patch the sources and recompile to activate support for the onboard ethernet chip. I really had high hopes that with kernel 2.6.20 I wouldn't have to rely on such desperate measures anymore :-(

So here's what I've already tried after going through previous forum posts:

1. Try to use the initrd from kernel 2.6.17 with 2.6.20

...all that has changed after trying this was that I'm getting different (and mostly, more of them) error messages, that also indicate that no discs were found.

2. Make a new initrd using yaird

...tried that using the 2.6.20 as well as the 2.6.17 kernel config, both not yielding any better result

3. replace all UUIDs in menu.lst and fstab with the trusty old /dev/sda...-entries

...and again, nothing, nada, nix, zilch, zip. No visible change.

4. Boot from Ubuntu Live-CD and try copying its kernel to the hard drive

...nice plan, but unfortunately the live system doesn't recognize the hard drive as well, so no copying from A to B here. Maybe I should have tried the live cd before upgrading? Naah, ssssh... don't be silly :-D

Now to my system: I've got a Core2Duo on a Foxconn P9657AA-Board, with only one single SATA-disc attached as well as a DVD-drive  via IDE (which seems to be properly detected, so it seems to be the SATA controller this time).

Here's the output of lspci, executed under 2.6.17:

```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
00:1f.6 Signal processing controller: Intel Corporation 82801H (ICH8 Family) Thermal Reporting Device
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
02:00.0 IDE interface: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMB361 AHCI/IDE (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4364 (rev 12)
04:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
04:03.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
04:03.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
04:03.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
```

And here are the relevant entries from my menu.lst (I'll spare you all the old kernels :-)):

```
##### First the new, defunct kernels from Feisty Fawn:

title           Ubuntu, kernel 2.6.20-15-386
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-386 root=/dev/sda7 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-386
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-386 root=/dev/sda7 ro single
initrd          /boot/initrd.img-2.6.20-15-386

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/sda7 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/sda7 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

### And here's the old self-compiled kernel from Edgy:

title           Ubuntu, kernel 2.6.17.13-ubuntu1
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.17.13-ubuntu1 root=UUID=a345d7ad-a74f-41e2-9b1d-6720a392de96 ro quiet splash
initrd          /boot/initrd.img-2.6.17.13-ubuntu1
quiet
savedefault

title           Ubuntu, kernel 2.6.17.13-ubuntu1 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.17.13-ubuntu1 root=UUID=a345d7ad-a74f-41e2-9b1d-6720a392de96 ro single
initrd          /boot/initrd.img-2.6.17.13-ubuntu1
```

...and because I'm just getting warm and nobody shall tell me I didn't provide enough information, here's my fstab, too:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
#UUID=a345d7ad-a74f-41e2-9b1d-6720a392de96 /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7   /   ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=A0041E7B041E551E /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda1   /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
#UUID=81797d88-9271-47ed-905b-cdba633d3e86 none            swap    sw              0       0
/dev/sda6   none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

# For the scanner to work:
none /proc/bus/usb usbdevfs auto,devmode=0666 0 0

```

It doesn't really make a difference here (or in the menu.lst) if I use UUIDs or the old device entries.

Well, I don't know what more I can do anymore... maybe someone can give me a clue about what to try next?

CU 
 Markus

---

### Post by John Jason Jordan on 2007-04-26
> **Putzlappen said:**
> 
3. replace all UUIDs in menu.lst and fstab with the trusty old /dev/sda...-entries
...and again, nothing, nada, nix, zilch, zip. No visible change.

<snippage>

It doesn't really make a difference here (or in the menu.lst) if I use UUIDs or the old device entries.
Ever since nearly a year ago when I upgraded Breezy to Dapper every single upgrade has messed up my menu.lst file by making it point to hda3, which does not exist on my computer. Somehow it conjures up a UUID for a non-existent partition. I've tried to get to the bottom of why it does this, but have had no luck. However, in my case at least I know that right after a kernel upgrade it is not going to boot until I go into menu.lst and change the partition it is pointing.

So my suggestion is to use tune2fs to verify that the UUIDs in menu.lst are correct:

sudo tune2fs -l /dev/hda2 <change "hda2" to your device>

If that doesn't help, I have no other suggestions. I just thought I would mention it since you seem to be grasping at straws.

---

### Post by Putzlappen on 2007-04-28
Problem solved thanks to the German Ubuntu forums - the krauts aren't that useless after all :-)

The secret is to add the option "irqpoll" to the kernel boot options in your menu.lst. After that, all works fine and the hard drives are magically found :-)

:guitar:

---

### Post by Dominus on 2007-05-04
Hi all,

Im trying to solve the same problem, but it doesn't work even with "irqpoll" solution.

I left my /boot/grub/menu.lst if you find any differences.

     title		Debian GNU/Linux, kernel 2.6.20-15-generic
     root		(hd0,4)
     kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/hda5 ro quiet splash irqpoll locale=es_ES 
     initrd		/boot/initrd.img-2.6.20-15-generic
     boot


Thanks ...

---

### Post by strikeback03 on 2007-05-04
> **Putzlappen said:**
> Problem solved thanks to the German Ubuntu forums - the krauts aren't that useless after all :-)

The secret is to add the option "irqpoll" to the kernel boot options in your menu.lst. After that, all works fine and the hard drives are magically found :-)

:guitar:

Same problem, also with  a Foxconn P9657AA-8EKRS2H and an E6600, 2 SATA hard drives and one SATA DVD-burner.  In general I can't boot the installed Feisty, can boot the LiveCD with the "all_generc_ide" option.  How do I edit my menu.lst from the LiveCD?

---

