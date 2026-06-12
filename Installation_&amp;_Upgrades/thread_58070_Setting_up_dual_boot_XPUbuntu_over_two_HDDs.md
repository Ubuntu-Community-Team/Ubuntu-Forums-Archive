---
title: "Setting up dual boot XP/Ubuntu over two HDDs"
date: 2005-08-18
forum: Installation &amp; Upgrades
---

### Post by fluKe_666 on 2005-08-18
Hi, I've already had ubuntu set up and running on an old test machine and I'd like to now install a copy on my main machine.

The setup I have at the moment is a 200Gb SATA drive with XP on it. I would like to keep my ubuntu install on a completely different drive and I have an old 120Gb IDE drive lying around which I thought I would use. I'm pretty certain that I could go ahead and install ubuntu onto the IDE drive and get it up and running but I wanted to check out what the recommended way of doing things is before I have a go.

Ideally what I would like is:

SATA 200Gb >> XP (currently installed)
IDE 120Gb >> ubuntu

Now I rekon it will be easy installing ubuntu onto the IDE drive, just slap the drive in the PC boot from the ubuntu disc and install to the IDE drive. But I would like to be able to have the system running as dual boot (eg. using grub to select between OS).

I would also like to leave the windows install completely alone and not touch anything on my SATA drive at all.


So, when I'm installing will the ubuntu installer see the XP install and set up grub for me? And if so will this work ok? I know I would have to then boot from the IDE drive if I was leaving the SATA one as is, and this is fine. 

I just wanted to check that I can install ubuntu onto a secondary drive, have it detect windows, boot from the ubuntu drive and load whichever OS I want. All without touching my SATA drive at all?

Sorry for the confused post, I'm not knew to linux but I am new to setting up my own dual boot system.

Thanks very much for any help or advice :)

---

### Post by Rogue21121987 on 2005-08-18
I've got my system set up like that-2 HDD, one with XP, one with Ubuntu.

Ubuntu picked up Windows XP fine, and gives you the option of where to install GRUB.  Very easy. :smile:

<edit>Not sure about how it will go with the SATA Drive: give it a try though.

---

### Post by Velox Letum on 2005-08-19
[QUOTE=Rogue21121987]I've got my system set up like that-2 HDD, one with XP, one with Ubuntu.

Ubuntu picked up Windows XP fine, and gives you the option of where to install GRUB.  Very easy. :smile:

<edit>Not sure about how it will go with the SATA Drive: give it a try though.[/QUOTE]
 I've done this as well, however I'm having trouble with GRUB not showing up when I switched the "primary drive" in BIOS to the Linux drive. Windows (after a pause) began loading.

---

### Post by Rogue21121987 on 2005-08-20
My Windows drive is still the primary Drive, and I just put GRUB on that.  Ubuntu is still the default OS that GRUB loads.

---

### Post by pekko on 2005-08-21
I made my dual boot, dual HDD installation like this:

1. Install Windows to Primary drive
2. Switch Windows HDD to secondary drive and Linux HDD to primary drive
3. Install linux, GRUB will install to Linux HDD. Installation should notice windows in secondary drive.
4. Windows does not like to boot from secondary drive so we have to fool it to think it's on primary. This can be done in menu.lst. Take a backup first.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```
Then edit the windows part to be like this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
map		(hd0) (hd1)
map		(hd1) (hd0)
rootnoverify	(hd1,0)
chainloader	+1
```
5. Now you should be able to boot from Linux (primary) drive and select the OS you want to boot.

Benefits:
- Your Windows HDD will not be affected at all by Linux installation
- If you need to re-install windows, just make windows HDD primary drive and install, after that just switch the Linux HDD back to primary drive and that's it.
- If something happens to one of your HDD's, you can still boot from another (Windows HDD still has it's own MBR, just make it primary drive)

---

