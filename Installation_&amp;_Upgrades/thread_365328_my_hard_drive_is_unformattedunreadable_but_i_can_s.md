---
title: "my hard drive is unformatted/unreadable but i can still boot!?!"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by groggyboy on 2007-02-19
Here's the scoop: on my computer, I have a working 10gig Windows XP partition and a working 10gig Ubuntu partition.  I also have approximately 8gigs of (usually) unpartitioned space that I have set aside for tinkering with other OS's/distros.  After these three partitions, I have a large 31 gig storage partition (formatted to ext3) that contains all my music/videos/documents/linux-home-directory.  Tucked away at the end of my hard drive is a 1 gig swap partition.

About a week ago, I tried to install osx86 ( JaS 10.4.8 ) on my harddrive but problems with the installer being able to format/mount the extra partition led me abandon the effort.
I reformatted the spare partition, and slapped PCLinuxOS on it.  After tweaking the GRUB bootloader that runs off my Ubuntu partition, I never got PCLOS to boot.
I gave up that effort, too, and tried installing Fedora Core 6.  But when I ran the installDVD, error messages kept popping up about my hard drive at /dev/sda not being usable (or something).

I aborted the installation, and booted up from gParted's liveCD.  What really freaked me out was that gParted could no longer see the partitions on my hard drive!  As far as it was concerned, my computer is one big unformatted beast.  So I rebooted into Ubuntu, which worked fine.  As another test, I booted into Windows (*wince*), which also booted fine.  However, when I tried to access my 30gig storage partition, Windows claimed it was unformatted, and asked if I wanted to format it.  Of course I said no.

Does anyone know what happened?  Why does everything but Ubuntu think my hard drive is unformatted (even tho the two existing OS's can still boot)?  I'm no newbie when it comes to partitioning hard drives and installing things, but I have never encountered this behaviour.  It's not urgent - as soon as I saw gParted thought my hard drive was blank, I made backups of everything important, and as I said earlier, Ubuntu *does* work.  That said, I feel like I'm sitting on a ticking time bomb.  Worse case scenario: I wipe my computer and start from scratch.  If anyone knows how I can avoid this and get everything thinking my hard drive is normal, I'd love to know.

cheers, groggyboy!

p.s. - sorry for rambling on there - this post got really long really fast.

---

### Post by cwgpress on 2007-02-19
Sounds to me as if your partition table is not in the standard place, or something like that. Why don't you try other partitioning tools and see if you can find/repair it.

I think you said there's a working XP on there. Have you tried booting to that and then using the disk management facilities to see what it sees?

I had a similar problem once after trying to use logical disks which didn't turn out to be what I thought they were. I was installing a linux distro (don't remember which one) and ended up with 160GB of unreadable partitions. I had to dig out an old disk and install Win2k on it, then run some sort of magical disk recovery software that helped me locate about 20GB of stuff I thought was important. I then put the 160Gb drive away for about a year before I decided there couldn't be anything else on it that was too important, and put it back on my main computer. That's the one I'm currently trying to set up using the gparted installer but I'm stuck trying to figure out how to commit changes.

Good luck!

Chuck

---

