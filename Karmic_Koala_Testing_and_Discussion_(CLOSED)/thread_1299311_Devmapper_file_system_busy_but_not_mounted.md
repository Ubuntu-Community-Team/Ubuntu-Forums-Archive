---
title: "Devmapper: file system busy but not mounted"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ExtenzJunkie on 2009-10-23
Can someone help a brother out?  I can't mount drives on my system now.  I *think* this happened in the last couple of days (mid-October).  Keep in mind that I started out when you'd store your program on paper tape.  Yes, I'm serious.  I'm THAT old.  So, this has blown my mind.

This is 64-bit karmic, up-to-date.  

It started out that I was cleaning off an external (eSata, but USB and Firewire have the same issue) drive.  After that I tried to mkfs the thing, and it said it couldn't get exclusive access (already mounted?).  It wasn't mounted.  It wasn't anything except attached and empty.

After literally hours of googling and dinking around, I found that this is related to devmapper-- about which I know nothing.  I run "dmsetup status" and I see what's obviously that drive.  I remove it (dmsetup remove 1ATA...), and now I can mount that drive manually (unless I wait too long, then it seems to add it back).

My logs are now full of:
Oct 23 15:40:26 hallix64 kernel: [84374.975897] device-mapper: ioctl: error adding target to table

I suspect that's related.

There is very little information out there on the net about how this damn thing works-- it's mostly about why it's so totally awesome!  Now, I've come to find that when I plug in a drive, the system tries to automount it under /media, but fails because of... whatever is doing this.  It's busy.  You can't mount it.  But it's not.  Not mounted.  No stray mtab entries.  Nothing. lsof shows nada.  

All the relevant suggestions I've seen suggest removing evms.  Of course, that's not there anymore.  I've tried manipulating multipath.conf, but again, the docs are so obtuse that I'm at a loss for such required entries as wwid.  It's not the same as uuid?  It could be those strings that show up in dmsetup and /dev/mapper, but then... they don't look like any example I've seen.  Who knows?

I'm stumped.  Is there any documentation out there that explains what devmapper does in a way that someone who doesn't program low-level device drivers might be able to understand how to wrangle it?  And why do we need all these different ways to refer to disks?  I understand UUID over /dev/sdX in case it moves, but... why this?  These aren't LVM volumes, and they aren't RAID.  So, why is devmapper screwing with them?

Any pointers to practical explanations of how to really master the confi of this thing would be very welcome.  I'd love something that gave simple examples of this situation.  "So you wanna plug in a USB drive?  Do this!"  As it is, I think this is going to screw a lot of people up.  It has me.

Thanks.

---

### Post by ShadowTek on 2009-10-23
I have noticed that Karmic will go ahead and load desktop while a disk check is being performed. It gives no indication as to what is going on, it just fails to mount the drive and gives a "busy" warning if you try to mess with it.

I was hoping that they had fixed this by now.

Anyway, is your disk access light blinking for a long time after you first boot your system? If so, it's probably the same issue that I was seeing. You can just wait long enough for a full disk check to be performed, at which point you should be able to access it again.

---

### Post by ExtenzJunkie on 2009-10-24
Yeah, I've waited until that's done (they are externals that go to sleep), but there's no time dependency that I can see.  If I attach a drive, fuse tries to mount it, fails, and I can't do anything until I manually dmsetup remove it and manually mount it.  It's not the end of the world, but clearly it's not supposed to work that way... unless I'm missing something.

---

### Post by ShadowTek on 2009-10-24
The only mounting of external drives I've done thus far is loading some music on my FAT32 usb mp3 player. Everything auto-mounted and functioned as normal, with the only noted difference being that there is now a "safely remove device" option in the gui menu when you right-click on the device.

I'm not sure exactly how that's different from simply umounting it, but I tried both commands and they worked fine.

---

