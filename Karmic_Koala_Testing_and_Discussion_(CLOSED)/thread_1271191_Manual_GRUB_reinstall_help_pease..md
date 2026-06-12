---
title: "Manual GRUB reinstall help pease."
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-09-20
Hi, I just updated my PC last night and I cannot boot now.  I popped in a alternate disk to do a recovery and I can access the PC still thru that, so it seems I need to reinstall grub.  i have software raids setup and have never manually installed grub like this.  Can I please get help?

Setup:
3 sata drives with 3 partitions

partition 1 drive 1+2 is a 512mb mirrored raid for /boot
partition 2 all drives is the /root
partition 3 all drives (and partition 1 drive 3) 512 MB swap space

---

### Post by LordVeovis on 2009-09-20
Almost fixed...
i can boot up, but it does not mount my encrypted home folder so it cant find any files it needs and locks up

---

### Post by talkingwires on 2009-09-21
So /home is part of the root filesystem? Is that the only part that's encrypted, or did you encrypt your whole filesystem?

I'm kinda new to encrypting parts of filesystems, but do you know your encryption passphrase? If you do, at least you can access /home with a live CD and get your data out...

---

