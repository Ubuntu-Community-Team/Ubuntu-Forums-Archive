---
title: "Ubuntu Studio messed up my MBR and other problems...."
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by funkster on 2008-05-01
Hi there,
so I was a little too curious, or too quick in my judgement that 8.04 would be a no brainer to install.
I downloaded Ubuntu Studio , burnt a DVD (md5 sum is OK) and went on to install it on my spare partition (which I left expressly for the new US). The install went without a hitch (or so it seemed), when arrived at the end GRUB asked to install in the MBR, it properly recognised my WinXP partition and my Linux MINT XFCE was seen as Ubuntu 7.10, so I allowed it to install.
After reboot there's no sign of a new GRUB?WTH? Instead I get back to my GRUB install from MINT. No entry or sign of Ubuntu Studio 8.04? Ok, I'm gonna fix the GRUB install or the 'Menu.lst' from within MINT. But no, now MINT tells me on boot, that there were problems with hda6 (my MINT system) and inconsistent filesystems so fsck tries it's thing and dies with exit status 3, going to reboot the system in 5 seconds. I've seen this before and don't worry, so I get on. Upon reboot, same thing again, of course still no sign of a new GRUB, neither any entry to the existing one and MINT starts the filesystem check on hda6 again, and has to reboot the system in 5 seconds. 

WTH? Now I'm stuck in an endless loop between reboot and system filecheck. This went on at least 10 times before I wanted to throw the system outta my window.

But wait, I still have this SUPER GRUB on a USB stick, on floppy and on CD, so why not give it a try? SUPER GRUB wasn't able to fix my MBR with the 8.04 GRUB install (even though it said it did), so now on reboot I have no GRUB, now Windows bootloader, no nothing? Cool (not)!!! Restart SUPER GRUB, repair MBR again, this time the other way round, fixing the MINT entry, upon reboot I see my MINT back on track. But still not cool at all. I fall back into this endless loop again between system reboots and fsck checking my filesystem and rebooting. So i used my old floppy set of Partition Magic, wiped off 8.04, reformatted the partition in question, rebooted and... still no go.
Fortunately I had created a system Image a few days before, and my home is on a separate HDD alltogether. So I restored my backup and I was back on track, fortunately. That was really a PITA experience.

Why does 8.04 see my PATA HDD's as SCSI? Shuffling around the order of entries in fstab, mstab and menu.lst? I have IDE & SATA drives which are all recognised correctly by any other distro? The only one which caused me also trouble in this regard, was any flavor of SuSE up to 10.2 or so. 
If this has to do with LVM, why aren't I given the opportunity to choose myself if I want this **** or a normal install? Although US is a alternate Install medium, the choices we're given are not quite as comprehensive. Only a few yes/no, put in your name, pswd etc. & the choice of which bundles of software I'd like to install. That's about it.

Really, I clearly don't know if this is a call for help, a rant to get of my chest, or whatever. But I was really angry and mad yesterday evening/night.
I thought the Ubunutu team could surely do better.

Anyway, best regards and don't take it too seriously.

Raphael :(

---

### Post by beebelo on 2008-05-03
Hey,

Two possibilities I can think of:  
1.  Linux Mint is not installed to the MBR, and Ubuntu is? 
2.  You have two different /boot partitions.

Check those items and see what you find.

Was is the result of "fdisk -l" (that's an L), which lists your partitions.?

As for the 'alternate install' version, I haven't done 8.04 yet, but I think you have to select "advanced", and then it'll ask you about everything.  This is especially important if you're trying to do multiple distros, because of the /boot partition.

---

### Post by zvacet on 2008-05-04
Look if [this]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub") can help you.

---

### Post by funkster on 2008-05-12
Sorry for coming back this late, but I didn't think anybody would still bother answering this thread (didn't look very probable after 2 days falling into the nirvany of the forum).

@beebelo: MINT's bootloader is definitely installed into the MBR. 
I think what messed up is the fact that 8.04 uses a diff. hdd naming convention. Where my IDE drives were labelled hda/b/c etc, in 8.04 they're called SDa/b/c and so on.
Now I do also have SATA drives in my PC (in fact 3xIDE+DVD-Burner & 2xSATA), and 8.04 didn't see my drives in the right order, which created this mess (IMHO).

@zvacet: Very useful link, thanks for that mate. ;)

I have solved my problem since then anyway by wiping off Ubuntu Studio and reinstalling "64-Studio". Very fine distro, serving both the 32- & the 64-bit HW users. Way less bloated, more performant, better latency figures OOTB etc. 

While Ubuntu (also the Studio flavor) does a fine job, helping to convert many windows users, and trying to make it as painless as possible, it's too much for my taste. We're approaching MS territory here IMHO, trying to stuff so many things into the distro, and still trying to make it installable/usable on ALMOST any system.       

It defies the 'Raison d'être' for linux somehow.
Anyway, I prefer to stay with a leaner distro and spend some more time learning the system/linux so that I'll be able to tweak my system to my liking.

Thank you both for trying to help.

Regards
Raphael ;)

---

