---
title: "Dual booting with Hardy already installed"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by Deaconblue on 2008-10-25
I already have Hardy on a 180Gb drive, but would like to partition 20Gb from that to install XP for a dual boot system, but everything I've read seems to be for if you are installing Ubuntu into an existing Windows HD. I did install GParted but although it shows me my Ubuntu partitions, it won't let me alter them in any way.

Can what I want be done, and am I using GParted the wrong way?

---

### Post by Afkpuz on 2008-10-25
Well, you can't edit a mounted hard drive.  Since you're running gparted off the same hard drive, you see the problem.  What you'll need to do is head over to the gparted website...actually, just click this link.

[http://downloads.sourceforge.net/gparted/gparted-live-0.3.9-4.iso?modtime=1222872844&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-live-0.3.9-4.iso?modtime=1222872844&big_mirror=0)

Download gparted and burn it to disc.

Then, boot from the CD and pick the autoconfigure setting.  It's the default choice.

Then, you can edit your main hdd to your hearts content.


Although, I think I've heard that windows likes to live on the beginning of your hard drive.  Either way, that's how to you can edit your hdd

---

### Post by bulldog on 2008-10-25
Windows MUST be installed on a primary partition!
It won't boot from an extended partition.
And you need to re-install GRUB.
Instead of the GParted live cd,you can use the Ubuntu live cd as well.

---

