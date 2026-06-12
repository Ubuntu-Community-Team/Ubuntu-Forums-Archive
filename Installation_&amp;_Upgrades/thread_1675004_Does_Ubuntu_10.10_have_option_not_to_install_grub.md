---
title: "Does Ubuntu 10.10 have option not to install grub?"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2011-01-24
Hi all,

I have my machine booting Windows 7, Ubuntu 10.10 (64bit), and OpenSUSE 11.3 (64bit). All good.

When I added OpenSUSE it was really easy (thanks wilee-nilee and Garvinrick4 :)). There is an option not to install grub. I ticked the box and once installed I simply re-booted into Ubuntu and 'sudo update-grub'. Voila, job done. (Interestingly it uses the same /swap as Ubuntu so that is convenient, an accident, long story, and off topic!)

Is there a similar option in Ubuntu where during install I can choose not to install grub and use the same method as I did with OpenSUSE? 

Also, I am wanting to use the existing Ubuntu /home and /swap partitions. How do I go about that? I will do some further research on that bit and no doubt find the answer but I'm figuring I create just one partition, /, during install and somehow direct it to use the existing /home and /swap. Issue is, won't it create a /home *directory* inside the / partition if I don't allocate a /home partition during install?

Reason I'm doing this? I have a Realtek wireless card that has never behaved. I ended up emailing Realtek only to discover the driver/firmware wasn't suitable for 64bit systems. Therefore I am going to attempt to install Ubuntu Desktop 10.10 32bit version and see if I can't get the card behaving there.

I had thought of Virtualbox for doing this (which I have installed but haven't used yet) but decided against it only to save time when booting. I would need to boot the 64bit Ubuntu then the 32bit Ubuntu inside that. Waste of ten seconds!

Tnx in advance ... ;)

---

### Post by kansasnoob on 2011-01-24
Most of your questions are answered here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

> The option to choose where to install grub is now only available if you choose “Manual partitioning”, and there is no option to not install grub. AFAIK if you don’t want to install grub to the mbr of a drive you must now install grub to the pbr of the new "/" (aka: root) partition or the “/boot” partition if one is being created.

> I assume everyone knows that “Format” will erase everything on that specific partition! Commonly if you’re creating a new “/” and “/home” you will want to format the new partitions. However, **if you’re using an existing “/home”, you would not want to format that “/home”!** Doing so will erase all data in “/home"! There is no need to format a SWAP partition.

> the installer will use any and all existing SWAP partitions

---

### Post by Bucky Ball on 2011-01-24
Cheers, kansasnoob. That leaves me in a bit of a predicament re grub. This means I am going to have a couple of grub2s installed in separate places. 

Guess I could just use the new grub2 and 'sudo update-grub' will pick up ALL installed OSs? I'll have a look at the link you posted.

* AFTERTHOUGHT: Or ... if I just go ahead and let grub install to where it normally would, I can then boot into the new 32bit install and 'sudo update-grub'? Would it be that easy? I'll do some digging ...

---

### Post by Bucky Ball on 2011-01-24
Just to add to that, I have been checking this page:

[http://ubuntuguide.org/wiki/Lucid_Multiple_OS_Installation](http://ubuntuguide.org/wiki/Lucid_Multiple_OS_Installation)

... and I'm wondering if this is the way to go:

Don't install grub2 to the MBR but to the sd** the new / is on, as inferred.

When I reboot will this then take me to the original grub2 on the MBR where I can boot into the original Ubuntu and 'sudo update-grub', easy as that, thanks for all the cheese, move along nothing to see here?

Ideas??

---

### Post by Quackers on 2011-01-24
I don't think there is an option on 10.10 to not install grub (only previous versions), however I think it should be possible to install grub to a flash drive, rather than your hard drive (if that's what you want). I don't know whether your other grub (legacy) will then pick up 10.10 or not though!
I have 3 Ubuntu installs, and 3 versions of grub 2 installed in various places. The only problem is identifying which grub has control at any time. It is easily corrected by booting into the OS that I want grub to run from and running the grub-install command.

---

### Post by Bucky Ball on 2011-01-24
Thanks Quackers. There is no option to not install grub2 since Lucid apparently (from kansasnoobs informative link). The link I posted in post #4 is the one I've been looking at but I'm thinking it is probably easier than the description given under 'Installing your second Ubuntu'. One thing though; it might have a point when it mentions not to install grub to the MBR but to the / partition of the new install. I'm figuring that would reboot me into my old grub then I could just update it to pick up the new install.

My current install is 10.10 64bit desktop so Grub2 is up and running and booting that, Win7 and OpenSUSE without problem. When you installed your second Ubuntu (or third for that matter!) did you just create / and that was it? The rest took care of itself? Then reboot, and once at the desktop, sudo update-grub?

That easy?

PS: Nope, not interested in the Flash option. Have free space ready on the hard drive.

---

### Post by Quackers on 2011-01-24
I have separate /home partitions on them all and as I installed the next one I just run sudo update-grub.
Something I've used to differentiate between the 3 grubs, is I have no splash image on one grub, and I have  different splash images installed on the other two grubs. So I know which grub is running things - and more importantly, when control changes.

---

### Post by Bucky Ball on 2011-01-24
> **Quackers said:**
> 
Something I've used to differentiate between the 3 grubs, is I have no splash image on one grub, and I have  different splash images installed on the other two grubs. So I know which grub is running things - and more importantly, when control changes.

Good thinking. Going to try my luck later this afternoon. Thanks for the help and I'll post the outcome later. ;)

---

### Post by Quackers on 2011-01-24
Ok, have fun :-)

---

### Post by Bucky Ball on 2011-01-25
Created a 20Gb EXT4 partition for the Ubuntu 32bit OS, downloaded 10.10 32bit OS and burned to CD. Booted from CD and got to the 'Ubuntu' screen with the dots filling and emptying again and that is where it stayed for about half an hour.

I downloaded the ISO via torrent so pretty sure nothing wrong with the CD but it won't go past that screen. Might start another thread about this issue as it is different from the original problem described in this threads title (which is theoretically solved).

Will post a link here if I can't figure it out and I end up posting another thread. ;)

* Machine is working fine so no screw ups when creating the partition. Things were a bit odd there at first, another story, but I fixed everything so was working fine before attempting to install anything.

---

