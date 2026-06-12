---
title: "Installation can not find installer iso image"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by VeryFoggy on 2013-05-22
I killed my hard drive somehow, so I grabbed the 80 gig one I have been using as a thumb drive. Formatted it, and put the Universal USB installer along with the "saucy-desktop-i386.iso" on it. I plugged it in, and fired up the comp. Got the purple screen that said it couldn't find any drives.


Next I took a 2 gig thumb drive, and did a FAT 16 format. I put unetbootin installer on it. I swapped my regular drive with the 80 gig "thumb drive," and fired it up with the 2 gig in the slot. This time it came up and tried to install. 

It got hung up at: 

--------------------------------------------------------
[!] Scan hard drives for an installer ISO image

The quick scan for installer ISO images, which looks only in common 
places, did not find an installer ISO image. It's possible that a 
more thorough search will find the ISO image, but it may take a long 
time.

Do full search for installer ISO image?

<Go Back> <Yes> <No>

------------------------------------------------------------

Since both drives were recently formatted and both contain only the installation files, including the iso file it needs, it did not take long to do the more thorough search. 

So that is where I am stuck. Any thoughts?

---

### Post by gordintoronto on 2013-05-22
In what you described, there is no operating system anywhere. How did you boot to "scan hard drives..."

Also, Saucy is a work in development. If you plan to help with the testing, great, otherwise I suggest you use a version of Ubuntu which has been released. There is a special forum for reporting anything to do with Saucy.

BTW, I suggest FAT32 rather than FAT16.

---

### Post by Mark Phelps on 2013-05-22
To the original OP -- this is WAY too early to mess around with the next release.  It's weeks away from even an Alpha version -- meaning -- lots of stuff is not going to work and regular breakage is likely.

---

### Post by VeryFoggy on 2013-05-22
Downloading 12.04 now.

How did I boot to scan hard drives? That only worked when I used the thumbdrive with unetbootin on it. Trying to boot from the DVD gives me this lovely message

-------------------
SYSLINUX 4.06 EDD 2012-10-23 Copyright (c) 1994-2012 H. Peter Anvin et al
No child node, aborting...
No child node, aborting...
No DEFAULT or UI configuration directive found!
boot:

----------------------------------------

When it comes to these things, I am gifted. Murphy loves me.

Hopefully the stable version will work. We will find out in a few hours (I have a really slow connection and a kids party I am supposed to help with). 

Wish me luck.

---

### Post by VeryFoggy on 2013-05-22
Going to call this duck hunt over. I am able to run it from the USB. 

Thank you all for your help.

---

