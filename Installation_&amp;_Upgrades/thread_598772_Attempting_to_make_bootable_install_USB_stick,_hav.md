---
title: "Attempting to make bootable install USB stick, having problems"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by hoborocket on 2007-10-31
I am following the directions here:

[https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html)

I format my USB drive as a single FAT16 partition. I do zcat boot.img.gz > /dev/sdb1 as directed. I do install-mbr /dev/sdb1.

When I try to boot from it on the target system, it gives me "operating system not found". The BIOS does support booting from USB, and I have tried the same USB stick on other systems with the same results.

What do I do?

---

### Post by hoborocket on 2007-10-31
I have attempted this with multiple USB drives, with the same results. Has anyone actually done this that could maybe point out what I'm doing wrong?

---

### Post by hoborocket on 2007-10-31
Bump. Installing via PXE netboot has come up as an option, but the wiki articles on it are a bit over my head.

Using this: [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

I can get the target system to attempt to netboot, but it gives me TFTP timeout errors. I'm entirely stuck as to what to do now, though I'm pretty sure I need to reconfigure something somewhere.

---

### Post by hoborocket on 2007-10-31
Would it be too much for one person to attempt to help me with this? I've really tried to provide as much info as I can, and figure out what I can with my limited knowledge.  I have a computer that won't boot because UNetbootin locked up after eating the MBR, and poor documentation is preventing me from making a bootable USB stick.

I know the stick is bootable and I know my system can boot from it, because I got it to boot with Super Grub Disk, but there's no grub to fix so SGD can't do anything.

I have followed every guide I could find regarding installing Ubuntu from a USB flash drive TO THE LETTER. Then I went through and did them all again to make sure I did it as directed. Then I tried them all with another flash drive. None of them produced a drive that any of my systems would boot from.

I tried setting up another Gutsy box to be netbootable, and netbooting from that, but I hit the limits of my knowledge and the guide on the wiki just confused me.

I swapped the drive into another laptop and tried to mess with it with a Gutsy live CD, but Gutsy won't even detect the drive.

Short of buying a USB optical drive, which would take at least a week to get here, I have no idea what to do.

At this point I'd be happy to just get it booting into windows, at least that WORKED.

---

### Post by kbyrd on 2007-11-09
See my post here:
[http://ubuntuforums.org/showthread.php?p=3738602](http://ubuntuforums.org/showthread.php?p=3738602)

I unziped the boot.img then did dd instead of zcat.

---

