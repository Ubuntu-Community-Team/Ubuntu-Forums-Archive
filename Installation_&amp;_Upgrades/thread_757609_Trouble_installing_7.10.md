---
title: "Trouble installing 7.10"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by rules on 2008-04-17
Hi all

Actually been running Suse 10.3 for a while but a friend suggested checking out Gutsy. I have downloaded (desktop.i386) and used K3B to check the iso (came up with correct md5sum) and then burned the cd at x4.

The cd boots up fine and the installation starts up fine. I go through all the settings and things it asks but about a minute or two into it doing the actual installation it stops and comes up with an error. I can't remember the exact message but it says something about, either the cd being faulty and/or the hard drives being faulty or old.

At this stage it has already formatted the 3 partitions (swap, root, home) and also killed grub so it was quite a mission to get back into my windows partition.

Any ideas?

With Suse I used EXT3 file format. What should I use for Gutsy?

Thanks.

---

### Post by zvacet on 2008-04-17
Ubuntu use ext3 too.Check your CD for errors.You have that option when you boot.

---

### Post by rules on 2008-04-17
Hi 

Just did the cd check and it failed saying 2 files where damaged/corrupt. I checked the md5 again using K3B and then cut another cd. The writing process completes without any problems but when doing the cd check it again said there was an error with 2 files.

MD5 checks out.
Use proper cd (Verbatim AZO) and slow writing speed (x4).
CD writes without any errors/problems.
CD check fails.

I'm confused :P

---

### Post by dstew on 2008-04-17
Burning a complete image is a challenge for most CD burner hardware, because every bit burned has to be readable. It has to be perfect. You need to use good quality CD-R, and burn slow. If 4x is not working, go to 2x or 1x. Maybe your burner is faulty, or your reader has a bit of lint on the lens.

---

### Post by zvacet on 2008-04-17
Download same iso with torrent and point download to the foldr with existing iso.Torrent will just check your iso and replace corrupted files with good ones.Check md5sum again and burn iso on CD and check Cd for errors.If everything is O.K. go for install.

---

### Post by Psyphre on 2008-04-17
Do you get this?

[I]The installer encountered an error copying files to the hard disk:

[Errno 5] Input/Output error

This particular error is often due to a faulty CD/DVD disk or drive, or a fault hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens, to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment[/I]

---

