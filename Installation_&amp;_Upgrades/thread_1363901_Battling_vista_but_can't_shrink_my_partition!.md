---
title: "Battling vista but can't shrink my partition!"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by Karmatose on 2009-12-25
Hi guys, sorry if this is a duplicate thread.

I'm trying to install ubuntu so i can dual boot and forget vista except when i want to use windows' excel, and game.

I'm having problems shrinking my laptop harddrive to partition it; even though I have 100g out of 180g free, I can shrink my C: drive by 30 gig. This reduced to 0 gig after following instructions I scraped from the internet which should have fixed the problem.

Here's what I've done so far:

-Cleared and disabled shadow copies, hibernation files (I think) and pagefile
-Disabled kernel memory dump
-Deleted pagefile.sys
-Defragged ~3x each with Power Defragmenter, Auslogics Disk Defrag, and Perfect Disk 10.

After following these steps I was actually able to shrink my drive by LESS, not by more, as promised by the various forums around the internet.

The one thing I can think of is that PD10 hasn't moved the remnants of the pagefile and MTR (MRT?) files away from the end of the harddrive. I tried to do an offline defrag as suggested, but PD10 can't get exclusive access to the C drive even after rebooting. CHKDSK has similar problems. Maybe something is preventing access pre-boot, but I don't run Zonealarm (which apparently causes problems) and I've disabled f-prot... still no luck.

Any help you can offer would be great at this point. I'm dying to say goodbye to vista, please, help me!!!

Oh, and merry christmas all, seeing as it's that day ;-)

---

### Post by raymondh on 2009-12-25
Why not just use the "guided-resize' option and use the slider to allocate partition sizes?

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Happy holidays as well.

---

### Post by oldfred on 2009-12-25
It sounds like you have done all the things I have seen suggested. While it is still best to use the Vista partitioner you can use gparted if it is a newer version and uncheck the round to cylinders checkbox.  Old windows and linux partitions start at 63 but Vista & 7 start at 2048. After resizing with gparted be sure to boot it at least twice to let it repair itself. If you do it as part of the install you have to reinstall windows to the MBR to let it run the checkdisk repairs, and then reinstall grub.

The following article by the How-To Geek contains useful information regarding resizing your Vista partition, and getting it to boot again.
Using GParted to Resize Your Windows Vista Partition 
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

Herman on Gparted old error and not in Ubuntu but still recommends Vista partitioner for safety:
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)
starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

---

### Post by Bartender on 2009-12-26
Then there's the "jump out of a perfectly good airplane" approach.  Make your Vista recovery discs, wipe the drive clean, create a primary NTFS partition the size you want for Vista, format the rest of the drive as an extended partition (the last three steps can be done from a GPartedLiveCD), then reboot with the first of the Vista recovery discs in the tray.  Vista installer will see the NTFS partition but not the extended partition.  So you install Vista to the primary NTFS partition and the rest of the drive is ready for Ubuntu.

---

### Post by Karmatose on 2010-01-05
Thanks for the response guys.

Yeah I'm a bit dubious about using non-vista partition devices from what I've read (which has basically been "don't use linux partitioners or vista will throw a hiss). 

That said I'm not in the know with this kind of thing at all, so if you guys think it's cool I trust your opinions.
One thing that would be ideal is if I can reinstall windows at the end of the driver (I read somewhere that this is where it's slow, and I'd rather have my primary OS operating at max, so better to instal ubuntu first). I don't know ANYTHING about recovery discs, but if I wipe the drive, can i use recovery discs i make to reinstall vista on the tail end of the drive, after installing linux? I don't have the original vista cd, as my laptop came with...

---

### Post by Bartender on 2010-01-05
If you don't have Vista recovery discs created from the original manufacturer's installation because it came with XP, and you don't have access to a genuine Vista disc, ignore my suggestions.

I've read posts where people say they want this OS or that OS in the outer half of the drive where it'll go faster, and I've read others who said the difference is not enuf to worry about.  I imagine what you propose is technically feasible, but I'm also quite sure the vast majority just install Windows first and don't worry about it.

---

