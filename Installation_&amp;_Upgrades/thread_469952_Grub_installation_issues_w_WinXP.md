---
title: "Grub installation issues w/ WinXP"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by HunkirDowne on 2007-06-10
[SIZE="3"]Recovering Windows addict seeks shelter in Linux halfway house.[/SIZE]
(I'm getting back into Linux after having set my hobbyist tendencies aside for a while.)

I have recently recovered from a hozed grub setup.  No emergency here, but I'd like to know how to...
...(1) make this happen less and
...(2) recover more gracefully next time.

I'd like to think that as soon as I wean myself off of WinXP I won't be munging Grub as often.  But until I do, I'm thinking of repartitioning to make my system a little more resilient.  Tell me if I'm off base.

_My current config_:
/dev/hda1: ntfs winxp
/dev/hda2: extended
/dev/hda3: debian
/dev/hda5: ubuntu ce
/dev/hda6: ubuntu
/dev/hda7: swap

_Proposed_:
/dev/hda1: /boot/grub (can this be FAT/DOS with FDISK /MBR somehow?)
/dev/hda2: ntfs winxp
/dev/hda3: extended
/dev/hda5: ubuntu ce
/dev/hda6: ubuntu
/dev/hda7: swap

(1a): Just going into winXP didn't hoze my grub.  I've gone there before without this happening.  But I had a raw partition and decided to format it when I was in XP and I'm thinking *there's my sign*; XP will want to report the newly formatted partition and that means an MBR write, right?

(2a): Recovery for me was a two-step procedure: (2a1): using DOS, "fdisk /mbr" and (2a2): using ubuntu 7.04 desktop "live", install where recently formatted xp partition was.

(2a1-gripe): Why do I not have a Linux equivalent of the veritable DOS FDISK /MBR function?  Could it be that one exists and I don't know about it?

(2a2-question): I've recently read several posts about Grub and realize that I might have been able to use my Ubuntu Live CD to reinstall Grub.  This appears to be a decent routine but I have not tested it except for the ID part which follows.
[FONT="Courier New"]
[B]$ sudo grub
grub> find /boot/grub/stage1[/B][/FONT]
(grub will report the location as (hd#,#) indicating the disk and partition of the location.
[FONT="Courier New"][B]grub> root (hd#,#)
grub> setup (hd#)
grub> quit[/B][/FONT]

My output of "find" was:
[FONT="Courier New"] [B](hd0,2)
 (hd0,4)
 (hd0,5)[/B][/FONT]


...but which do I choose?  I'm guessing any one that contains the menu.lst I like the best, right?  I realize that with the easy installs nowadays, the automagic installer will not look for another /boot/grub on the system and go ahead and install one off of root.  But could I build a rescue partition with just Grub and some essentials on it?  If I can't get a Linux equivalent of FDISK /MBR I'd want to format it from a DOS boot floppy (Win98 or WinXP) but would I then be able to install Grub?

If this was a desktop, I wouldn't go through the rigorous procedure I've set out for myself, but this is a laptop and the more I carry on the hard disk the better.  (I still haven't been able to boot from a USB yet).

**Finally,** if you've made it this far you are almost as masochistic as I am so maybe you know the best primers for Xorg (Debian gdm issues) and Grub and the like.  I am very fond of two Linux books in my collection, both O'Reilly books: *Linux In a Nutshell* and *Running Linux*, but these are somewhat outdated.  If you have a good reference book that complements the man and HOWTO pages, please let me know.

**One last question:**
I used to [FONT="Courier New"]**mount -t ext3 /dev/hda1 /mnt/hda1**[/FONT] but now I [FONT="Courier New"]**mount -t ext3 /dev/sda1 /media/sda1**[/FONT].  I realize I can (and sometimes still do) mount to /mnt but the sometimes rather arbitrary-ness of /sda vs /hda has me a little curious.  As far as I know, my IDE HDD doesn't go SCSI on me when I reboot.  But then this* is *the Twilight Zone.

---

### Post by logos34 on 2007-06-10
> I've recently read several posts about Grub and realize that I might have been able to use my Ubuntu Live CD to reinstall Grub. This appears to be a decent routine...
Yep, '....setup (hd0)' -- that's the routine (or from your mounted root partition, 'sudo grub-install (hd0)'. 

> My output of "find" was:
(hd0,2)
(hd0,4)
(hd0,5)

...but which do I choose? 

I would think (hd0,5), which is /dev/hda6 (ubuntu), assuming it was the last to be installed (in which case its menu.lst and fstab files will contain entries for all the other OS's parititons)

> If I can't get a Linux equivalent of FDISK /MBR I'd want to format it from a DOS boot floppy (Win98 or WinXP) but would I then be able to install Grub?

You can make a [grub boot floppy]("https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28grub%29"), and/or get [SuperGrub CD]("http://supergrub.forjamari.linex.org").

> the best primers for Xorg (Debian gdm issues) and Grub and the like

**[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)**
> 
I used to mount -t ext3 /dev/hda1 /mnt/hda1 but now I mount -t ext3 /dev/sda1 /media/sda1. I realize I can (and sometimes still do) mount to /mnt but the sometimes rather arbitrary-ness of /sda vs /hda has me a little curious. As far as I know, my IDE HDD doesn't go SCSI on me when I reboot. But then this is the Twilight Zone.

The standard mount directory is now /media, but you can mount them wherever you like I guess.  Have yet to sort out the deal with ide drives being called 'sdx' -- something to do with the devs porting the ide subsystem over to libata, the highly successful scsi subsystem, and merging them in a libata-pata driver to handle both. All I can say is when I did a test install of Feisty on another drive recently I didn't notice my pata drive showing up as 'sda' before or after the update to from 2.6.20-15-generic to - 16 kernel.

check this out:
[https://launchpad.net/ubuntu/+spec/libata-for-all-ata-disks](https://launchpad.net/ubuntu/+spec/libata-for-all-ata-disks)

---

