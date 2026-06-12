---
title: "Troubles installing Ubuntu, weird"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by falfool on 2007-01-30
Hello all,

I'm trying to install Ubuntu on my friend's computer, which is something not new to me, I've installed, and upgraded Ubuntu several times, but this is the first time I see such errors. Here is what I tried and what I got:

1. I installed Ubuntu 5.04 (Hoary) from the CDs I got, just as I did on my own machine, then tried to upgrade to 6.06 (Dapper LTS) but it really didn't go smooth at all. I've done everything in the Howtos for upgrade, everything I've done on my system, but it didn't work. After fetching and downloading over 600mbs from repositories, it failed with a 'dependency error' and i tried apt-get -f install, nothing worked, so I thought of trying a fresh install of 6.06.

2. I downloaded all three isos from ubuntu.com , 6.06 Desktop, Server, and Alternate ISOs, burned them all, with Desktop twice. Here is what happens, when I try to boot up the Desktop or Server versions, it hangs after the "Detecting hardware for CD rom...." phase, giving me an error saying that my CD is damaged or one of the packages are corrupt (I traced a CD defect test, it said "/initrd.gz" is corrupt or missing, so I thought maybe the CDs were damaged or something. I bought a blank CD of a different kind, and burned the Alternate iso, and now another weird error occurs, after "Detecting hardware for CD rom" thing, it says that the CD rom could not be mounted, and if I could insert it again and try, each try takes up to 30 minutes. This is annoying me.

Now the system can't boot even into Win2k, because the GRUB boot loader is all messed up, I can't do, or undo, anything.

And by the way, I've installed 2 CD drives, thinking maybe the problem was with the reader, but I doubt it.

I'm really looking forward for any kind of help, thanks alot for your time.

-Ahmad

---

### Post by mizar001 on 2007-01-30
Th GRUB is messed up ? weird behavior. Your upgrade has some several errors, and the updating of grub was destructive.

To restart windows you can boot from the windows cd and restore the boot partition (FIXMBR is the command to restore).

But when you install a fresh ubuntu distro, and you do update , it's not better to install directly the updated version ? well i see you already done.

See the system specs of the computer. If you are in a singular situation with less than 200MB of  RAM you could see those errors, and the solution is to install the alternate distro or xubuntu.

---

### Post by falfool on 2007-01-30
Thanks for the fast reply,

Well, I tried installing from all ISOs, and the latest version with no need for upgrading. I have 6.06 Desktop + Server + Alternate, tried all three of them. And the computer has 512 mbytes of RAM, 1.5 GHz CPU, it should be fine! I want Ubuntu on this system :(

---

### Post by mizar001 on 2007-01-30
maybe the cd reader is broken or works worser with burned cds ? It's strange that all errors are cd reading related.

As last hope , try a different cd reader.

---

### Post by falfool on 2007-01-30
I doubt that the problem is with the cd readers, because they work smoothly on other machines. Couldn't it be something with the hardware?

Well, anyway, I can't get another reader, I've got only two of them.. Thanks anyway! :)

---

### Post by sstakes1 on 2007-01-30
Another source of the problem could be your IDE controller/ IDE chain itself.
1. Did you install any new hard-drives immediately before trying to install Ubuntu? If so, double check your jumper settings.
2. If that does not work, not try putting the CD-ROM as the sole master in an IDE channel and try the install again. 
3. If that's not possible, restore Windows boot as suggested in the previous post and check if the CD-ROM drive works and you are able to read data correctly.

This may help you isolate any hardware issues. I had such a problem with my DVD-Drive in the past that I traced to the IDE controller and had to replace the motherboard. 

Hope this helps

---

### Post by barronmb on 2007-01-30
> **falfool said:**
> I doubt that the problem is with the cd readers, because they work smoothly on other machines. Couldn't it be something with the hardware?

Well, anyway, I can't get another reader, I've got only two of them.. Thanks anyway! :)

I have run into similiar problems on a different distro...  This seems to be centered around the CD-ROM.  What type is it?  Some strange things occured with a Mitsumi drive I used to have... I managed to get it going by disconnecting the CDROM and reconnecting it.... then ensuring that it was properly seen in BIOS (I do not know why this had any effect --- it shouldn't --- could have been a fluke).  If push comes to shove you can probably command line it and force a default generic driver for the CDROM and see if that gets you beyond the problem.  I am not certain about the Ubuntu install (as I am still trying to get it going myself) but in most distros that I have installed there are ways to force generic drivers to RAID, Keyboard, Mouse, Monitor, and CDROM during install.  One of the Gurus here would probably have more info on that.  

Just a thought... might or might not fix the issue.  Keep us posted.

Edit:  As an after thought... the reading lens of the CDROM could be dirty or failing... this has caused similiar problems for me in the past both on windows and linux.  The CD will spin up and act as though reading but then cycle down and fail to mount.  This is basically b/c the CDROM can't read the media and therefore acts as if it isn't there or as if it is a bad/unknown type and will essentially not read it and mount it.

---

### Post by falfool on 2007-01-30
That sounds very helpful, thank you. I've found a 5.10 Ubuntu CD in my packs, and I tried it, it's going really fine, it's now installing, unfortunately, that doesn't make things better. However, if the lens was really dirty, or if it was something with my CD drives, why is it working with both 5.04 and 5.10 installers and not with 6.06's three isos?

When the system is installed, I'm going to try to run the ISOs I burned from within Ubuntu 5.10, and verify whether it's mounting/working correctly. If it does work fine, then it might be with the ISOs ? Is there a specific way to burn the images? I've used GnomeBaker for burning, I hope that helps.

And oh, is it possible to upgrade from 5.10 to 6.06 using the CDs I have *from within* Ubuntu? Meaning that I don't have to boot up from CD before HD.

Thanks big time for your effort and time, I really appreciate it!
Cheers!

---

