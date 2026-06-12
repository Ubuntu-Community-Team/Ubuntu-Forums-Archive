---
title: "Can't boot ubuntu cd"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by billgoldberg on 2007-10-30
I deleted linux from the first partition from my harddrive. Grub gave me error 22. 

After being unable to boot from cd on my new packard bell computer, i installed an new (actually an old one from an old dell demension pc) cd-rom drive.

This time, instead of doing nothing and booting the harddrive (thus giving me error 22) the screen remains black. When i remove the cd, the hard drive loads and produces error 22.

I have tried booting the following cd's without any luck (screen remains black, i think it knows something is in the drive because it doesn't go to the harddrive): ubuntu 7.04, linux mint 3.0, super grub disk, gparted.
All these work on my laptop.

The weird thing however, when i put in an old xp cdrom, it loads! It gets all the way to when i need to select a partition, but then, whatever partition i choose, it says it isn't xp compatible. It does however reads the partition size correctly. When i press enter to install it on the first partition, 
it says somewhere: id0 on bus 0 (something like that). (edit: all the partitions are nfts or is it ntfs?)

Why can't the pc boot anything exept the xp cdrom. The computer is worthless now. If i remove the hard drive, the screen remains black, when i pull the cd out, it says no bootable ... on the drive or something.

Oh, the hard drive is a seagate 250GB sata drive.

---

### Post by Pumalite on 2007-10-30
What are you trying to accomplish and are you dual booting?

---

### Post by billgoldberg on 2007-10-30
I was dual booting with vista home premium. I removed ubuntu and wanted to reinstall it.

When i put in the ubuntu 7.04 cd, the computer wouldn't boot it (it booted and worked on other pc).
No cd whatsover would boot.

Since i removed ubuntu from first partition, grub gave me error 22. So i need to boot reinstall ubuntu to get the pc working again.

Now, with a new cd rom drive installed, it the computer screen remains black and doesn't go to the hard disk (so not giving any grub error). 

Then only cd that seems to work is xp home, but i can't install it to the hard drive since it says xp is incompatible with the partition. (it's formatted to ntfs)

I just want to reinstall ubuntu and get the computer (a new one, just a couple of months old) working again.

---

### Post by It_Was_Luck on 2007-10-30
Grub Error 22 is basically you deleted a Linux Partition so when Grub goes and looks for it its not there. And thats basically what your problem is. I'll asnwer it in two parts.

First off, check your boot-up list, as soon as your computer comes up press either Esc or F8 or whatever (this depends on your computer) this will then bring you to the boot priority menu. Most computers come this way but you need to put CD-ROM first in the list, then HD. 

Secondly, if all your wanting to do is run windows you can do one of two things:
1. If your computer came with a Recovery CD or something pop it in, and it should boot, then go to the command box and type in "FIXMBR" the fill tell your MBR (Master Boot Record) to boot straight into Windows.
2. If you don't have a Recovery CD, burn yourself a SuperGrub Disk, link below. Then boot it and select windows,then fix boot of windows, this will do exactly what tying in  "FIXMBR" will do from a revocery CD.
Heres the site in case you want to read up on it...
[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)
and heres the download link...
[http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2](http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2)


3. If you still wish to have Linux your probably going to want to first, fix your Grub problem, get into Windows, burn yourself another Live CD, unless your other on still works, then boot it, then reinstall Linux. It should work, if not, burn a SuperGrub CD (see links above) and uninstall Grub, then try to reinstall Linux, then it will install a fresh copy of Grub thats not be all "tampered with"


Hope that helped.

---

### Post by billgoldberg on 2007-10-30
> **It_Was_Luck said:**
> Grub Error 22 is basically you deleted a Linux Partition so when Grub goes and looks for it its not there. And thats basically what your problem is. I'll asnwer it in two parts.

First off, check your boot-up list, as soon as your computer comes up press either Esc or F8 or whatever (this depends on your computer) this will then bring you to the boot priority menu. Most computers come this way but you need to put CD-ROM first in the list, then HD. 

