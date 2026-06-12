---
title: "No IDE recognition for CDROM (DVD)"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by freekb0y on 2011-03-14
Hello All,

So this past week I have been trying to install Ubuntu 10.10 64 bit on a new machine that I just built.  I am running a Quad core i5 with 4 gigs of ram with an Asus motherboard and Graphics card.  I couldn't boot up until I used the alternate cd and turned off APIC, this finally allowed me to get to at least the installer walk through, but when I get to the CD drive it can't find it.  I have tried going through the documentation for fixing this but it doesn't help.  One of the issues that I encounter is that under the /proc directory there is no IDE subdirectory.  I have used DMESG but it doesn't make mention of the CD-ROM at all or even an attempt to mount it.  I know that it works because I am booting off a DVD drive and it is attached through SCSI.  The Bios recognizes the drive and reports back the manufacturer.  When it comes time for UBUNTU to mount the drive though it does not and asks for where it is mounted which I can not find.  It is not mounted as HDC or SDA/B, believe me I actually went through all of them hoping it was mounted somewhere else.  It is also not under /media or /mnt or /CDROM.  If anyone can offer any help it would be greatly appreciated.

Thanks

---

### Post by andrewthomas on 2011-03-14
How about /dev/sr0?

---

### Post by freekb0y on 2011-03-15
No it did not mount under SR0.  Though by turning of APIC and another option which I don't remember I was finally able to get the cd drive to mount.  I have finally installed it but will have to do it again because it ran the grub boot loader to SDA1 and I am using SDB1 as my install location

---

