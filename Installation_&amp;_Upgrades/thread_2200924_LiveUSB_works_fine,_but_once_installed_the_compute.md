---
title: "LiveUSB works fine, but once installed the computer won't boot"
date: 2014-01-21
forum: Installation &amp; Upgrades
---

### Post by Cley Faye on 2014-01-21
Hi,

I'm trying to install kubuntu on an "old" laptop (~6 years old). It had a working kubuntu installation of 10.4 that have never seen an update, so I thought installing 13.10 would be the "easy" route.

Image downloaded from [http://www.kubuntu.org/getkubuntu](http://www.kubuntu.org/getkubuntu), 13.10 64-bit

When I boot on the LiveUSB media, everything's fine. I can try kubuntu, open a web-browser... however, once installed on the harddisk the computer won't boot. GRUB shows up, followed by the kubuntu logo start glowing in the middle of the screen, which then **freeze**.

Now, although no linux guru I've checked a few things:
- Installation don't use any special partitions layout: only one harddrive, 80GB, installation set to automatically use all the disk.
- This is not a GRUB installation/configuration issue: the GRUB menu does show up, the kernel and it's ramdisk are found and loaded.
- This is also not a "no root mount point" issue; it just isn't this error message.
- Trying the "recovery mode" doesn't work; it however show a nice kernel panic (longer than the console so I don't know how it begins). After a while I get watchdog spilling some more messages about the CPU cores being dead. At this point, nothing respond (the keyboard does nothing at all, I can't switch numlock etc)
- Editing the boot command line, I added some flags that used to help on this computer (namely "noapic", "nolapic", "nohpet") and disabled the splash screen by hand (removing "quiet" and changed splash to "nosplash" just to be sure). It still hang at the same point
- Booting on the LiveUSB again I checked which kernel was installed. I don't remember exactly (sorry, left the computer with my relatives) but the exact same kernel version used on the LiveUSB was installed on the harddisk.

I'm baffled. The installation was done offline, so it had only the packages present on the LiveUSB installation media. On a whim I tried another installation, connecting the laptop to internet and enabling updates at installation time. It did download quite a few packages, but when the installation ended and the computer restarted, same issue.
I don't even know what to check. There don't seem to be any useful logs left on the harddisk (checked while booting on the LiveUSB). I can somewhat see in the kernel panic stack trace references about cfg80211, but since the module load and works properly on the LiveUSB, I'm not sure if it is relevant.
I also tried a 13.4 install with the same result. Only thing left for me is to try a 32-bit installation, but it just feel weird, as I *know* a 64-bit linux system used to work fine.
So, I don't even know what to look for. No logs, no useful informations on console (there don't *seem* to be any error before the kernel panic... or it's too fast to be seen), and a supposedly similar kernel/software packages works when loaded from an USB key. I'm open to all suggestions for a fix (or just somewhere to start :) ).

---

### Post by tfrue on 2014-01-22
Try and install boot-repair to see if it can automatically fix your problem. If it doesn't try and re install boot repair, but post the boot-info url here so I can help you troubleshoot

---

### Post by mastablasta on 2014-01-22
what about nomodeset boot parameter?

if you hit Esc (or do it with no splash screen) where does the boot stop? what is the last line?

what are system specs (CPU, GPU..)?

---

### Post by Cley Faye on 2014-01-23
Still no progress; here are the informations about the system:

CPU: AMD Turion64 X2 Mobile Technology TL-60
GPU: ATI Mobility Radeon Xpress 200
RAM: 2GB
LAN: Broadcom NetXtreme BCM5788
WLAN: Broadcom BCM4311

