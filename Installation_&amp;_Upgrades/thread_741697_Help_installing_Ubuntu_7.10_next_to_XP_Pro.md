---
title: "Help installing Ubuntu 7.10 next to XP Pro"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by thrice upon a time on 2008-04-01
Hello,

First, I tried search, but could not find this issue. Please forgive me if this is due to my ignorance or if I did not search correctly :confused:

I have Windows XP Pro, and am trying to install Ubuntu 7.10 next to it, dual boot. However, I have tried twice, and have run into problems both times, and am asking for advice. 

I have installed Ubuntu to dual boot with XP Home in the past with no issues. But, I just purchased XP Pro from a friend who just bought Vista, and it's giving me pains compared to XP Home. Unfortunately, my work pretty much requires some version of Windows at this point for a couple of programs. I'd install XP Pro in Virtual Box, but am concerned about how that works with Ubuntu upgrades, including the coming Hardy, in only a few weeks. So, onto the issues -  XP Pro appears to keep a partition at the beginning of the hard drive, seperate from XP partition, as a fat-32 format. I deleted that, thinking it was accidental free space, as I had not seen that in XP Home, moved the NTFS partition to the left, and installed Ubuntu. After that, Ubuntu did not recognize that XP Pro was there. 

I tried adding XP Pro to grub, but I only got error messages trying to boot into it. I inserted the XP Pro cd, and tried everything I could think of. I eventually tried even just saving my XP Pro install (thankfully I have backed up all of my data!), but after running fix /mbr, bootcfg, fixboot, etc.... I still could not even get it to boot at that point. It said "ntloader not found". I copied ntldr from the XP Pro disk, and it overwrote a copy on the XP Pro partition, which made me wonder again about the fat partition that XP Pro had installed. 

Twice I have tried this. The second time, XP Pro somehow detected my "backups" partition as an "unidentified" OS, put on it's own sort of GRUBish thing, and that caused some havoc as well :-(  Has anyone installed Ubuntu next to XP Pro and can give any advice or tips? 

Any advice, thoughts, tips, and/or know-how DEFINATELY appreciated!

---

### Post by JLB on 2008-04-01
It is normally the same as a XP Home install. The FAT partition you saw at the front should have remained there.  The deleting and moving most likely wiped the NT loader and thus made it invisible to GRUB.  It was most likely a diagnostic partition or a recovery partition. Probably the best course of action (as well as most expedient) would be to wipe the drive and reinstall your XP Pro and just select however many GB you want that XP partition to be during the setup. Once installed, pop in Ubuntu and install alongside of it. Smart move that you backed up your XP documents. You get a cookie for that one :)

---

### Post by thrice upon a time on 2008-04-01
Thanks mate. I have some free time tonight. I'll give that a shot - and leave the fat partition alone as well ;-) Thanks for the cookie :lolflag:

---

### Post by thrice upon a time on 2008-04-01
Goofy but true ending to this story:

I had formatted my "backup" partition to fat-32 to make it easily readable by both Windows and Ubuntu.

It turns out that XP Pro puts all of it's important files, in that partition, and leaves a re-director on it pointing to "F:\" drive, which is where XP Pro names it's partition. Installing Ubuntu geeks up it's scheming or redirection or something, somehoworother. 

I cannot for the life of me make XP keep it's system and .ini files in it's native partition :-( Simply copying or cut'n'pasting doesn't work, using the map command doesn't work, in fact nothing seems to convince Windows it doesn't need to store it's boot info on my "backups" partition. I suppose if I got REALLY motivated one day, I could make the backup partition in ext3, and just use Ubuntu to transfer the data once installed, so that XP would be blind to it, but for now I've had it with Window's inherent stupidity. The fat partition it makes at the beginning of the drive is empty, unnocupied, btw. It's use I cannot determine ATM except that it's just wasted space :confused: 

So, I think I'm just going to upgrade to Hardy now, then install Vbox and put XP Pro in it :D Dealing with the odd bug here and there certainly can't be as bad as dealing with actual Windows :lol:

Thanks for the help, again!

---

