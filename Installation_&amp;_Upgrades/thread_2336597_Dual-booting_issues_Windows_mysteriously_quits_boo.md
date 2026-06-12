---
title: "Dual-booting issues: Windows mysteriously quits booting from GRUB"
date: 2016-09-09
forum: Installation &amp; Upgrades
---

### Post by SagaciousKJB on 2016-09-09
[SIZE=6]!!!!Here's a video that shows exactly what is happening!!!
[/SIZE]

[https://www.youtube.com/watch?v=JcVQjXI5rmo](https://www.youtube.com/watch?v=JcVQjXI5rmo)


This is a very interesting problem, and I don't really know where the issue and solution is going to end up being, so I am putting it in this forum for now since it seems like it will have the broadest range of expertise that may have ran into this issue...

So I'll try to be brief but descriptive...

What I am trying to do...

Dual boot Ubuntu 14.04.5 and Windows 7 using GRUB 2 on an older ( no UEFI ) DFI LP JR 790GX-M2RS motherboard.

What I have done...

Installed Ubuntu 14.04.5 onto a SATA HDD, configured GRUB to boot off of it
Removed Ubuntu HDD from computer, inserted IDE HDD and installed Windows 7 on it
Used Super Grub Disc to boot back into Ubuntu 14.04.5 after re-inserting Ubuntu HDD
Used Boot Repair to update Grub, adding Windows 7 to the menu

What happened...

Everything went smoothly at first. Windows booted up from the GRUB configuration menu as did Ubuntu, and there were no problems, and much rejoice was had as this hasn't been my experience before.

...then a few days later...

The old problem came back. When I tried to boot Windows from the GRUB menu, instead of the "Starting Windows" loading screen, I was simply presented with a perpetually blinking cursor in the upper left hand corner of a blank screen. Interesting sidenote, Ctrl Alt + Del would not reboot the computer at this point as it would at almost any other stage during the boot process.

The odd quirky bit I have found that "fixes" it...

So I don't remember quite when I discovered it, but during my first forays into dual-booting I had this very problem, and I had left the Windows installation CD in the drive. So the computer would see it and go "Press any key to boot..." but I would just simply not press any key, let GRUB load, and in those instances the Windows loader would work.  However, if I took that CD out, and booted directly to the hard-drive, the Windows loader behaved with the blinking cursor issue I mentioned.

Now it's important to clarify, this last time I configured it all, I paid special attention to having no CD in the drive, but leaving the boot priority in my motherboard as CD > Hard Drive. In the past I theorized that perhaps setting it back to Hard-drive > CD might have made things wonky or something, so I made sure to leave the boot configuration alone this time, made sure no CD was in the drive, and when Windows loaded with that configuration I thought that was the end of that issue.

The blinking cursor nonsense happened again maybe the second or third time I tried booting Windows from grub, so remembering my old solution, I put Super Grub Disc into the CD drive and chose "Detect all OS" option, it found "Windows Vista bootmgr" and I selected that, and Windows started just fine.  This might seem to suggest that it's a problem with the grub configuration file, but as I said, I don't even need to actually boot from a CD, just simply have a bootable CD in the drive as I turn the computer on and then choose to boot first hard disk, and the same grub configuration will magically work whereas if I started the computer with no CD in the drive it would give me the blinking cursor.

So...  What the heck is going on? I am kind of starting to suspect it is not software related at all, and perhaps something to do with my BIOS, or maybe something is happening to the Windows installation after a few times booting up?  I am pretty sure I can actually rule out configuration issues with GRUB, but perhaps there's some other caveat to the way it's installed I am not understanding. I did pretty much let Boot Repair do all the work.

I used Boot Repair to do a Boot Info Summary, so here's the pastebin URL to that...

[http://paste.ubuntu.com/23155473/](http://paste.ubuntu.com/23155473/)

---

### Post by yancek on 2016-09-09
The boot repair output shows that you have windows 7 on sdb1 and that you have windows boot code in the MBR of that 60GB drive.  You can set that drive to first boot priority to boot windows.

You have Grub in the MBR of sda with your Ubuntu install and boot files on sda2.  If you scroll down the boot repair output to the grub.cfg file, you can see that your windows drive/partition is sde1 or in Grub, hd4,1.  Boot Ubuntu and run:  sudo update-grub, watch the output for a windows entry.  This could easily happen if moving drive, changing connectors or ports.

---

### Post by oldfred on 2016-09-09
Drive order is important, if you have more than the common 1 drive system.

I found with older BIOS system, that I had skipped a SATA port. My flash drive when plugged in would be sde, but on reboot would be sdb and every other drive one higher. Same with grub, hd1 became hd2, flash drive was hd1 in grub.

Then with new UEFI system I used first 3 ports, but made the mistake of plugging in DVD as SATA1 with SSD as SATA0 and HDD as SATA2. Then my sdb drive was hd1, in most cases, but not all.

Bottom line, keep all drives in SATA port order and do not change unless absolutely necessary. And then plan on some reconfiguring of grub.

---

### Post by SagaciousKJB on 2016-09-09
> **yancek said:**
> The boot repair output shows that you have windows 7 on sdb1 and that you have windows boot code in the MBR of that 60GB drive.  You can set that drive to first boot priority to boot windows.

You have Grub in the MBR of sda with your Ubuntu install and boot files on sda2.  If you scroll down the boot repair output to the grub.cfg file, you can see that your windows drive/partition is sde1 or in Grub, hd4,1.  Boot Ubuntu and run:  sudo update-grub, watch the output for a windows entry.  This could easily happen if moving drive, changing connectors or ports.
I have tried changing the boot priority to boot it first but it doesn't seem to have an effect. As for the update-grub suggestion, I have done that already and it does show a Windows entry and seems to configure it all correctly.

> **oldfred said:**
> Drive order is important, if you have more than the common 1 drive system.

I found with older BIOS system, that I had skipped a SATA port. My flash drive when plugged in would be sde, but on reboot would be sdb and every other drive one higher. Same with grub, hd1 became hd2, flash drive was hd1 in grub.

Then with new UEFI system I used first 3 ports, but made the mistake of plugging in DVD as SATA1 with SSD as SATA0 and HDD as SATA2. Then my sdb drive was hd1, in most cases, but not all.

Bottom line, keep all drives in SATA port order and do not change unless absolutely necessary. And then plan on some reconfiguring of grub.
Yeah I have ran into this in the past which is why I always disconnect my SATA cables on the drive end. I wonder if they're changing based on when there is a disc present in the CD drive though, as it is a SATA CD/DVD-ROM.

I made this video of the problem just to make everything crystal clear, because I think there might be some misinterpretation of what is happening.  Windows loads, but ONLY if I start the computer with some kind--any kind--of bootable disc first, then load the grub menu.  Here it is on display in 90 seconds...

[https://www.youtube.com/watch?v=JcVQjXI5rmo](https://www.youtube.com/watch?v=JcVQjXI5rmo)

---

### Post by SagaciousKJB on 2016-09-12
Bump

---

### Post by oldfred on 2016-09-12
It seems that most that try to install Windows on any drive other than first drive have issues. And particular if installing with only that drive then plugging in other drives that do not leave Windows as first drive in boot order.

When you install Windows it is first drive or hd0 in grub/BIOS and sda in Ubuntu, not sure how Windows 7 specifically sees it. But Windows thinks it is on first drive. Grub used to and may add a command in boot stanza to swap drive order, so even though BIOS saw Windows as second drive, grub changes entry so when Windows boots it still thinks it is first drive.

But much easier just to keep Windows as first drive using first SATA port or SATA0. 
But if an old PATA drive with other SATA drives, BIOS may not let you set boot order.

---

