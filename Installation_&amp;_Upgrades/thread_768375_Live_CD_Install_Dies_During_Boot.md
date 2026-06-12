---
title: "Live CD Install Dies During Boot"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by H4rm0ny on 2008-04-26
**EDIT:** *For anyone who arrives through Search - I've edited the subject of this thread due to discovering part of the problem was the Asus M2R32-MVP Motherboard I have. This comes in later.*

Hi,

I'm running Gutsy at the moment, I'm trying to do a fresh install of Hardy. I cannot get the live desktop CD to run (have tried multiple burns and CD passes its verification check).

I turned on Safe Graphics mode and to get more information I also removed the Splash and Quiet options from the boot line. I don't know how I can get an actual log file from a live CD, so the best I could do was copy down the error messages by hand. I got the following:

```
end request: I/O error , dev fd0, sector 0
end request: I/O error , dev fd0, sector 0
Buffer I/O: I/O error , dev fd0, locical block 0
ata1.00: qc timeout (cmd 0xec)
ata1.00: failed to IDENTIFY (I/O error, err_mask 0x4)
failed to recover some devices retrying in 5 secs
```

I then get an endless cycle of repetition of the above with some minor variations for other ata numbers (ata2.00, ata3.00, ata4.00) along with the occasional message that a particular numbered SATA link is UP or DOWN.

It may be significant that earlier in the message list (though apparently before it errors properly), I see the line:
```
floppy drive fd0 is 1.44M
```

I have no floppy drive. Nor IDE drives. My hardware is as follows:AMD Barcelona Dual Core 5200 CPU, Asus M2R32-MVP motherboard, 4GB DDR800 RAM, Samsung SATA DVD-RW, Radeon 2600HD Pro Graphics card, 2x 160GB HDs with Ext3 filesystems.

To the best of my knowledge, my hardware is good. I'd really appreciate any help with this as I'd really like to get the new Kubuntu on my machine. Also, as this is a problem right out of the box, I'd imagine that there are other people out there who have the same problem and are getting a very bad first impression of Kubuntu so fixing this might mean solving a bug in the actual Kubuntu install.

Anybody?

Thanks a lot,

Harmony.

---

### Post by SnakeHips on 2008-04-26
Which image are you using?

ubuntu.com/8.04/kubuntu-8.04-desktop-amd64.iso...........this one?

---

### Post by H4rm0ny on 2008-04-26
Thank you. I'm actually using the KDE4 Remix:

kubuntu-kde4-8.04-desktop-amd64.iso

I will go to the normal Kubuntu one and try that if I can't get any further with this, but a big part of why I want to upgrade is to start using KDE4.

Based on where it falls over, however, I think possibly the problem occurs before we reach any distinction between the KDE3/KDE4 versions. I could be wrong though.

---

### Post by alt236 on 2008-04-26
I'm also experiencing the same problem.
My laptop has only IDE drives and no floppy drive

I tried the all_generic_ide switch without luck. 

I'm pretty sure that it has an unused fdd controller though.

I'm also using the KDE4 remix version.

---

### Post by alt236 on 2008-04-26
OK, its working now.

Apparently it's not actually hanging. It's stalling for some reason.

If you wait a bit the boot process will continue.

For me, I got the first i/o error at about 54 of the boot timer and it continued normally at 292.

---

### Post by H4rm0ny on 2008-04-26
Yes - this is the case here also, but I have to say, it was stalling for a really long time. If I hadn't had to dig my laptop out of storage so I could read this forum whilst fiddling, I would never have come back and found that it had actually moved on from error messaging at me to something else.

HOWEVER, this was not the end of the story. I had significant problems and now have my system set up in what I suspect is a half-gutsy, half-hardy - some mutant gibbon-heron chimera that is likely to die at some point.

The desktop trial system never successfully booted. I tried to install from the alternate CD in the end. The first problem was (after the excrutiating wait, that is), that the system couldn't detect my SATA DVD drive (a Samsung Writemaster). As this was the DVD drive I'd booted the CD from in the first place, having the system suddenly lose it mid-install was problematic. I ended up plugging in an external drive and booting from that. (The internal Samsung drive is now working perfectly, however and lest anyone be put off by this, I'd like to say that it's the best DVD drive I've ever purchased).

Unfortunatly, I then reached the second problem: Neither of my internal hard-drives were detected. I kid you not. Both SATA, as mentioned earlier. I got an error message telling me that no partitionable media was detected. Nor could the install script handle this as it firstly gave me blank menu options and the secondly dumped me in a blue screen with no menu at all, forcing me to reset. The Blue Screen of Death in Linux! Hideous! I couldn't find any way past this.

So that brings me to where I am now. I managed to boot into the command line on my half-upgraded existing system and with a lot of manual dpkg -reconfigure, uninstalling and re-installing I managed to get a system up again. It's not worth me detailing the many commands I used to do this and nor can I remember them anyway. dpkg kept quitting on me with "too many errors" when I tried to use it automatically. I had to do packages by hand. dbus was problematic, though I found out that dpkg --reconfigure would work on it when dbus was running but not when it was not. How that comes about, I have *no* idea, but it really was the case!

Now I'm up and running, but I need to reinstall the ATI drivers and I'm not at all confident that my mangled collection of packages can handle that right now. If you don't hear back from me, my computer is dead again! ;)

But I really, really would appreciate any suggestions from the experts here. I would strongly prefer to do a full re-install of Kubuntu on my system.

Anyway, wish me luck, people. :)

_harmony.

---

### Post by H4rm0ny on 2008-04-27
Okay, this has been epic and I feel that I should post what's been going on for the benefit of anyone searching the forums for help.

