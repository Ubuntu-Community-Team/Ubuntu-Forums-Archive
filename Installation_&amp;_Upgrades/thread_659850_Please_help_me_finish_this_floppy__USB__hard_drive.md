---
title: "Please help me finish this floppy / USB / hard drive install!"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by Taxi on 2008-01-06
I'm following this guide: [https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies](https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies)

I've been having getting hung up the whole way, but finally I'm at the end... so close... and... more trouble.  I'm to the "Installation" section (using the Xubuntu Gutsy alternate install image), but I'm having a hard time convincing the installer to use the dummy partition on my hard drive with the CD image dd'd on it.  I tried the trick posted in "Notes," but it's not working.  Any gurus out there with suggestions?  Even if you don't consider yourself a guru, I certainly will if you can get me through this!  :)

---

### Post by Taxi on 2008-01-06
The installer gets to the part where it says "Detecting hardware to find CD-ROM drives" then goes through it's driver loading, etc. But when it gets done it comes up with a screen that says:

[!!] Detect and mount CD-ROM
Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive. If so you can insert it and try again.
Try again to mount the CD-ROM?
(Yes) (No)

This is somewhat expected since there's no disc in the drive and even if I put one in it doesn't make a difference since the drive doesn't work well in general and not at all for burned discs. It seems like the trick (based on the method of dd'ing the iso to a partition and the note at the bottom of that guide) is to get the installer to read the dd'd partition as a CD-ROM. It seems to be working, since it boots fine and starts the installer. But then (I guess when it's looking for modules to load?) it decides to look for the CD again instead of just using the partition it's been using. Obviously, that doesn't go so well. :/

I can get a shell from the installer after the error, and I'm thinking something similar to the trick in the note will be what gets it working by making the installer recognize the dummy partition as a CD. I just don't fully understand what the person did, so I don't know how to modify/customize their method to make it actually work for me. I'd really appreciate any help or suggestions anyone can give.

---

### Post by Taxi on 2008-01-06
Maybe there's a good way to manually mount it?  Is there some specific way I can mount it (as opposed to just linking the /dev/'s) so that it would skip auto detecting and already know where the "CD-ROM" is?

Just throwing that out there; feel free to ignore me and go in another direction if it seems more likely to work.

---

### Post by Taxi on 2008-01-06
Well, I at least partially solved my own problem.  I tried a few things, including mounting the dummy partition to /mnt/cdrom0 like I would expect in an installed Ubuntu, but the one that worked was:

mount -t iso9660 -o loop /dev/sda3 /cdrom
(/dev/sda3 is the dummy partition)

After doing that, it worked fine for a while.  But now I'm getting a new error:

[!!] Install the base system
Debootstrap Error
Failed to determine the codename for the release.
(Go Back) (Continue)

I'm not sure what this is about, but I'm going to see if anyone knows in the IRC channel and if no one there can help, I'll make a separate thread.  I'll post back when (I'm really hoping I'm past "if" at this point) I figure it out, just for closure.  In the meantime, if anyone happens to know what's going on, please feel free to post here!

---

### Post by Taxi on 2008-01-09
Well, it turned out that the guide I was using was off slightly. It probably worked great in the older installers, but not for Gutsy. Luckily I continued searching every which way for more information and came upon this guide: [http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093). I didn't end up using that method, but I was able to deduce that the problem with my original guide was that it had me copying and booting the vmlinuz and initrd.gz from the CD, whereas different ones from [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/) are available and necessary for an install from hard drives and non-bootable USB drives. Everything went smoothly once I had the correct kernel and ramdisk files. I didn't even have to do the manual mounting I was doing before.

This install was quite the learning experience / hassle. The funny part is that after all that Xubuntu is running too slow. I'm gonna try Fluxbuntu tomorrow; the good news there is that the same installation method should work for Fluxbuntu, so it should be a breeze compared to the first one that took forever to figure out.

---

