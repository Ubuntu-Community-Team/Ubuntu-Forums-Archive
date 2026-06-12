---
title: "SCSI Detection Holding Up Boot Process- Help!"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by dreck345 on 2007-05-07
For the past three days I have desparately been trying to install Ubuntu Feisty on my desktop PC. I burned both Edgy and the Feisty alternate CD, both of which work on my other computers. Unfortunately, it simply REFUSES to work on my main desktop!

I will say that Edgy works absolutely fine. Unfortunately an upgrade to Feisty causes a freeze during every boot

System specs:

2.65ghz P4
P5PL2 Motherboard
ATI Radeon x1300
40gb/160gb segate HD attached via IDE to a PCI ITA1812 attachment (motherboard doesnt use IDE, needed a way to connect them to the motherboard, so I used the ITA1812 PCI card)
I also have a CD-RW and CD-RW/DVD combo attached to an IDE on the same PCI card.

I have ALSO tried the installation with only one device attached to one separate IDE cable.

Using the standard LiveCD it just gives me the cryptic "tty job control turned off" error that I simply could not troubleshoot after exhausting the forums.

Using the alternate CD- well, I didnt get the job control turned off error. Instead I took out the 'quiet' in the boot options and saw the text boot process.  It ALWAYS halts the boot process after:

sdb:
sd 4:0:1:0: Attached scsi disk sdb
sd 4:0:0:0: Attached scsi generic sg0 type 0
sd 4:0:1:0: Attached scsi generic sg1 type 0
scsi 5:0:0:0: Attached scsi generic sg2 type 5
scsi 5:0:1:0: Attached scsi generic sg3 type 5

The installation will then just hang.

I have tried every single possible combination of noapic nopci=off...I forget them all now. But I have tried them. Every single variation of anything having to do with 'pci' and turning it off or on or sideways- it doesn't matter.

I'm typing this on my laptop with a perfect Feisty installation- help me get it on my desktop!

---

### Post by phidia on 2007-05-07
I read your post several times. It seems like either ubuntu doesn't support the pci card for hard drives (unlikely) or there is something wrong with the master slave jumper settings. Check your jumpers on those drives and also the bios settings.

---

### Post by dreck345 on 2007-05-08
Hmm, you know, I never actually checked my HD jumper settings before- err, well, at least in awhile. Could be worth a shot. Thanks for the suggestion, I'll get to it and post in the morning.

---

### Post by QwUo173Hy on 2007-05-26
I'm having simliar problems so I'm curious, how did it go?

---

### Post by dugald on 2008-01-30
I am having the same problem.  If I add "single" to my grub boot options it seems to boot fine, although I have to press Ctrl-D during boot to continue.

What happens in "normal" boot mode that doesn't happen in "single" boot mode?

In "bootlogd" I changed BOOTLOGD_ENABLE=No to BOOTLOGD_ENABLE=Yes, but /var/log/boot is stilkl empty so I can't post me boot logs.

---

### Post by dugald on 2008-01-31
I seem to have got it working now.  I noticed that my FAT and NTFS drives were not mounting correctly when I logged in with recovery mode, so I booted into Windows and did a full scan disk (inc surface area) for both drives.  A few problems were picked upp by this and now I am able to boot Ubuntu correctly (without recovery mode) and both win partitions mount correctly.     :guitar:

Hope this helps - its at least worth a try.  I know that there is a linux equivalent of sacndisk for FAT partitions but I'm not so sure that it can handle NTFS.

---

### Post by dugald on 2008-02-01
Okay, so that wasn't the problem.  It went back to its old ways.  A few more observations (I am no expert but this is what I have noticed):

[LIST=1]
[*]I have two drives, one sata, one ata, both of which the system recognises as scsi drives (sda and sdb).
[*]Ubuntu boots straight from a Suse GRUB menu.
[*]My NTFS and FAT partitions never seem to mount cleanly or at all.
[*]Sda and Sdb seem to swap over some times..?
[*]When the system locks up on boot at "Attached scsi generic.." it hasn't locked up - if I attach or unplug USB devices it recognises this on screen.  It just seems not to have been told to boot properly.
[/LIST]

I made the following changes and now everything seems to work:

[LIST]
[*]Booted using the recovery mode (or adding "single" to the boot options)
[*]Changed fstab such that the trailing numbers after my FAT and NTFS drives were zeros rather than 1s.  After this these partitions started mounting reliably.
[*]Did a fdisk -l as root and made sure the sda/sdb listings matched up correctly with my fstab.  They were the wrong way round.
[*]Changed Suse's /bott/grub/menu.lst so that the Ubuntu entry for "kernel" changed from this:

kernel /boot/vmlinuz-2.6.22-14-generic 
root=UUID=85ed2279-7249-4815-af1d-7c297499b6aa 
root=/dev/disk/by-id/scsi-SATA_WDC_WD4000AAJS-_WD-WCAPW0327715-part6 
ro quiet splash

To this:

kernel /boot/vmlinuz-2.6.22-14-generic 
root=UUID=85ed2279-7249-4815-af1d-7c297499b6aa 
ro quiet splash

(I took out the second "root=" - best to [COLOR="Red"]copy[/COLOR] the original entry and then make changes to it)
[/LIST]

It now seems to boot without any file structure problems and has been mounting my other partitions correctly.

Once again, these are just my totally uninformed observations.

---

