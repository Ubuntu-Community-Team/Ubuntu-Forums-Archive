---
title: "Installation errors 10.04-desktop-i386"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by tempestoffrost on 2010-09-15
So, I'm having trouble installing ubuntu on my dell demension 2350. I've installed ubuntu before and it went smoothly, but now it's having issues. First off, when I boot off the live CD, it shows a black screen with the little keyboard icon at the bottom until I press a key, and then it shows the language options (not sure if that's normal). It looks fine at the menu, however, when I try to boot from the live CD or install it it goes black, then to the Ubuntu loading screen, with the orange dots, and sits there for awhile and eventually drops me on a black screen with BusyBox(or something like that) at the top and says something about being unable to find a medium containing a live filesystem. I did it again and checked what was happening at the loading screen and it seemed to be going in a loop, saying something like "Mount: mounting /dev/sr0 on /cdrom failed: invalid arguement," and "can't open /dev/sr1: No media found," and "stdin: error0" and a few other things I didn't write down. After trying to install in a few different manners, like changing options and trying it from a usb, it also spouted out "root inode is not a directory. Corrupted media?" at me a few times in the loop.

any information about my machine if you need it.
Computer: Dell deminsion 2350
Processor: Intel Celeron 1.7GHz
Memory: 1gb
Video Card: Nvida GeForce FX 5500
Hard Drives: 
 one 360gig divided into 3 partitions
 one 30gig in one partition
Main OS: Windows Xp
 ~recently installed and removed an installation of windows 7.

Any help would be appreciated.

---

### Post by uRock on 2010-09-16
After selecting the language have you used the check disk function?

---

### Post by tempestoffrost on 2010-09-16
I just tried it, it's spouting out the same errors. I'm going to try a fresh download on a usb stick and report back..

---

### Post by tempestoffrost on 2010-09-17
The usb stick and fresh download didn't help, but I was messing with stuff and turned of my pci-video card and connected my monitor to the integrated video and changed the settings in my bios. Ubuntu installed fine after that and seemed to be working fine. Then after it installed updates it asked me about the drivers for my video card and I set it up thinking nothing of it, well, now my problem is that ubuntu won't start up and it's spouting the same errors at me. I tried turning on and off my pci-video card in the bios but neither work and I cannot run ubuntu off the live cd or usb. Is there any reason why my video card would be causing ubuntu to act up this badly?

---

### Post by xd20 on 2010-10-01
I have this same issue, but I've not tried disabling my PCI video card. I hope this isn't the case..  I have a Nvidia GeForce 8400 GS 512 mb, and my computers integrated video is really crappy, a measely 64 mb intel thing.

Still can't figure it out..

---

### Post by Goolie on 2010-10-02
> **xd20 said:**
> I have this same issue, but I've not tried disabling my PCI video card. I hope this isn't the case..  I have a Nvidia GeForce 8400 GS 512 mb, and my computers integrated video is really crappy, a measely 64 mb intel thing.

Still can't figure it out..

Have you tried the alternative ISO for Ubuntu?

I couldn't get Ubuntu on a system for the life of me, someone told me to attempt it with the alternative ISO image, the actual installation isn't as pretty, and perhaps slightly less user-friendly, but it does work and the final product is the same as the regular ISO.

---

### Post by xd20 on 2010-10-02
Nope, it doesn't work.  I tried it and ended up with a different error.  When it got to the partition part of the install I set aside two partitions, an ext4 for / and a basic swap partition, then proceeded to finish the partition.  But it failed to create a file system on the ext4.  Then I attempted ext3, ext2 and various other formats, and they also failed.

So while the alternative ISO gets further for me than the liveCD, it still fails eventually.

If you could figure out why.. that'd be pretty excellent too.. I've posted my issues in this thread:
[http://ubuntuforums.org/showthread.php?p=9913989](http://ubuntuforums.org/showthread.php?p=9913989)

---

