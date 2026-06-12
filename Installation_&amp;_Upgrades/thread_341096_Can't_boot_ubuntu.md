---
title: "Can't boot ubuntu"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by teust on 2007-01-18
Hi, 

I've installed ubuntu in text mode on my machine, dualed with XP.  However when i tried to boot it for the first time it hangs,  I get a black screen that says "Starting up..." and then nada.  I tried using the live cd, safe graphics mode, but it couldn't boot either so text mode was only option.

I did some research and tried adding the following to the boot acpi=off, this got me an error saying pnp bios caused a fatal error.  So i tried acpi=off pnpbios=off but nothing happened.
How can I trouble shoot this problem?? ](*,) 

Thanks

---

### Post by Bartender on 2007-01-18
I got to the exact same spot when I had told GRUB that a Linux install was on hd0,2 when I shoulda said hd0,1.  In other words, the first part of GRUB started but it couldn't find a Linux OS where I'd pointed it to.  Did you write down the GRUB settings?
Are you saying you can't get into Windows either?  There are lots of posts on using a real Windows CD (not a "Recovery" CD) to fix the MBR so you can at least get Windows working again.  I've seen posts that say you can fix the MR with an Ubuntu CD but haven't seen this done.  If you can get Windows running again then you can uninstall/reinstall or fix the Ubuntu partition.
Another thought - borrow someone else's PC and download GPLCD

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Make a CD and boot from that.  You'll be able to see your partitions and verify that Windows is still there.

---

### Post by teust on 2007-01-18
I can get into windows through GRUB.  I installed ubuntu onto the same disk as windows and I guess I assumed GRUB would look there as the other drive is RAW at the moment.   When GRUB comes up it defaults to ubuntu so I guess it finds it??  Not sure how I go about editing the GRUB settings can you enlighten me or point me towards the light ;)
Thanks

---

### Post by UncleFoo on 2007-01-18
Kind of obvious but it happened to me. If you don't have enough RAM it hangs on install. No warnings, it just stops.

---

### Post by teust on 2007-01-18
I've got 2gig of RAM.:)

---

### Post by teust on 2007-01-18
I've been reading about cheat codes that could help booting.  I haven't seen any specifically for ubuntu 6.10, could anyone provide some I could try to get off the ground.  Do these also apply to ubuntu [http://www.knoppix.net/wiki/Cheat_Codes.] (*](http://www.knoppix.net/wiki/Cheat_Codes.] (*),)

---

