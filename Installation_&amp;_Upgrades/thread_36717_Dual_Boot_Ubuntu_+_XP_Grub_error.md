---
title: "Dual Boot Ubuntu + XP Grub error"
date: 2005-05-24
forum: Installation &amp; Upgrades
---

### Post by Krobar on 2005-05-24
I'm hoping that someone can help me figure out the best way to fix this, I titled it with as many keywords as I could think of as my searches have been...less than fruitful. All of the information I've found with this error applies to either SATA drives or instances where XP is on the second harddrive or second partition.


Situation:
hda has 2 partitions, 1 for winXP system, 1 for Data, both ntfs
hdb has Ubuntu created partitions 

After installing Ubuntu I can reboot and go back into Ubuntu as much as I wish, however the minute I go into XP and reboot something seems to corrupt Grub (or something?) and I get stuck in an infinte loop of rebooting right after the systemtests. The message flies by so fast I can't tell what it says, something about stage1_5 maybe, but the only way to fix it was to reinstall Grub. The problem is that, again, as soon as I go into XP and reboot I lose it again.

I ended up having to reformat the XP partition and reinstall my programs, so where I'm sitting at now is a working XP install that I can get to, and a working Ubuntu install I can't get to. I've tried creating a Grub boot disk from the Ubuntu Live CD with no luck, and I'm pretty much tapped out of ideas and so frustrated that I'm having problems making sense of some of the data I've found. Here's hoping someone here can maybe get me pointed in the right direction. Thanks.

---

### Post by shaunm on 2005-05-24
Hi Krobar 

By no manner of means am I an expert -  but it might be worth seeing if you can copy your /boot/grub/menu.1st file here so it can be compared with others that work. 

Grub uses a different labelling system for hard drives and windows - as far as I know windows really likes being on hda1= (hd0,0)

My dual boot win 98 system looks like this:

I have my first drive partitionedshared with win and partitioned  into /: swap: and /home with / on hda5 = (hd0,4)

So my menu.1st file looks like this:

 
..............................Cut..........................................................................................
 title  Ubuntu, kernel 2.6.10-5-386 
root  (hd0,4)
kernel  /boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash
initrd  /boot/initrd.img-2.6.10-5-386
savedefault
boot

title  Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root  (hd0,4)
kernel  /boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro single
initrd  /boot/initrd.img-2.6.10-5-386
savedefault
boot

title  Ubuntu, kernel memtest86+ 
root  (hd0,4)
kernel  /boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title  Windows 95/98/Me
root  (hd0,0)
savedefault
makeactive
chainloader +1


------------------------------------------------cut -----------------------------------------------------------------------
Good luck

shaun

---

### Post by agds on 2005-05-24
Which OS did you install first?  I've heard that Windows doesn't like playing second fiddle to Linux and will therefore cause GRUB errors if installed after Ubuntu.  On my dual boot system, I installed Windows first and used the installer's partition utility to create a small NTFS partition for Windows plus a large FAT partition to allow for file sharing between Windows and Ubuntu.  I left several GBs unpartitioned.  Then I ran the Ubuntu installer and had it automatically partition the remaining free space.  This has been working well so far.

However, if you have a large enough HD, you may want to leave additional free space in case you want to add more partitions later.  Alternately, you could make a number of small partitions across the entire space.  Of course, you can make this decision for yourself based on how you anticipate using your machine.

---

### Post by GAW-Snow on 2005-05-24
Agds is absolutely right.  I'm a long time user of windows and I know it like the back of my hands.  Windows doesn't like linux or any other OS that is not windows.  

You have to install windows first and then everything else.  Otherwise, windows installation will make your other partitions completely invisible.

---

### Post by agds on 2005-05-24
[QUOTE=shaunm]By no manner of means am I an expert -  but it might be worth seeing if you can copy your /boot/grub/menu.1st file here so it can be compared with others that work.[/QUOTE]
That's a good call, Shaun.  I would provide mine here, but I'm not in Ubuntu right now.  (It's being fussy about HAL and various Gnome applets, but that's another story.)

---

### Post by Krobar on 2005-05-24
Sorry, thought I had said that, I had XP installed first. I'm at the office right now so I can't post my grub menu.lst, but I did explore that when it first happened and if memory serves correct it looks like yours. The Windows portion says:

title Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1


I also changed root to rootnoverify in an attempt to get it to work with no success. As I said, I've since had to reinstall windows and now I can't get to my ubuntu install and frankly I"m a little scared to try to reinstall grub as it was for fear that it'll cause the same problem. I did try 2 different Ubuntu install disks and I installed it about 5 or 6 times in total now. Each time the same problem, I was fine until I went into XP and rebooted. 

And again

