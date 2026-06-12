---
title: "Where's my floppy?"
date: 2005-11-11
forum: Installation &amp; Upgrades
---

### Post by James Hunter on 2005-11-11
First, I have just installed Ubuntu, and it is awesome. I have a huge admiration for all the people who put this together. It is very user friendly, and most things are working fine. I have run into one glitch. For some reason I can't seem to get to the floppy disc either through OO or through Gimp. The 2 CD Rom drives work fine. They load onto the desk top and I can get them there. The floppy is connected in some way because the program for formatting floppies works. If I go in through the file browser it shows the floppy drive (when I hit “computer”) but when I try to open it I get a message that says “Unable to Mount Selected volume.” When I go in through the terminal I can't find either the CD or the floppy drives – at least not so that I can open them.  They were under /mnt on the last program I had.  I need to be able to get to the floppy drive. Any help would be appreciated.

---

### Post by canadianwriterman on 2005-11-11
Try this, it worked for me:

Go to Web site: [http://archive.ubuntu.com/ubuntu/poo...9.6-1_i386.deb](http://archive.ubuntu.com/ubuntu/poo...9.6-1_i386.deb) . This will download the file pmount_0.9.6-1_i386.deb

Then, in a Terminal window, type:

sudo dpkg -i pmount_0.9.6-1_i386.deb

After installing this fix for pmount, you'll be able to open "Computer" and right click on the floppy icon and select "mount" or "unmount" successfully.

---

### Post by James Hunter on 2005-11-11
I didn't manage to get the file you named at the address you gave, but I did find it, and downloaded it. I arrived on the desktop, so I CDed there and entered the command you suggested. This is what I got. 

jedson@jedson:~/Desktop$ sudo dpkg -i pmount_0.9.6-1_i386.deb
(Reading database ... 57037 files and directories currently installed.)
Preparing to replace pmount 0.9.5-0ubuntu5 (using pmount_0.9.6-1_i386.deb) ...
Unpacking replacement pmount ...
dpkg: dependency problems prevent configuration of pmount:
 pmount depends on libdbus-1-1 (>= 0.50); however:
  Version of libdbus-1-1 on system is 0.36.2-0ubuntu7.
dpkg: error processing pmount (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pmount
jedson@jedson:~/Desktop$

This is over my head, now. I would seem that this pmount file -- whatever edition of it -- may be the key. 

Jim

---

