---
title: "[SOLVED] Grub Error 22"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by melrom on 2008-05-27
Hi- Let me preface this by saying that I've read the documentation on the forums about fixMBR and such. I just have a bit of a different situation, so I decided to post my own thread.

I had an extended partition with Gutsy installed on it [sda5 with sda6 as swap]. Hardy then installed itself as sda7 with a swap of sda8. I wanted to get rid of the Gutsy part because I never used it, so I deleted sda5 and sda6 using gparted [off of the Ubuntu live cd], but now I get grub error 22. Furthermore, gparted doesn't recognize the Hardy partition anymore. It says it can't read the partition. =\ Any ideas? Should I download this supergrub thing? But that's not the most of my problems. I'm also wondering what the heck happened to the data on the sda7 part and why gparted doesn't recognize it anymore.

---

### Post by melrom on 2008-05-27
Note: I booted back into the Ubuntu live cd and gparted sees the data on the Hardy partition now, but it's still throwing the Grub error. The thing is I didn't want to get rid of linux or anything, so I don't want to do the fixmbr thing and have just Windows run again...

---

### Post by Rallg on 2008-05-27
Before doing anything else, use the live CD, terminal:

ls -l /dev/disk/by-uuid

and see if the UUID for your Hardy partition (and swap) match the Grub menu on your hard drive. If not, edit menu.lst.

Also check to see if the partition identifiers are the same. Is your (former) sda7, which was probably known to Grub as (hd0,6), still the same, or is it now (hd0,n) for some other n? If there was a change, fix it on Grub menu.lst.

---

### Post by melrom on 2008-05-27
what would the path of the menu.lst be? is it going to be in the 100 megs i have allocated as a boot thing??

also, should the swap and linux have the same uuid?

---

### Post by melrom on 2008-05-27
it says that menu.lst and grub.conf are unreadable??

but also that i don't have the privelge to read them. i tried sudo-ing them but i'm not sure how to sudo off of a mounted drive. lol.


[edit:] okay, i'm viewing menu.lst. sorry about all the above nonsense.

but menu.lst has everything listed as being fedora? which i had awhile ago but not anymore. perhaps there is a different one that was being used for ubuntu.

---

### Post by Rallg on 2008-05-27
Perhaps you were reading menu.lst from the live CD. It shows its file structure, but will be un-editable even with sudo, since the files are read-only on the CD. You want to be sure to get to the files installed on your hard drive, not the CD.

Path to menu.lst: From the Ubuntu menu, use Places. Find the volume (partition) that contains your installed Ubuntu. It may be listed as "XX Gb Volume" (where XX is its size). If you don't see that, then find it in Computer > filesystem > dev.

Once you locate the hard drive volume that has Ubuntu installed, go to boot > Grub and you will see menu.lst. If all you want to do is look at it, double-click to display. But if you need to edit it, try this in Terminal:

gksudo gedit /dev/whichone/boot/grub/menu.lst

where "whichone" gets you to the correct place.

---

### Post by melrom on 2008-05-27
okay, i will try that now. as far as the menu.lst i was looking at, i have an sda3 partition that i guess was used when i used fedora which is strictly a boot partition. i didn't install fedora myself, someone else did, and i think they wanted to keep grub separate from the OS itself. i have no idea. but that's the one i was looking at. i will locate the correct menu.lst now.

---

