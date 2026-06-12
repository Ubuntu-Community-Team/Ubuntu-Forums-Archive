---
title: "'Boot Error' when booting from USB"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by Venkat Arun on 2011-03-30
I want to dual boot Ubuntu and Windows XP. I have Windows XP, I downloaded the desktop iso for Ubuntu 10.10. Then using the Universal USB Installer, I prepared my pendrive (without formatting it, the filesystem is FAT32). Then I made the required changes in the boot order.
But the BIOS showed a 'Boot Error', it showed this even when I had mentioned Hard Disk (windows) as a second option.

Thanks

---

### Post by Sean Moran on 2011-03-30
> **Venkat Arun said:**
> I want to dual boot Ubuntu and Windows XP. I have Windows XP, I downloaded the desktop iso for Ubuntu 10.10. Then using the Universal USB Installer, I prepared my pendrive (without formatting it, the filesystem is FAT32). Then I made the required changes in the boot order.
But the BIOS showed a 'Boot Error', it showed this even when I had mentioned Hard Disk (windows) as a second option.

Thanks
It's been a while with no answers.  I hesitated because I'm not familiar with the Unuversal USB Installer.  I just start out burning my .iso files to a CD and go from there.  From there, I can install on somke partition or other, and install unetbootin to create my custom distros or test other distros on a USB drive.

I'd hazard a guess that the Boot Error might have something to do with the way the USB version was created, but as mentioned, I'm not sure at all on the Universal USB Installer.  Is it possible to burn the .iso onto a CD and test that out?  Then install from the CD and add unetbootin so that you can create USB drives the way I'm used to doing it?  It's just one way, although there are many, and chances are you're running a netbook or something that doesn't even have a CD-ROM drive.  Sorry if I'm not much help here, but you haven't had any other replies, so just doing what I can to help with things I don't generally know much about.

---

### Post by Venkat Arun on 2011-03-30
Thanks. I tried booting with a CD and it worked beautifully.
If anybody else is facing this problem then this was my experience.
I first tried with Universal USB Installer, which did not work (Boot Error)
Then I also tried with unetbootin, which also gave the same "Boot Error" message.
It finally worked with the CD

So if you get this problem, then simply changing the program which does the booting does not work.

Note: I had not formatted my pen drive.

---

### Post by Sean Moran on 2011-03-30
> **Venkat Arun said:**
> Thanks. I tried booting with a CD and it worked beautifully.
If anybody else is facing this problem then this was my experience.
I first tried with Universal USB Installer, which did not work (Boot Error)
Then I also tried with unetbootin, which also gave the same "Boot Error" message.
It finally worked with the CD

So if you get this problem, then simply changing the program which does the booting does not work.

**[COLOR=Red]Note: I had not formatted my pen drive.[/COLOR]**

That is cause for some consideration, but I didn't want to confuse the issue at the start.  Glad that you've got CD and unetbootin and all the same tools I have to work with.  It is a habit of mine to right click on the USB drive icon on the desktop and click on Format... every time before I start unetbootin, and it's always a FAT32 format.  I give each flash-drive the volume name to suit the colour of the drive's casing.  I've learned from experience to try to always buy different colours of flash drives, so that I can tell them apart, and the volume labels reflect the colours to help my tired old mind think of more productive matters.

Anyway, if you have time to test it out, try formatting a USB drive before running unetbootin, and make sure you're running the latest unetbootin (471) if you're intending to create a USB-Drive for 10.10 or 11.04.  One thing I know is that creating USBs with the Karmic Koala unetbootin (356?) works fine for 9.10 (Karmic) but doesn't work for Maverick (10.10).

---

