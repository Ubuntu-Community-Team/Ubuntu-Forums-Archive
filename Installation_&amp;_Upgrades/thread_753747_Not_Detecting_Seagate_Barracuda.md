---
title: "Not Detecting Seagate Barracuda"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by Ocarina654 on 2008-04-13
I have a Seagate Barracude 7200, 750GB.  When I attempt to install the installation cannot detect the hard drive.  I know the hardware is plugged in and running properly because a Knoppix Live CD detects and can write to the drive.  FreeBSD can also see and write to the drive.
I am using the 7.10 Alternate Install CD.

Any ideas, suggestions, or help on what I can do to get this working?

Thanks in advance.

---

### Post by Lantesh on 2008-04-13
I don't know if your drive falls in with this series of drives or not, but if it does you may be in for a serious headache.

[http://www.theinquirer.net/gb/inquirer/news/2007/12/06/seagate-snubs-linux](http://www.theinquirer.net/gb/inquirer/news/2007/12/06/seagate-snubs-linux)

By Nick Farrell: Friday, 07 December 2007, 7:30 AM

SEAGATE'S latest batch of drives, the ironically titled Free Agent series are not compatible with the Open Sauce operating system Linux.

As an INQ reader, who owns two 320s and 500s (USB2) pointed out to us, Seagate designers must have been working overtime to manage that feat. Linux runs his ancient Arcnet card, the latest DVB-c/s/t cards and even the more obscure studio-grade A/D/A converters. It cannot manage the latest from Seagate.

The problem is to do with the power-saving systems on Seagate's latest range of drives and the fact that it is shipped already formatted to NTFS.

The NTFS is only a slight hurdle to Linux users who have a kernel with NTFS writing enabled or can work mkfs. But the "power saving" timer is a real bugger.

It will shut shut the drive off after several minutes of inactivity and helpfully drop the USB connection. When the connection does come back it returns as USB1 which is apparently as useful as a chocolate teapot.

As our reader points out this is a, "fairly **** idea perfectly implemented, " unfortunately while Windows can handle it, Linux and Mac's can't cope.

There are a few work-arounds but Seagate Tech Support says they do not know what they are. Instead they are telling man plus dog that their latest drives do not support Linux.

Rose Allen from Seagate Tech support said that work-rounds may succeed, but there is no way that she, or her band will support that sort of thing.

---

### Post by Ocarina654 on 2008-04-13
As scary as that would be, thankfully my drive isn't one of those.  It works with BSD, at least, but I'd much rather use Ubuntu because I actually kinda know what I'm doing in Ubuntu.

---

### Post by Ocarina654 on 2008-04-14
Well does anyone know anything about not detecting hard drives, regardless of make?

---

### Post by TMC on 2008-04-15
> **Lantesh said:**
> SEAGATE'S latest batch of drives, the ironically titled Free Agent series are not compatible with the Open Sauce operating system Linux.

My apologies for hijacking this thread, but I have a workaround for the FreeAgent.  As the problem occurs because the drive spins down after 15 minutes of inactivity, just set up a cron job to access the disc periodically.  I've tested this by dir'ing a directory on my FreeAgent every 5 minutes and it works.  Bit of a dirty hack, but I don't care - it works!  :)

David Shaw

---