Secondly, if all your wanting to do is run windows you can do one of two things:
1. If your computer came with a Recovery CD or something pop it in, and it should boot, then go to the command box and type in "FIXMBR" the fill tell your MBR (Master Boot Record) to boot straight into Windows.
2. If you don't have a Recovery CD, burn yourself a SuperGrub Disk, link below. Then boot it and select windows,then fix boot of windows, this will do exactly what tying in  "FIXMBR" will do from a revocery CD.
Heres the site in case you want to read up on it...
[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)
and heres the download link...
[http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2](http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2)


3. If you still wish to have Linux your probably going to want to first, fix your Grub problem, get into Windows, burn yourself another Live CD, unless your other on still works, then boot it, then reinstall Linux. It should work, if not, burn a SuperGrub CD (see links above) and uninstall Grub, then try to reinstall Linux, then it will install a fresh copy of Grub thats not be all "tampered with"


Hope that helped.

Thanks for the info, but no luck. I use super grub disk all the time, but the cd won't load. The bios is set to boot from cd. Nothing will boot except the xp home cd-rom even the cd's boot fine on other pc's. When i tried to install that xp (the only one that will boot) , it says the hard drive is incompatible. So the computer is useless. I fear that if i buy a new hard drive the same problem will occur.

After many hours searching on google, i found a guy who also had the incompatible hard drive issue with xp. He got it working. He said:
> 
Alright, i found out what the problem was...

Like i said, i have three drives all SATA, two in RaID 0.

As soon as i unpuged the loner... it worked. i partitioned my Raid drives in windows setup and i was able to partition them...

Why ? i dont have a clue...


I only have 1 hard drive and have no clue what RaID 0 is.

---

### Post by Pumalite on 2007-10-30
Vista is a problem. Normally wants the computer for itself and unless you do things a certain way, it won't let you run anything in that computer. Before I'd do anything else I'd try to restore Vista MBR (There must be an option similar to XP in the installation CD). Then I would make sure to use Vista partitioner AGAIN to allocate space to Ubuntu. Then I'd install.

---

### Post by It_Was_Luck on 2007-10-30
Actually I agree with him, Vista might be the problem, didn't Vista come with there own recovery CD?

---

### Post by billgoldberg on 2007-10-30
If i put in the ubuntu cd or any other bootable cd (exept xp home) the screen remains black.

If i pull out the cd, it loads the hard drive and gives grub error 22.

You see the problem, i want the computer working again. If i am not able to boot any cd and the only one that will boot (xp home) isn't able to install itself. My three month old €600 desktop is worthless.

---

### Post by It_Was_Luck on 2007-10-30
If you have another computer in the house you could get risky and pull it out and plug it in as a 2nd HD into another computer then use a repartitioning software to partition the HD so theres nothing on it, then you could reinstall Vista, then just try to install Ubuntu again.

---

### Post by billgoldberg on 2007-10-30
Could it be vista. Vista came preinstalled without any cd's. You needed to make your own recovery disk.

After a week (after partition for ubuntu install) i accidentaly deleted the vista partition, so i used a friends vista cd to install vista.

I'll ask him to lend me the dvd again, but i don't think it's vista.

If i pull out the hard drive, the same issue occurs. The cd's won't boot. The screen remains black, if i then pull out the cd, the computer says nothing is in the computer to boot. 

Again, how is it possible that none of my working bootable cd's will boot, exept an old xp disk.

---

### Post by It_Was_Luck on 2007-10-30
Don't like take this like its 100% percent correct or something, but my only GUESS is that its the HD...

---

### Post by billgoldberg on 2007-10-30
> **It_Was_Luck said:**
> If you have another computer in the house you could get risky and pull it out and plug it in as a 2nd HD into another computer then use a repartitioning software to partition the HD so theres nothing on it, then you could reinstall Vista, then just try to install Ubuntu again.

