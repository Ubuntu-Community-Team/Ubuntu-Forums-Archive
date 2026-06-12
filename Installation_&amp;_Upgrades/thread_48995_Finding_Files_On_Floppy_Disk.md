---
title: "Finding Files On Floppy Disk"
date: 2005-07-14
forum: Installation &amp; Upgrades
---

### Post by Lambert on 2005-07-14
linux newbie, I'm trying to install gnome-ppp. I've downloaded it on a win machine and put it on a floppy formatted in fat. It's a .deb extension file.

I've put the floppy in my laptop running ubuntu and I go to applications>systemtools>File browser and from there I searh around. I'm trying to copy the .deb file into my /home directory so I can install. But I can't seem to find the file?

I've gone into /media/floppy and /media/floppy0 and there's nothing there. (that's where /dev/fd0 looks to be mounted.

I've read that floppy drives work differently in linux then windows and all I know is windows. You put in the floppy and go over to a: and there it is. 

This may be a dumb question but I'm baffled. How do I find the files on the floppy and copy them to /home?

Also does /dev/fd0 mount on boot automatically or do I have to mount it each time I reboot or unmount it?

---

### Post by varunus on 2005-07-14
Open up a terminal and try typing "mount /dev/fd0" or "mount /media/floppy0" or "mount /media/floppy" (depending on your setup).  Make sure to type "umount /dev/fd0" before ejecting.

I don't think GNOME automounts floppies; one thing you may want to use is to add a "disk mounter" to your panel; you can unmount and mount everything from there, adn the icons will change if stuff gets mounted by the volume manager.  Heck, I use one just because its easier to have my CD and removable drives on my panel. 

Good luck.

---

### Post by Lambert on 2005-07-14
[QUOTE=varunus]

I don't think GNOME automounts floppies; one thing you may want to use is to add a "disk mounter" to your panel; you can unmount and mount everything from there, 
Good luck.[/QUOTE]


Would you mind expanding on a disk mounter and where to get one or find out more about this? Something in the repository I can download and install?

did mount /dev/fd0 and it worked...thanks

---

### Post by varunus on 2005-07-14
The disk mounter is a panel applet included with gnome.  You can right click a panel, choose add to panel, and choose "disk mounter" from the list.  It will show you icons for every drive in your computer and whether they're mounted or not; you can mount and unmount them with a left click (which will bring up a menu).  (Similar to the icon windows shows you for "safely remove drives").

EDIT:  Typos.

---

