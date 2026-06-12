---
title: "Blank screen after trying to update a Wubi installation"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by logico on 2010-05-26
Hey everyone.

I screwed up.  I have an EEE PC 1005HA with Ubuntu Netbook Remix installed inside XP via Wubi.

Been working fine with Ubuntu 9.10.  Update Manager said I could update to 10.04, so I went for it.

Update process seemed to go okay until time came to reboot.  Now, when I power on, I get nothing but a blank screen with a blinking cursor.  I'm not sure I can even access my BIOS.  I'll try creating a live USB with my desktop and booting my netbook with that, but I suspect that won't even work.

One area where I might have made a mistake during installation:  it asked me where I want to put the Grub loader files (or something like that).  Directions said putting it on all the partitions is often fine if you don't know what else to do.  I selected my two main partitions, C and D.  (Asus does this weird thing where every machine comes with four partitions; I don't know what the remaining two small ones are for.  My Ubuntu virtual disks are in D; the rest of my files are in C.)

Any ideas?  My impression is that this is very, very bad.

---

### Post by bcbc on 2010-05-26
Good news is your windows files should all be there. You've destroyed the windows boot sector by installing grub over it. You've also replaced the windows bootloader in the MBR.

So, if you can get a live USB going, you can fix the bootsector with testdisk. And you can install the lilo bootloader (matches windows functionality in the form shown below). See this link for instructions for the boot sector fix: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
To replace the bootloader run:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

If you can't boot ubuntu then you need a windows repair disk. And you need to run ```
fixmbr
fixboot
```

---

### Post by logico on 2010-05-26
thanks for the reply, bcbc.  i created a live usb drive for ubuntu.  i  inserted it, turned the netbook on, and again got nothing but the blank  screen with blinking cursor.  the usb drive's light did not blink, so i  believe the machine is not even checking for bootable usb drives.  i am  sure i cannot access the BIOS.

i may try removing the hard drive from the netbook and using my usb  enclosure to access the contents of that drive with my desktop.  will i  then be able to replace the bootloader using the code you gave above  (making sure i apply the lilo -M command to the right device)?  i'm new  at all this, as you can tell.  not sure if there's a better way to go  about this.

---

### Post by bcbc on 2010-05-26
try holding down the F2 key when you boot (right after hitting power button)

see [http://forum.eeeuser.com/viewtopic.php?id=35381](http://forum.eeeuser.com/viewtopic.php?id=35381)

---

### Post by bcbc on 2010-05-26
> **logico said:**
> 
i may try removing the hard drive from the netbook and using my usb  enclosure to access the contents of that drive with my desktop.  will i  then be able to replace the bootloader using the code you gave above  (making sure i apply the lilo -M command to the right device)?  i'm new  at all this, as you can tell.  not sure if there's a better way to go  about this.

Yes if this is something you're comfortable with doing, it should work fine.

---

### Post by logico on 2010-05-27
stupid me.  i could access the bios after all.  booted up from the live usb, followed your instructions about testdisk and lilo, and all is well.  thanks a lot!

---

### Post by bcbc on 2010-05-27
> **logico said:**
> stupid me.  i could access the bios after all.  booted up from the live usb, followed your instructions about testdisk and lilo, and all is well.  thanks a lot!

Cool. You're welcome.

PS on my netbook, the first partition seems to be a special boot partition, the last contains the recovery data. Perhaps it's the same on yours. Anyway, it's probably a good thing you didn't install grub to them. Although I guess testdisk would probably have worked on them as well if you had.

---

