---
title: "Live CD does not boot (8.10 x86_64)"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by null_pointer_us on 2008-10-30
I used BitTorrent to download the 8.10 Live CD for x86_64, which was then burned at 1x speed to a new CD-RW disc.

When I booted from the Live CD, I did a disk check. The splash screen ran for a LONG TIME and produced three errors like "end_request: I/O error, dev sr0, sector 143620." Then the disk check started at 0%, ran all the way up to 100%, and said that the disc was fine. Odd.

After rebooting, I picked the Live CD option to boot into the Ubuntu graphical desktop before changing anything on my computer. This option appeared to freeze for 5-10 seconds, after which the splash screen ran for a LONG TIME (again). Finally, the screen started filling up with errors (1 every few seconds) like this:

[x] end_request: I/O error, dev sr0, sector x
[x] Buffer I/O error on device sr0, logical block x

Here is a very similar thread (but the fix did not work for me):
[http://ubuntuforums.org/showthread.php?t=768348](http://ubuntuforums.org/showthread.php?t=768348)

Then I put in my old 8.04.01 Live CD and encountered a very similar problem. The weird thing is that I already installed 8.04.01 from this Live CD months ago, and it's running fine.


My hardware:

Intel Core 2 Duo E8500
Geil 8 GB (4 x 2 GB) DDR2-1000
Abit IP35-E (Intel P35+ICH9 chipset)
sda: 320 GB SATA (Vista)
sdb: 320 GB SATA (TV)
sdc: 120 GB SATA (Ubuntu 8.04.01 LTS)
sr0: SATA DVD writer, model: (TSSTcorp CD/DVDW SH-S183L ATA Device)


Kernel options that did NOT help:

noapic
irqpoll
acpi=noirq
generic.all_generic_ide=1


One other symptom:

When I remove the **quiet** and **splash** boot options, the kernel output continually outputs something about mounting ext3 journal daemon, like several times per second. The screen literally fills up with these identical messages so fast that it took a while for me to see what the other error messages said.

---

### Post by Pumalite on 2008-10-30
Use a good quality CD-R. Do not use CD-RW

---

### Post by dabl on 2008-10-30
> **null_pointer_us said:**
> 

Then I put in my old 8.04.01 Live CD and encountered a very similar problem. The weird thing is that I already installed 8.04.01 from this Live CD months ago, and it's running fine.



It sure sounds like some kind of hardware degradation of your optical drive since you last had it boot a Live CD. Two ideas:

1. Clean the lens on the optical drive, and retry

2. Try booting the Live CD on another computer

One way or the other, you'll learn something.  :)

---

### Post by Hatfield on 2008-10-30
Similar problem.
-Downloaded a Kubuntu 8.10 from a bittorrent directly from the Kubuntu site.
-Burned a LiveCD
-Inserted it into my computer which is already running Ibex RC from about a week ago.
-Did a "Check CD"=no errors
-Tried to run the LiveCD and it's hung up on a thick blue stripe across my screen left to right.

Did a reboot and it worked.

---

### Post by null_pointer_us on 2008-10-30
Pumalite:

The 8.04.01 disc I tried was on a CD-R, but it gives similar error messages, so I think the problem is not media-related. I'll keep your advice in mind for future installations, though.


dabl:

Definitely possible that the SATA drive has stopped working. However, with this same drive, I recently reinstalled Vista and a lot of programs, and I use the drive with my Windows games, so it's hard to believe that the drive has degraded to this point.

Now that I think of it, I suppose it's possible that I used a different drive to do the original 8.04.01 installation. And Fedora did have some trouble booting with this drive attached (although the error messages were completely different).

I'll try the 8.10 disc on a different PC to see what's up.

(ATM I'm using [this guide]("https://help.ubuntu.com/community/Installation/FromUSBStick") to put the 8.10 x86_64 iso on a 4 GB flash drive.)


Hatfield:

I've rebooted many times while trying different boot options, and always the errors are identical. Yours sounds more like a hardware problem (overheating, due to clogged fan? or unstable power?) since it was random.

---

### Post by eyelessfade on 2008-10-30
> **null_pointer_us said:**
> 

[x] end_request: I/O error, dev sr0, sector x
[x] Buffer I/O error on device sr0, logical block x


My hardware:

Intel Core 2 Duo E8500
Abit IP35-E (Intel P35+ICH9 chipset)


I have the same board, and same cpu. I have also seen your error. I only get them when I don't use AHCI, but then again, I never get my cd to boot when using it. :/

I don't think your cd is the problem, because I don't get the error on other computers with the same disk. My guess is the "IP35-E"

Since my 8.10 is working great, upgraded from 8.04 to alpha 4, I haven't tried to fix this to badly.


Oh yeah I get the same error on my gfs compute which also have the IP35-E.

---

### Post by null_pointer_us on 2008-10-30
> **eyelessfade said:**
> I have the same board, and same cpu. I have also seen your error. I only get them when I don't use AHCI, but then again, I never get my cd to boot when using it. :/

I'm pretty sure the IP35-E doesn't support AHCI, but then again maybe that changed with BIOS version or a later board revision. Or I could have missed it. Where are you seeing a BIOS option for AHCI on your IP35-E?

> I don't think your cd is the problem, because I don't get the error on other computers with the same disk. My guess is the "IP35-E"

Yeah, it's probably a BIOS or kernel bug of some kind.

I'm posting this in the 8.10 Live CD, using a USB flash drive and [this guide]("https://help.ubuntu.com/community/Installation/FromUSBStick") (as mentioned earlier) with the UNetbootin program. It's really slick. The flash drive boots the 8.10 Live CD image almost as fast as my 8.04.01 partition installed on the hard drive. The "CD check" completed in less than one minute.

One thing to note is that the IP35-E treats bootable USB flash drives as hard drives, so, **to boot from a USB flash drive, you must actually change the Hard Disk Boot Priority option** so that the USB flash drive appears at the top of the list.

Wow, this is great!

---

### Post by eyelessfade on 2008-10-31
> **null_pointer_us said:**
> I'm pretty sure the IP35-E doesn't support AHCI, but then again maybe that changed with BIOS version or a later board revision. Or I could have missed it. Where are you seeing a BIOS option for AHCI on your IP35-E?
I actually have the IP35 PRO XE, but I saw on one of the IP35-E bios updated that they have updated the AHCI rom. But I may have read it wrong.
And I assumed that all IP35 had AHCI

> **null_pointer_us said:**
> 
One thing to note is that the IP35-E treats bootable USB flash drives as hard drives, so, **to boot from a USB flash drive, you must actually change the Hard Disk Boot Priority option** so that the USB flash drive appears at the top of the list.

Wow, this is great!

So that's how you boot from usb. Never got it to work :/

---