I have now successfully done a full install of Kubuntu 8.04 (Hardy Heron). Although I played around with the KDE4 Remix, I am advising people *not* to choose this one, but to go with the official KDE3 version. KDE4 is looking great and it drips with potential. But it is not ready yet. You will end up installing KDE3, I'm sure of it; so you might as well do that first, imo. ;)

Now the install issues. I'm not going to cover the attempted upgrade. I did get it working but it was a ******* of a job with much manual reconfiguring of packages. Why that should be the case, I don't know, but there's no way I can detail all the steps and it wouldn't be useful anyway. My advice is to do a fresh install and simply keep the /home partition. If you haven't put /home on its own partition, you can copy the contents off and put it back again afterwards. Be sure to get the hidden files and directories that contain, e.g. your emails.

However, trying to install went seriously wrong on my set up. I got repeated messages about SATA links going up and down, drive errors, floppy drive I/O faults (I don't have a floppy drive). I eventually found that there was a bug in the Linux kernel which has trouble with my motherboard (an ASUS M2R32-MVP) as regards the hard drives.

Firstly, I downloaded the latest BIOS firmware for my motherboard from the ASUS website. That's easy to find. I renamed the file to M2R32MVP.ROM (**not** M2R32-MVP.ROM as instructed) and put this on a USB stick. I then hit Alt+F2 as the boot-bios screen came up with the stick inserted and the computer started searching it for the appropriate file. Note - this failed with my first USB stick, so I reformated one with a FAT16 filesystem and the motherboard was able to read this. For information on how to format a USB stick in this manner, just Google for "linux usb fdisk" and you should find something on how to do this, probably in the context of making a bootable Linux USB drive. Try with any USB stick first (just stick the M2R32MVP.ROM file on it at the top level) and if that doesn't work, go for the fdisk'ing of the drive using the FAT16 file system. You can completely ruin your pen drive doing this, but not permanently, so don't worry about getting it wrong - you can always fix it again. ;)

Once the latest BIOS was on my computer (only took a couple of minutes), I tried again. The boot up still failed, but putting the latest BIOS on at least helped me rule something out as the cause. I then looked at my hard drive configuration. I have two identical Hitachi 160GB SATA drives as well as a SAMSUNG S203D WriteMaster - also SATA based (and the best writer I've ever used - buy one! ). I tried various settings and ended up with setting the mode to AHCI in the BIOS. There was still some sort of conflict on the motherboard as this now prevented any booting at all - I simply got the message "something wrong with your hardware." However, disconnecting either of the SATA drives from the motherboard resolves this. I was then able to complete a normal and successful install using the 8.04 AMD64 Alternate Install iso. Fortunately for me I want all of the core parts of the file system on the one drive with my second one being for media. I have yet to try booting with the second drive attached, so I will post further when I have successfully done this. But in the meantime, I have a working Hardy Heron system (I hope). Just got to put some of the missing bits and pieces on now such as Flash and the proprietary ATI drivers. I hope this helps someone. It's been a bugger to fix and to sort out what was going on.

But at least I know my BIOS is up to date now. ;) >:( :D

---

### Post by empyreal on 2008-04-28
Talk about trouble.  I managed to get it boot LiveCD on my M2R32-MVP.  Bios settings for Sata set to Native IDE so that my XP can still function.  I used pci=nomsi to boot, but this leaves my crossfired radeons sitting like antiques on the shelf because nomsi apparently ruins PCI Express' functionality.  I will be experimenting disabling msi on a couple specific devices using what i've read earlier today.

To disable these 3 devices; Sata Controller ATI SB600 Non-raid-5 SATA, SATA JMicron and some unknown ATI device in the list. 

device_nomsi=0x10025a37,0x197b2360,0x10025a35

If I figure out which one it is specifically, ill msg you.  Good luck yourself.

---

### Post by H4rm0ny on 2008-05-01
> **empyreal said:**
> Talk about trouble.  I managed to get it boot LiveCD on my M2R32-MVP.  Bios settings for Sata set to Native IDE so that my XP can still function.  I used pci=nomsi to boot, but this leaves my crossfired radeons sitting like antiques on the shelf because nomsi apparently ruins PCI Express' functionality.  I will be experimenting disabling msi on a couple specific devices using what i've read earlier today.

To disable these 3 devices; Sata Controller ATI SB600 Non-raid-5 SATA, SATA JMicron and some unknown ATI device in the list. 

device_nomsi=0x10025a37,0x197b2360,0x10025a35

If I figure out which one it is specifically, ill msg you.  Good luck yourself.

Hi Empyreal.

Happy to swap notes and keen to hear of any progress you make at your end. I also have a Radeon card, but only the one so obviously not crossfired. It is, however, working correctly and happily with all of my other hardware, without resorting to disabling msi on any of the devices. Or at least it seems to be now... To install Kubuntu, I took the simple approach of disconnecting one of my SATA hard drives. However once I had successfully installed, I reconnected it and things were fine. Make sense? Not really. It didn't matter which I disconnected, however - the problem only occurred when they were both connected. I had them connected to SATA1 and SATA2 ports (the two orange ones if yours looks the same as mine) and these are a Master and a Slave. You might try connecting your two drives to both Masters instead and see if this resolves a conflict. I know it sounds semi-dodgy, but when choosing between theory and experience, I usually go with the latter, and there was definitely some sort of conflict going on with my set up.

Note: I say SATA1 and SATA2 are Master and Slave on mine, but that's based on the board diagram in the manual. The manual also says that the two red SATA sockets are the Masters, but that contradicts the layout of the diagram. You'll have to check it in the BIOS.

Anyway, wish I could help. My set-up seems okay at present (I hope) and I'm happy to confirm anything you want to compare notes on and interested in how you get on. I'm not using any special boot parameters, now.

Regards,

_Harmony.

---

