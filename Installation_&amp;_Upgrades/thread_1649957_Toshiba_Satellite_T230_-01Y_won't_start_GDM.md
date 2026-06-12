---
title: "Toshiba Satellite T230 -01Y won't start GDM"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by BobSongs on 2010-12-20
I'm having a bit of difficulty installing Ubuntu on a Toshiba Sattelite T230 -01Y. Note: if any particulars about this machine are required, I'll be happy to add them.

This laptop does **not** have an optical drive: no DVD, no  CD-ROM. I used a USB memory RAM stick (4Gb) upon which I've installed  Maverick through System > Administration > Startup Disk Creator.

The installation seems to work well. I cut the hard disk (roughly  250 Gb) into 3 partitions: 20 Gb for the system, 2 Gb for Swap, the  remainder for /home. The whole setup works as it would on any other PC.

Once the setup is complete and the system reboots, it never actually  seems to get GDM going. I'm left at a command prompt login. If I leave  it long enough (a few seconds), I get a listing that appears over the login prompt, spewing info at me. It sort of resembles the following:

[ 29.296206] rtl8192_SetWirelessMode(), wireless_mode:10, bEnableHT = 1
[ random number] ====>rtl8192_set_chan_()====ch:1

and ch:2, ch:3 to ch:13.

Eventually, regardless whether I use the keyboard or not, some kind of  screensaver sets in and I can't see any more input-output.

If I hit the power button, oddly: the background goes purple displaying CLI characters momentarily, notifying me that the system's going to halt... and the system halts.

Any way I can get this going? Do I require the Optical Drive instead of  using USB to install the system? I'm afraid all NTFS partitions have  been wiped away as the client insisted they wanted nothing to do with  Microsoft products.

**Note:** when installing I ask it not to update during the installation as I've had poor results with that. If you feel I should give that a try, I will.

---

### Post by BobSongs on 2010-12-21
I've tried changing the file system from Ext4 to ReiserFS ... just for the heck of it.

No change. Still unable to get Gnome Display Manager to start up.

Same error messages.

I wonder if it was a mistake for my client to buy Toshiba.

---

### Post by sikander3786 on 2010-12-21
You didn't need the ReiserFS. Ext4 would be a better choice.

We need to know a few hardware details for the machine in question. Specially RAM, Processor and Graphics Card.

In the mean time, from Bios screen, press and hold down Shift key until you see the Grub menu. Highlighting the first entry, press 'e' to edit it. Navigate to words "quiet splash", delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot and see if it takes you to the desktop this time.

Otherwise, we need to know about hardware specs.

---

### Post by BobSongs on 2010-12-21
I'm not trying to avoid answering this post. ;)

I've kinda got some success . . . but not entirely

Here's what I've done so far. I've done some research on this crazy laptop. Seems getting its specs are a challenge. Anyway, here's what Ubuntu says about this machine:

**Hardware**
Memory: 2.9 Gb
Processor 0: Intel(r) Pentium(r) CPU U5400 @ 1.20 GHz
Processor 1: Intel(r) Pentium(r) CPU U5400 @ 1.20 GHz

**System Status**
Available disk space: 274.5 GB

There used to be an applet in System > Preferences or System > Administration that told you all kinds of info about a PC. Seems this has been stripped from Maverick. I'm trying to locate the vid card for this box, but nothing yet.

I've tried following these instructions:
> In the mean time, from Bios screen, press and hold down Shift key until  you see the Grub menu. Highlighting the first entry, press 'e' to edit  it. Navigate to words "quiet splash", delete them and type "nomodeset"  in their place (without quotes). Press Ctrl + X to continue boot and see  if it takes you to the desktop this time.
The result is ending a long list of CLI commands ending with a CLI login prompt.

**Note:** when I booted using the Recovery Mode kernel and selected Low Graphics Mode, the system booted to a graphics mode that ran fairly well.

I'm in it now and updating the system with the very latest kernel, etc, hoping that will help.

---

### Post by BobSongs on 2010-12-21
Solution!

Once the system was booted into safemode, I applied an update (this brings the system up to Linux Kernel 2.6.35-24 and...? Success!!

The problem is that this machine's graphics card is probably not listed in the kernel on the setup CD. However, the latest kernel has the correct drivers. The system booted up correctly and I'm beginning the long, arduous process of installing favourite software.

Thanks for the tip on holding down the Shift key while booting. My main PC dual boots between XP and Maverick (yes, Ubuntu's my #1 system, falling back on XP for only the occasional use). So the GrUB screen always comes up.

Thanks! I'll mark this thread [Solved]

---

### Post by sikander3786 on 2010-12-22
Glad to know it is finally sorted :-)

> I'm trying to locate the vid card for this box, but nothing yet.

From Terminal,

```
lspci | grep VGA
```

And if Nvidia or ATI, you might need to activate the drivers from System > Administration > Additional Drivers as that might improve the performance.

Happy Ubuntu-ing1

---

### Post by BobSongs on 2010-12-22
> **sikander3786 said:**
> ...From Terminal,

```
lspci | grep VGA
```
Sikander, you're a gem! Here's what lspci says when I grep VGA:
> 00:02.0 [COLOR=Red]VGA[/COLOR] compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)I think this is why there was an issue. Neither ATi nor nVidia graphics cards, but one created by Intel.

Having spoken with the owner, this little Toshiba Satellite T230 was meant to be a gift for someone who wanted an iPod. But the notion of paying a bit more for a complete (or fairly complete--less the optical drive) laptop was considered an upgrade.

Apparently this is becoming the trend: laptops without optical drives with the option to download Windows software through some kind attempt at a pay-for repository. I asked the owner how one would go about installing stuff one already has or sliding in a music CD to make MP3s of one's own music...

Oh well. None of my business. :p

---

