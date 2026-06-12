---
title: "stupid me: need help with disaster recovery"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by arjay1 on 2006-06-20
I was installing ubuntu over suse 10. I had spent the afternoon carefully backing up my data onto what I thought was a separate disk in my computer (hdb2) but turned out to be a separate partition on the same disk (hda2). Can't believe I was so stupid.

I chose reformat entire disk, of course. I stopped the reformat about 30 seconds into things by pulling the plug (literally). The data was stored in ReiserFS format. I have tried to look at the disk using the storage media function in the live ubuntu CD but it says "can't mount the disk - not in fstab or mstab" or words to that effect. Does this mean just that, or does it mean that my partitions are gone and at worst, some of the data. Perhaps someone could help with the correct command to mount the hard disk hda, or a line to add to the fstab to do the same (if the live cd will let me do that?)

I have tried fdisk /dev/hda but it just says "unable to open /dev/hda". I have a backup of the hard disk but it is rather old and I have important family photos on the disk that I really, really, want to recover if possible.  Wife is going mad:( 

Any help really appreciated

RJ

EDIT

It doesn't look good at the moment - found and ran QTParted. It reports:

01 /dev/hda1 ext2 Active 55GB 887 MB used
02 /dev/hda-1 free 55GB
03 /dev/hda2 extended 1.44GB
04 /dev/hda5 linux-swap

Looks like all of my data has gone or could it be that the part install/format just changed file names??

I have a live CD (ubuntu) and two CD Roms. Can anyone advise me what recovery software - hopefully open source, though I'll pay if I have to, that I could run under ubuntu just to see if can see the content of the disk. Any other advice other than "what a prat" would be greatfully received.

---

### Post by John.Michael.Kane on 2006-06-20
Have a look over these. they may offer a better route for recover.

[**(R)ecovery (I)s (P)ossible Linux rescue system**]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip/")

[**finnix**]("http://www.finnix.org/")

[**SystemRescueCd**]("http://www.sysresccd.org/Main_Page")

---

### Post by arjay1 on 2006-06-20
Thanks SD

I'm "on the case"

RJ

---

