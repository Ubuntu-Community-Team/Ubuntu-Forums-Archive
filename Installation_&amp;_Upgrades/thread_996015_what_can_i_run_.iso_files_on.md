---
title: "what can i run .iso files on?"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by spamcami on 2008-11-28
I downloaded ubuntu 8.10 onto my Windows XP and when trying to open it I received an error saying that I can't run .iso files off of anything.

I just hope that this installation uninstalls Windows like my CD should have -- that didn't work either; My CD drive works fine, but ceased recognizing anything since June.

---

### Post by SocratesTNR on 2008-11-28
The iso file is a CD image.

It needs to be burnt onto a CD by a suitable CD writing program.

Try a Google for iso and CD Burner

---

### Post by gpsmikey on 2008-11-28
An .iso file is an "image" of the file system on a CD (or DVD).  You can use the free imgburn utility to burn it to a CD (or DVD if it was a DVD iso).  There are also tools out there (both free and payware) that allow you to mount .iso files like they were a drive.  I'm not sure there is anything out there that allows you to mount an .iso file and run it in a manner that would overlay the OS that is running the .iso file that you have mounted though.  If you do have a dead cd-rom drive, new ones are cheap these days (you can buy decent CD-ROM/DVD-ROM/burners for $20-$30 these days from places like newegg etc.

mikey

---

### Post by spamcami on 2008-11-28
So i could find something that would install it and *not* overlay my OS?

---

### Post by gpsmikey on 2008-11-28
Well, typically the way it works is you use the .iso to build a bootable CD which you then boot off of.  It loads it's own operating system (the bootable Ubuntu CD's can boot without a hard drive even present in the system).  From there (since it is running from the CD and RAM), it can load whatever it wants on the hard drive since the hard drive is not being used by the OS.  Trying to get something to overlay itself while running is a bit trickier (often used for "in circuit programming" of small embedded controllers etc though).

mikey

---