You can find more detailed info here (all obtained on the LiveUSB system for obvious reasons):
dmesg output after boot: [http://paste.ubuntu.com/6802532/](http://paste.ubuntu.com/6802532/)
cpuinfo: [http://paste.ubuntu.com/6802527/](http://paste.ubuntu.com/6802527/)
free mem: [http://paste.ubuntu.com/6802526/](http://paste.ubuntu.com/6802526/)
lspci: [http://paste.ubuntu.com/6802525/](http://paste.ubuntu.com/6802525/)

Using nomodeset don't help unfortunately. The last informations visible on the console is not that helpful either, as you can see in these two pictures: [http://imgur.com/a/oBJR7](http://imgur.com/a/oBJR7)
(note that the second picture happen roughly 30 seconds after the first, despite the kernel timer saying otherwise!).
If the image fail to load, the first picture contain what looks like a stack trace, some registers and the message "Fixing recursive fault but reboot is needed!". The second picture is just another (different) stack trace.

[B]boot-repair
[/B]I also tried boot-repair, as suggested, from the LiveUSB. It produced the following reports:
- Initial (before repairing): [http://paste.ubuntu.com/6802463/](http://paste.ubuntu.com/6802463/)
- After repairing: [http://paste.ubuntu.com/6802477/](http://paste.ubuntu.com/6802477/)

I don't see anything wrong in there; and in fact the repair option merely changed the boot entries' labels from french to english.

Finally, I tried another set of boot option (by hand): "acpi=off nomodeset xforcevesa", it still hang at the same point, with the same error.

I'm gonna try the 32-bit installation (as soon as the download complete), but I'm not convinced that would work either, as I don't know why a perfectly fine kernel boot on USB and crash on HDD :(

---

### Post by tfrue on 2014-01-23
It also tried to reinstall Grub to /dev/sda, and /dev/sda2 does not contain a valid MBR code, so that partition probably needs to be formatted but I'm not sure what FS you have on it as I don't remember which has the ID of 5. Boot repair also tried to unhide the boot menu entries for 10 seconds.

You might should try and use a live CD rather than the USB, it might yield better results. If anything I would reformat the entire drive, then live boot and when you get to the partitioning part of the installer, choose use entire disk so Ubuntu can automatically do what it needs to do. I've never really cared for unetbootin anyway since it destroyed one of my USBs... :/

Good luck,
Chris

---

### Post by mastablasta on 2014-01-23
64bit is fine that's not the issue.

an obvious one but did you check the md5sum of the downloaded image?
how did you create the USB? Ubuntu had some changes in how the files are named and not all USB creators incorporated them (but then again you said you can boot live session just fine).

Radeon opensource driver doesn't have good support for that card, but agian you could boot live. however i can't get rid of this feeling liek osmething is missconfigured on install. or recognised wrongly on boot.

can you maybe get into recovery conosle and access the boot logs? that should show exactly where the boot stops. EDIT: nevermind - use live session to access this data instead of recovery.

---

### Post by Cley Faye on 2014-01-23
> **tfrue said:**
> It also tried to reinstall Grub to /dev/sda, and /dev/sda2 does not contain a valid MBR code, so that partition probably needs to be formatted but I'm not sure what FS you have on it as I don't remember which has the ID of 5. Boot repair also tried to unhide the boot menu entries for 10 seconds.

You might should try and use a live CD rather than the USB, it might yield better results. If anything I would reformat the entire drive, then live boot and when you get to the partitioning part of the installer, choose use entire disk so Ubuntu can automatically do what it needs to do. I've never really cared for unetbootin anyway since it destroyed one of my USBs... :/

Good luck,
Chris

Regarding /dev/sda2, it's the extended partition. At install, I did choose "use entire disk", and that's how it layout the system: one main partition taking all disk minus 4GB, and an extended partition containing a single swap partition. That's odd, but that's how it roll ;)

The problem with using a CD rather than an USB is, well... having a spare DVD and a DVD burner. These things disappeared for me for quite some time. On the other hand I had no problem with USB boot (even today... the USB stick *does* boot fine, that's part of the problem ;) )

> **mastablasta said:**
> 
[COLOR=#000000]64bit is fine that's not the issue.[/COLOR]

[COLOR=#000000]an obvious one but did you check the md5sum of the downloaded image?[/COLOR]
[COLOR=#000000]how did you create the USB? Ubuntu had some changes in how the files are named and not all USB creators incorporated them (but then again you said you can boot live session just fine).[/COLOR]

[COLOR=#000000]Radeon opensource driver doesn't have good support for that card, but agian you could boot live. however i can't get rid of this feeling liek osmething is missconfigured on install. or recognised wrongly on boot.[/COLOR]

[COLOR=#000000]can you maybe get into recovery conosle and access the boot logs? that should show exactly where the boot stops. EDIT: nevermind - use live session to access this data instead of recovery.[/COLOR]


No recovery console, and using the live session, /var/log (on the harddisk!) didn't have anything remotely looking like a kernel log. It probably crashed before it could even write them :\

In the end, I did give up and try a 32-bit install of Kubuntu 13.10, same source ([www.kubuntu.org]("http://www.kubuntu.org")), same procedure (install, use all disk, let the installer do his stuff), and it works. Seeing that a 13.4 64-bit install also failed to start, I'm kinda guessing there's something wrong in some legacy module, when built in 64-bit ABI :(

To sum it up:
- "simple" install 13.10 64-bit: kernel panic on boot
- "simple" install 13.4 64-bit: kernel panic on boot
- "simple" install 13.10 32-bit: boot fine, sound and wifi works, etc...

Unfortunately, this is a relative computer, so getting it up and running was the priority (and it's somewhat achieved, although it's not perfect). But there seem to be some discrepancies between the 32-bit and the 64-bit version of (k)ubuntu. I know for a fact that 10.4 worked fine, but somewhere among the line it got borked :(

Anyway, thanks for the suggestions; as I won't be able to "experiment" more on this computer to narrow it down, it will probably remain an unsolved mystery :confused:. It would probably take an ubuntu-installer expert to know the minute difference between a live boot and an installation boot (as far as I looked, there's no difference in kernel boot options, and I stopped here).

---