Since the computer is out of for a week now, i tried that today. However my second computer is a laptop (never will i buy a laptop again, a desktop is superiour in every way), so i went to a friends house. The plan was to pull out his hard drive, install mine, and use super grub disk to repair the vista mbr, so that i was at least able to use the pc again. When i opened his pc, it turned out he had ide hard drive and i had sata, the cables didn't match. I plan going to visit some other friends tomorrow, but all of them have old pc's, so i fear the worst.

---

### Post by billgoldberg on 2007-10-30
I refuse to bring it to a computer repair shop (student, can't miss the money), but i know i will fix the problem, then victory will be much sweeter. 
I think i will even download gutsy instead of reinstalling feisty.
I will even make a little website using gutsy only for the specific problem and solutions if i get it fixed.

---

### Post by Chappy7777 on 2007-10-30
This is like asking if you have your PC plugged in. Meaning, I'm almost embarrased to ask, but since you didb't say you had and no one else has asked, and this won't hurt......

Did you set the BIOS so that the CD is the 1st thing to boot? If so your BIOS boot order should look something like the following.

     1st Boot     CD-DVD
      2nd Boot    IDE Samsung 200Gig
      3rd Boot    Floppy Disk

If you did this great. If not, it's your problem.

---

### Post by billgoldberg on 2007-10-30
Chappy, it is set to boot from cd first.

With the new cd-rom drive, i think it actually recognizes the cd, but it won't load. Just a black screen. When i pull the cd out, the hard drive loads and give the grub error. Xp home however will load from cd. But i can't install it since it says the hard drive isn't xp compatable.

---

### Post by Symmetric on 2007-10-30
Hi there,

I made a [post]("http://ubuntuforums.org/showthread.php?t=595795") here a day ago about a similar sounding problem, perhaps we can pool our resources to try and figure out what's going on here.

If I understand correctly, when you try to boot from a CD your computer falls over - does this happen right at the point when the BIOS starts to boot from CD? i.e. at the bit where it would usually say "Press a key to boot from CD" or something similar.

Also, you mentioned that you can still boot from your WinXP cd - this seems strange. I'm wondering what's different about your WinXP disk. (On my box both the XP disk and Ubuntu will not boot).

---

### Post by Pumalite on 2007-10-30
Get a Gparted Live CD and see if it will boot that.

---

### Post by Symmetric on 2007-10-30
I've just tried the Super Grub Disk, so that makes three different (definitely working) boot disks that don't load on my box.

It does seem to me that the BIOS/motherboard is the only thing that could be at fault here - the content of the HD should not affect the process of booting from a CD drive.

If this is the case, then perhaps flashing the BIOS might be the thing to do.

P

---

### Post by Pumalite on 2007-10-30
Double check your BIOS and make sure CD is set to AHCI or 2nd Master and 'Auto'

---

### Post by Symmetric on 2007-10-31
Thanks for the suggestion Pumalite,

To avoid repeating myself, I'll copy the relevant text from my original post here.

> Hi there,

I tried to reinstall Linux recently, after reinstalling WinXP. I previously had dual boot using Grub - the Linux partitione still exists, but my PC is booting from windows at the moment.

Now to the problem - when I try to boot from a CD, my mobo gets through POST and then says "PRESS A KEY TO REBOOT" at the point it would normally boot from the CD. This happens both with my Ubuntu boot CDs, and with my WinXP cd as well. I have checked the disks in other computers and they are fine. 

I have checked that my boot order is correct, and even tried unplugging the HD that windows boots from.

Any ideas on what could be causing this problem? Are any pieces of hardware other than my mobo and dvd drive involved at this stage of the boot process?

ASUS P4G8X Deluxe motherboard
P4 2.5Ghz
1GB RAM
ATI Radeon 9800Pro
2x DVD writers
2x Maxtor 80GB IDE HDD (one is my Windows disk, one has my Linux partitions)
1x Maxtor 160GB SATA HDD
1x WD 500GB SATA HDD



billgoldberg - can you get your hands on a second hard drive easily? like an old 2+ GB one? I'd say that the suggestion above to try and install XP on another drive might be worth your while.

Do you have stuff on your current hard drive that you want to keep?

Cheers,
Paul

---

