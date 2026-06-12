---
title: "Can't install or boot linux"
date: 2018-03-01
forum: Installation &amp; Upgrades
---

### Post by othman.alazzam on 2018-03-01
Hello linux people,

I've decided to switch to linux just recently on an old laptop but for a newbie me ... :(

I'm trying to install lubuntu 32-bit on my laptop, it "was" runnuing fine from a bootable usb thumbdrive.

I encountered the "not a com32r image" and solution "live" solved it at first times.

I wanted to install lubuntu on the laptop natively while keeping previous data safe in a certain partition.

So I started the install executable file existing on desktop and encountered all sort of problems, at the end I got it (from a youtube tutorial), I need to re-
partition my hard disk right?,, well.. I kinda **cked up my computer I believe.

To give you an idea of what I did on my disk, I've tried to delete all partitions but not the windows one to maintain data .. last disk configuration I remember is like :
- 4.5gb free space
- 422gb main windows partition
- 0 partition (this one I couldn't delete and it says smthng like (sort of) "can't delete a partition while it's extended of other logical partition.. I can't remember :( "
- partiton of 73gb ,, this is considered confusing, cuz it didn't allow me to create a partitions saying that there is existing partition, AND it doesn't give the option to edit the partition considering I've deleted it lately 0_0 !!!

Now I'm getting errors at the boot after doing the "press tab then type (live)" thing stating:

"end kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(2,0)"

Here's a shot of current screen : 
[https://ibb.co/couUhc](https://ibb.co/couUhc)

the current build of lubuntu doesn't give a boot menu, it tries to execute and run and install the system after it opens ((i mean there is no try/install option))

Any Help is reallllllly appreciated :'( cuz I feel hopeless at this point.

---

### Post by othman.alazzam on 2018-03-01
I've re-writed the image to usb and it booted successfully, now I get fault while running the installation.

"the installer encountered an error copying files to the hard disk:
[Errno 30] Read-only file system: '/target/usr/share/lxterminal'

This is often due to a faulty hard disk. It may help to check whether the hard disk is old or in need of replacement, out to move the system to a cooler environment."

:/

---

