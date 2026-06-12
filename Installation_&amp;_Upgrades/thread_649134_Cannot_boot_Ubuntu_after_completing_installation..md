---
title: "Cannot boot Ubuntu after completing installation."
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by Simscape on 2007-12-24
I installed Ubuntu 7.10 on a text based installer on my second hard disk, I only have 2, and the one with Winodws XP was not hooked up when I installed Ubuntu, and its still not hooked up.
After I installed Ubuntu, it rebooted to start the new system, and said "Operating System Not Found".
I have a Emachines W2646 Desktop.
I have tried using the Ubuntu disk to boot the system, but it said boot failed.
Any help?

Thanks!

---

### Post by benrboone on 2007-12-24
I'm not sure what has happen but there are several possibilities that I know of. First, it sounds as if the grub menu doesn't appear at all.  This lead me to think that maybe your BIOS setting of bootable devices may need to be change.  One of the reason that I think this is because previously you booted to your window drive which you disconnected.  So it is possible that it is look for that drive and not finding it

---

### Post by Simscape on 2007-12-24
Yes, thats what I think also, its not finding the original drive.
I can go into the BIOS setup, but I don't know what to do to switch drives...

---

### Post by logos34 on 2007-12-24
there's the bios device boot order (floppy, cdrom, hard disk), but also a separate **hard disk boot priority** menu.
Just use the arrow keys to move the ubuntu drive to first position/top, save changes and exit

---

### Post by Simscape on 2007-12-24
I can't find anything about witch hard disk to boot first.
Do I need to set it as a Master? or Slave?

---

### Post by Simscape on 2007-12-24
Ok, never mind! It booted up!
I set the drive as the Primary Master.
Thanks for everyones help.

---

### Post by benrboone on 2007-12-24
good to hear
are you planning to dual boot if so you will probally want to add your other drive to the grub menu:
here are the settings I have use in the past, this would go in your menu.1st file.  This file is found in your /boot/grub/menu.1st  to edit it you need to use the sudo gedit command
if you have more question or don't understand then please ask before editing this file

sudo gedit /boot/grub/menu.lst 



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

