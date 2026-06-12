---
title: "Help, Unistall GRUB and upgrade to vista"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by trevorlsciact on 2007-03-20
This isn't my computer--I would not even have a windows partition--but the person it belongs to needs some programs that are windows only.  There is no XP disk, that is the current OS.  I have a Vista upgrade disk but unless Ubuntu is uninstalled there is not enough room to upgrade to vista.  The windows partition is almost out of space but the Ubuntu partition is hardly used.  I have searched but I can't figure out how to remove grub with a vista install disk--also should I delete the ubuntu partition before or after I remove grub.  I would need to get to the XP os to upgrade to vista. BTW I kinda need to know within a couple hours.  I am usually good with sort of thing but this computer has allot of stuff and I really can't lose access to it all. Please Help.

I hope this is the right category--it is what made the most sense to me.

---

### Post by confused57 on 2007-03-20
> **trevorlsciact said:**
> This isn't my computer--I would not even have a windows partition--but the person it belongs to needs some programs that are windows only.  There is no XP disk, that is the current OS.  I have a Vista upgrade disk but unless Ubuntu is uninstalled there is not enough room to upgrade to vista.  The windows partition is almost out of space but the Ubuntu partition is hardly used.  I have searched but I can't figure out how to remove grub with a vista install disk--also should I delete the ubuntu partition before or after I remove grub.  I would need to get to the XP os to upgrade to vista. BTW I kinda need to know within a couple hours.  I am usually good with sort of thing but this computer has allot of stuff and I really can't lose access to it all. Please Help.

I hope this is the right category--it is what made the most sense to me.

You may be able to make a Win98SE OEM boot floppy & restore Windows IPL code to  mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

The Super Grub Disk is also capable of restoring Windows XP mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by trevorlsciact on 2007-03-20
could I use the utility mbrfix.exe and delete ubuntu afterwords? I think it is yes.  Would I copy the exe file to the root or the whole folder.  I think it is folder.  Someone reassure me.

Edit:  Well I did it, I am about to reboot I am scared.

Edit: it worked--thanks for the links, really lifts some weight off my sholdure

---

### Post by halw on 2007-03-20
You night want to get a copy of Gparted live cd and use it to resize the partitions to give the current windows install more room.

---

### Post by trevorlsciact on 2007-03-20
> **halw said:**
> You night want to get a copy of Gparted live cd and use it to resize the partitions to give the current windows install more room.

I did that and successfully installed vista (am I the only one who thinks it's hideous) anyways--thanks for the help

---