hda (hd 0,0) is XP 
hda (hd 0,1)? is my data partition (which is windows only atm as it's ntfs and a dynamic disk)

and 

hdb (hd 1,0) is my ubuntu install and it has the whole 20gb drive to itself.

edit: I've also tried changing my bios settings to Large, LBA, and they're now back to Auto, each had no apparent effect, although I did change both drives at the same time, no idea if that has any effect.

---

### Post by agds on 2005-05-24
It seems like the problem occurs because XP and Ubuntu have been installed on different HDs.  I remember reading about similar issues arising when the operating systems were located on different devices.  Perhaps you could put XP and Ubuntu on the smaller of the two drives and use the other drive to store your data.  I'm not sure that's the most effective solution, though.

---

### Post by shaunm on 2005-05-24
Hi Again

> I'm at the office right now so I can't post my grub menu.lst, but I did explore that when it first happened and if memory serves correct it looks like yours. The Windows portion says:
 
 title Windows XP
 root (hd0,0)
 savedefault
 makeactive
 chainloader +1 

Did you keep the divider in? for non linux systems

 Again this is just an idea but I know some distros are very sensitive about thier config files. Worth a look I supppose.

shaun

---

### Post by Krobar on 2005-05-24
[QUOTE=shaunm]Hi Again

 

Did you keep the divider in? for non linux systems

 Again this is just an idea but I know some distros are very sensitive about thier config files. Worth a look I supppose.

shaun[/QUOTE]
 yes the divider is still there, I don't remember EXACTLY what everything said, just the windows portion as I was suspecting that's where the error was forming.

Unfortunately having both os's on the smaller drive isn't really going to be helpful as it's a really old drive with poor performance qualities (and due to it's age, questionable stability). I guess the only left is to try to create a grub boot floppy and maybe use that to get into Ubuntu when I want to? I'm not sure that it's worth that, I did have FC3 working at one time with this same setup and had no problems other than I couldn't figure out how to access my data partition (turns out that it was because I let XP make it a dynamic disk, something I still need to rectify), but everyone I know who uses Linux was raving about Ubuntu (and installing Ubuntu compared to installing FC3 was dreamy), so I figured I'd give it a whack. :-\

---

### Post by alastair on 2005-05-24
It's definitely not an issue with having Linux on disk2, and XP on disk1. Completely standard and (normally) working. 

If the problem starts once you boot into XP, then reboot - then something XP is doing is affecting the bootloader perhaps. What I don't know.

If you fancy reinstalling Ubuntu, do an "expert" install and, when it asks about installing a bootloader (GRUB) on MBR of hda (or whatever), say "no" - you should then be able to install on a floppy (/dev/fd0).

---

### Post by Krobar on 2005-05-24
[QUOTE=alastair]It's definitely not an issue with having Linux on disk2, and XP on disk1. Completely standard and (normally) working. 

If the problem starts once you boot into XP, then reboot - then something XP is doing is affecting the bootloader perhaps. What I don't know.

If you fancy reinstalling Ubuntu, do an "expert" install and, when it asks about installing a bootloader (GRUB) on MBR of hda (or whatever), say "no" - you should then be able to install on a floppy (/dev/fd0).[/QUOTE]
 alastair I'm gonna give that a try, thanks for your help. 

I didn't think this was a standard problem, and I've no idea why it did it, if it didn't mean reinstalling everything AGAIN I'd be willing to try again with this fresh xp install as I've not even installed a virus scanner yet, just got it patched up offline with my sp2 cd and then got the latest updates (behing a router and with windows firewall on as well of course), as I figure that if anything would be affecting that it would be the AV maybe.

---

### Post by agds on 2005-05-27
[QUOTE=alastair]It's definitely not an issue with having Linux on disk2, and XP on disk1. Completely standard and (normally) working. 

If the problem starts once you boot into XP, then reboot - then something XP is doing is affecting the bootloader perhaps. What I don't know.

If you fancy reinstalling Ubuntu, do an "expert" install and, when it asks about installing a bootloader (GRUB) on MBR of hda (or whatever), say "no" - you should then be able to install on a floppy (/dev/fd0).[/QUOTE]

Thanks for clearing that up.  Just out of curiosity, does GRUB keep a log somewhere?

---

### Post by egibbs on 2005-05-27
I'm running a similar setup with no problems - the differences are I don't have the data partition on hda, and my Ubuntu drive is hdc because it's on IDE channel 2.  It works fine for me.  I also don't use GRUB to boot Windows - I use F12 at boot to select the drive to boot from.  If I select the Windows drive GRUB never loads, and if I select the Linux drive GRUB loads.

A thought - where is GRUB located?  Are you sure it's on hdb and not hda?

Ed Gibbs

---

