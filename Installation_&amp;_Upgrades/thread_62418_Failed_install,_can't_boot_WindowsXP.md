---
title: "Failed install, can't boot WindowsXP"
date: 2005-09-04
forum: Installation &amp; Upgrades
---

### Post by angrykoala on 2005-09-04
Failed to complete the base install. It couldn't load gnuplg or something because of a scratch.
After I tried an integrity check from the menu it froze up, so I had to hit the power button.  ](*,) 

Upon restart, i had a "NTLDR is missing" message for windows.  I copied over NTLDR and NTDETECT.com from the windows cd into C:\. This didn't work initially, but another restart got rid of the message, but still no windows.

Next I tried FIXBOOT and FIXMBR. FIXBOOT keeps trying to point to G:\, which is what kubuntu made, even after I directed it to C:\ on further tries. My BOOT.INI looks right from comparisons online.

Now I'm getting an "Operating system not found" (I better check this quick to be sure). Something like that anyway. It looks like all my files are still there on the Windows drive, I can play mp3's and mpg etc.
 
I can't afford to do a WINXP reinstall and lose all my stuff. If  had a dvd burner I wouldn't care.
"IF" I had to reinstall, can I just keep it focused to the c:\ and not touch my D:\ and E:\ ? I could likely copy most of my doc's and check/balance sheets over to a floppy.

This is the first time I've had a fail install of linux leave me like this, normally a fixboot and fixmbr does the trick. I'm using an old Knoppix cd to post this.

Where do I go from here?

---

### Post by davmac on 2005-09-04
In your shoes, the first thing I'd be doing is using the old knoppix disk to boot it up and copy my key files off. After that, I'd probably try and fix it with Ultimate Boot CD ([http://www.ultimatebootcd.com/)](http://www.ultimatebootcd.com/)).

---

### Post by angrykoala on 2005-09-04
think I'll delete the partitions Kubuntu made.
maybe it keeps trying to go there for some 
reason or another.

The ultimate boot cd looks rather broad. 
Not even sure what programs to start with, aside 
from the windows version. Shouldn't it be an .iso 
if it's a cd and not an .exe. Not sure I have a way to 
burn it, since my cdrom is holding Knoppix.

What other possible files might be preventing Windows 
from loading that I can check on or look for their presence?

---

### Post by angrykoala on 2005-09-04
Here's the  boot.ini

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

---

### Post by rafakl on 2005-09-04
if you want to reinstall windows, one solution is to take your hard disk off your computer, go to a friends computer, install there your hd as a slave, and backup your important files to your friend computer or burn them.

Or simply try to reinstall ubuntu.

---

### Post by angrykoala on 2005-09-04
my cd is bunked, otherwise I would. Slave, slave.... hmmm
====================


Booyakasha!!!     

I had a gentoo 2004.3 install disk and fixed the the problem by doing
cfdisk on the hd. Kubuntu had made the partition bootable at creation.
Just toggled c: and deleted the kubu drives. Problem solved and disaster 
vanquished.        :grin: 

Now to finish my dl'ing of kubu.

---

