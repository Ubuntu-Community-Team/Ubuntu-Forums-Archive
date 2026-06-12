---
title: "Dual Boot Kubuntu and Ubuntu-Studio help required"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by Tom Mann on 2007-05-16
Hi,

Now UbuntuStudio has come out, I've reconfiguring my computer to dual-boot both this and Kubuntu. I have started from scratch, as I need a very particular partition scheme (to get the very best performance out of UbuntuStudio). However I'm struggling to get one to accept the others presence.

This is how I planned the install initially

/boot (shared for both os's, ubuntustudio uses a slightly different kernel so shouldn't interfere with Kubuntu, EXT3)
/ for Kubuntu (set to unused in ubuntustudio's install, ReiserFS)
/ for UbuntuStudio (set to unused in Kubuntu's install, ReiserFS) 
swap

this didn't work, so am trying the same with two different /boot partitions (each one set to unseen by the other OS)

I have a second hard disk (set to XFS), but that is only to be used as an audio drive (for the sake of performance).

Can anyone give any hints on how to do this, a HOWTO or even a little advice?

If I get this going, I will write a HOWTO for you all, if it helps.

Thanks,
Tom

---

### Post by Tom Mann on 2007-05-17
Sorted. I started by mapping my partitions as follows.

Disk 1 (160GB Drive)
(1) 50MB Partition (Primary) (EXT3)
(2) 50MB Partition (Primary) (EXT3)
(3) 90GB Partition (Secondary) (ReiserFS)
(4) 50GB Partition (Secondary) (ReiserFS)
(5) 10GB Partition (Secondary) (SWAP)

Disk 2 (250GB Drive)
(1) 60GB Partition (Primary) (ReiserFS)
(2) 40GB Partition (Primary) (XFS)
(3) 100GB Partition (Primary) (XFS)
(4) 30GB Partition (Primary) (XFS)

I started with UbuntuStudio, with the following assignments:
Disk 1: (1) /boot, (2) Not Used, (3) Not Used, (4) /, (5) swap.
Disk 2: (1) /home/username/Documents, (2) /home/username/Music (OGG) (3) /home/username/Projects, (4) /home/username/Work.

Then with Kubuntu I used the following:
Disk 1: (1) Not User, (2) /boot, (3) /, (4) Not Used, (5) swap.
Disk 2: (1) /home/username/Documents, (2) home/username/Music, (3) Not Used, (4) Not Used.

(I used the same username across both installs)

And the whole thing works beautifully.

All of the Audio/Temp Partitions are to the outside of the drive (in particular the work partition), ensuring maximum disk-write performance while streaming my music to and from the hard disk. :)

---

