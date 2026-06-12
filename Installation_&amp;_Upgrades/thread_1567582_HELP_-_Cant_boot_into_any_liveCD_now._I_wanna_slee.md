---
title: "HELP - Cant boot into any liveCD now. I wanna sleep, help me fix!"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by tiyhit on 2010-09-04
I run an apple, and i was cleaning off an old 500gb drive of most of its files.  I decided i wanted to partition said drive. (To put linux and windows partitions on it)

I go to boot into my liveCD to use gpartd (cause its way better than disk utility).

This time (this has never happened before) I hold down option key, click the cd and it boots.  As its loading the cd drive gets really intense sounding and then i get this:

"error: no such device: c3be59ad-a223-44d9-af2d-3196748d97dc ."

Its not the dvd drive, i have tested it and it did not break.

Its not the dvd because i just burned 3 and they all do this.

Leads me to believe, after reading online, it may be my mbr is corrupt.



Unfortunately... the usual fix is booting into a live cd... which isn't working!

---

### Post by tiyhit on 2010-09-04
Any ideas?   Missed my lan party because I couldn't get the linux os or windows os up.

---

### Post by oldfred on 2010-09-04
It seems like it skipped the CD and is trying to boot the drive that may still have a boot loader but the old partitions are gone so it cannot find the UUID.

Are you set to boot CD first? Has CD worked before or did it get damaged?

---

### Post by -kg- on 2010-09-04
> Leads me to believe, after reading online, it may be my mbr is corrupt.

Highly unlikely.  The MBR has nothing to do with booting from the CD/DVD drive...only from the hard drive itself.  Booting from an optical or external drive is handled by BIOS.

What do you mean by, "gets really intense sounding"?  That sounds like it could be the drive going out.  When you select it and it can't find a bootable disk on the drive, it then drops to the next in the list, which would be the hard drive itself.  As oldfred said, the bootloader is looking for a UUID that no longer exists.

If you have another computer, you could check this by making a bootable Flash drive and booting to that.  You would be able not only to boot to it, but install from it as well, if you need to.

There are several ways to make one...I prefer [Unetbootin]("http://unetbootin.sourceforge.net/").  I suggest (considering you likely already have the .iso) the second method of installation (Diskimage), since I've had a couple of problems with the default.  The "Diskimage" method has worked every time for me.

---

### Post by tiyhit on 2010-09-04
I went out and bought a time machine im just going to reformat the whole drive, restore files, and then do ubuntu on my external.  Thanks for the support.

---

