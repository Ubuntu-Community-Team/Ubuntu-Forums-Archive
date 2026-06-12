---
title: "Ubuntu and Open Solaris conflict"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by edwardswyco on 2008-07-18
Hi everyone!  I'm incredibly new here, but hope to stay for a long, long time!

A friend convinced me to dump XP for Ubuntu and I love the change.  He's also a network guy that suggested I get my feet wet with Solaris, just for fun and possible work.

Last night I installed Open Solaris on an empty partition and it wiped out my MBR.  Can anyone help in fixing this?  I am assuming Linux is still there, just inaccessable.

When I originally burned Ubuntu, I screwed up by using ISObuster on the ISO before burning it.  As it happens, even changing my boot sequence would not allow me to access the CD-ROM.  To install Ubuntu, originally I had to load up XP, double-click the disc drive, and asked the program to "help me install" from the CD.  

My first attempt at fixing the MBR problem was to put my Ubuntu CD in and see if I could fix it through that, but again...it doesn't read anything and goes to Solaris instead.

I would like to get my feet wet by actually fixing the problem instead of taking the easy way out and wipe it clean.  My brother recommended I burn another Ubuntu CD or to try to mount the CD and reinstall GRUB.  Does this sound doable?

Thanks - sorry for the length of the post.

---

### Post by PmDematagoda on 2008-07-18
Did you check in the BIOS to see if booting via the CD-ROM is enabled? Because from from your problem it does seem that the certain option is disabled.

---

### Post by edwardswyco on 2008-07-18
Hi,

I wish it was that.  Unfortunately, the boot sequence is correct.  

My brother found this advice:
# chroot /mnt/sysimage 
# grub-install <devive> (/dev/hda) 
 
I guess they meant to say device instead of <devive>.

Someone had installed fedora and then XP (Windows, of course, wiping the mbr clean).  I wish to try this tonight, but wanted to see if anyone had any better ideas.

Thanks,
Jason

---

