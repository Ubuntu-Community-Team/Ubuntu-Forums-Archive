---
title: "first time -- having trouble"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by jasminee on 2008-10-17
Hi. I'd like to try this out. I downloaded the 8.04 i386 live version , made a cd up, and restarted the machine, but the cd wouldn't boot, it just took me to windows as usual. 

I don't think it even scanned the disc. So I changed the bios startup options to boot from cd first, and it did scan the disc, but that didn't work either, and not even windows would load - it just kept prompting me for a boot file. Then i tried disconnecting the hard disk and seeing if it forced it to look at the disc, which didn't work either. 

So I put it all back to normal and returned to windows. 

Trying to load the umenu.exe in windows which gave me a message box titled "CD Menu" with the message "CD is invalid." 

I can read the cd and see logos and text files in the directories, which look uncorrupted, so I don't know what the problem is.

Can somebody guide me. I've never used linux before. 

System I'm using for this us:
MSI K7T266 with AMD 1.4GHZ ; 256MB memory ; 8MB graphics

---

### Post by Elfy on 2008-10-17
I would first of all check that the md5sum for the download is ok - information to do so from windows here - [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

There is a also integrity check for the cd to ensure it has burnt properly - [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

You will need your pc to boot from cd first to use the burnt image.

BUT you haven't got enough memory to run the ubuntu livecd if that si what you are trying to use - try xubuntu

> At least 256 MB of RAM is required to run the alternate install CD (384MB of RAM is required to use the live CD based installer).ubuntu minimum requirements

---

### Post by ilrudie on 2008-10-17
Sounds to me like you just wrote the ISO file to a disk instead of burning the ISO image to a disk.  It's an easy mistake to make.  When you put the cd into the drive while booted into windows what shows up on the cd?  Windows doesn't ship with very good burning software and whatever 3rd party junk came from the Vendor may or may not burn ISOs correctly.  I have had good luck with [infrarecorder]("http://infrarecorder.sourceforge.net/") though.  Its free and definitly worth getting.

---

### Post by jasminee on 2008-10-17
The iso was *extracted* onto the cd, not *copied* to it. Although I made this disc in mac OSX  using it's native burning software, not windows. As I already said I can read the contents of this disc fine in explorer, such as text files and the ubuntu/debian logos in the directories. The root directory contains the autorun.inf and two .exe's ; a total of 12 items.

I expect this is really an issue of getting the machine to boot from the cd. But even if ram is insufficient, I can borrow ram from another machine. But I'd expect *something* to boot, even if there is insufficient ram. Are there relevant issues with DMA? If I enable dma for the drive on this machine in windows, I can't read discs but can write them much faster, but usually don't bother with dma. Does ubuntua require dma? This is an LG 40x16x16  DVD +/-RW.



I don't really want all this trouble. I thought linux was supposed to be less buggy than windows? :) This is a large part of why I'm considering linux. First impressions are not so good.

---

### Post by Elfy on 2008-10-17
You need to burn it as an image or iso not extract it.

If the livecd doesn't have enough ram to boot up then it won't. You could download the alternate text based installer which will run with less RAM - but if you get it installed it's not going to be much fun with 256Mb RAM.

---

### Post by ww711 on 2008-10-17
> **jasminee said:**
> The iso was *extracted* onto the cd, not *copied* to it. Although I made this disc in mac OSX  using it's native burning software, not windows. 


Use the 'burn image' option in your native Mac OS app. 

> 
I don't really want all this trouble. I thought linux was supposed to be less buggy than windows? :) This is a large part of why I'm considering linux. First impressions are not so good.

Burning an iso CD/DVD is only a small part of the process to get started into using Linux.

---

### Post by jasminee on 2008-10-18
ok. I have made a new disk and it now boots to the ubuntu menu.

I ran the integrity checker, and it said there are errors in 12 files.

Tried to load the os, and after about 60 seconds it gave an endless stream of squashfs errors. 

Is this particular failure typical of only having 256MB, or is it more likely to be due to these file errors?

I got this iso image from [virgin media's website]("http://ubuntu.virginmedia.com/releases/"), because it was the quickest ftp download available to me. I'm not permitted to use torrents from my isp.

---

### Post by Elfy on 2008-10-18
Did you check the md5sum as I suggested in post #2? - If there's an error with the file then the burns will always fail.

If there are errors found then at some point it's going to fail.

Even if the burn is good then you'll likely have problems booting the livecd, although that's more likely to show as it not booting.

If you can make a swap partiton before you boot the livecd it should help it to boot, but even installed it will be slow.

---

