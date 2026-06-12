---
title: "[SOLVED] Where is my floppy drive?"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by mister_lister on 2007-08-13
I have looked through all the posts and found nothing that will answer my question. 

I have dapper drake (6.06) unbuntu.

During my install of Ubuntu I actually saw information pass through the installer about my IDE Floppy drive, as if It was detected.

Yet there is no floppy listed in PLACES>COMPUTER only the cd-rom drive and file system.

I already tried one suggestion: open a terninal and type 

"sudo mount /media/floppy0/" 
it says, 
"mount: can't find /media/floppy0/ in /etc/fstab or /etc/mtab"
and 
mount: can't find /media/floppy in /etc/fstab or /etc/mtab
when I type just "floppy"

Something was lost during install.

I am old school and I tend to use floppies for sneaker net and storage, I hardly use any disk space, I am that efficient. I need my floppy. 

Will someone please respond and give me a direction, some command line or config edit that I can do so I have a floppy again. 

I really appreciate any help you can give me.

PS. In ever other Linux distro I have tried, the floppy was always on the desktop. What gives?

---

### Post by mister_lister on 2007-08-14
I found the solve in a chat room. It is fairly simple.

To load the floppy real time before rebooting type the following in the terminal:

"sudo modprobe -k floppy"

To make it appear at start up, Type the following in the terminal:

"sudo nano /etc/modules"

And add the text "floppy" in a blank line, save (write) and exit. Restart.


The floppy drive should appear in nautilis (places>computer) and from there on you must mount the drive by putting a disk in and right clicking on the icon for the drive and select "mount". When done, right click and "unmount" the drive when done dismounting, remove the disk..

---

