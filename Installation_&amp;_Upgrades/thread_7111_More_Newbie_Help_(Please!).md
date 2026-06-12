---
title: "More Newbie Help (Please!)"
date: 2004-12-04
forum: Installation &amp; Upgrades
---

### Post by usasma on 2004-12-04
OK, I got Ubuntu installed (several times)  First time Grub didn't work, only got a command line - second time got a Grub error 17 (which I tracked to the wrong hard drive being specified in menu.lst - for some reason Grub wants to use (hd1,1) when it should be using (hd0.1)

Questions are:

1)  How do I save the changes in the Grub editor?  I can only boot into Ubuntu if I boot from the editor.

2)  Once in Ubuntu, can I log in using the "sudo" command to edit the menu.lst file in Grub?  If so, what do I do?  I can't figger out what menu item to open to enter the command "sudo gedit /boot/grub/menu.lst".  Also, is that syntax correct?

3)  I've successfully updated FireFox and want to import my settings from Windows to Ubuntu.  I can't seem to access any of my NTFS/FAT32 partitions/drives from Ubuntu   If possible, could someone point me at info on how to do it?

4)  Is there any way to log in as root in Ubuntu?  I know that sudo should do what I want ito do with as root - but it just seems too darned complicated to me

 :mrgreen:

---

### Post by bazuka on 2004-12-04
I'm a noob to this also, so take it with a grain of salt.

1. Dunno that one.

2. Do alt+F2 and type in " gksudo gedit /boot/grub/menu.lst " when promted, type in _your_password, not root.

3. Make directories under /mnt/ to mount the drives into, then do " sudo mount -t NTFS /dev/hda? /mnt/yournewdirectory1 "  for NTFS shares... replace NTFS in that line with VFAT if you're mounting a Fat32 partition.

4. Computer > System Configuration > Login Screen Setup > "Security" Tab > First Option entry.


Hope this helps a little.

Note on #2, if you can't get it to open, do alt+F2 and type in "gksudo gedit"  and enter your password, then manually open /boot/grub/menu.lst

---

### Post by usasma on 2004-12-04
Thanks for the info, I'll try all of it!  One quick question tho' - why "gksudo" instead of just "sudo"?  The reason I ask is because most of the stuff that I've read says sudo and makes no mention of gksudo.  Thanks again!

---

### Post by TravisNewman on 2004-12-04
sudo is for command line use, gksudo is for using the "run application" dialog and menus. If it called sudo instead of gksudo it would be waiting for input from the command line that doesn't exist.

---

### Post by usasma on 2004-12-04
AHA!  I see said the blind man!

Anywhooooo - I got into some sudo/gksudo mode that let me copy and edit the menu.lst file - and now all seems well with the Grub loader.

Still haven't fiddled with mounting the NTFS/FAT32 drives - but I got a Gmail account to store all the info on that I wanted to transfer.  Heck, this'll make me abandon Windows all the sooner! :mrgreen: 

Another question tho' - I added my only user to the sudo group - is this good or bad (I'll be the only one using this system)? 

Once again, thanks for all the help!

---

