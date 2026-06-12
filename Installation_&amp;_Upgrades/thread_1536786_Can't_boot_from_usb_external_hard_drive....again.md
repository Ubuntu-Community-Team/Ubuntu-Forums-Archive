---
title: "Can't boot from usb external hard drive....again"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by waterbottle on 2010-07-22
For the first time I tried installing UNR, I encountered many problems. :p
But I was eventually successful.

Recently, I deleted my partition of UNR (with backed up files of course), to either have a clean install of it or try out a different OS (I hadn't decided yet). 

I'm in the same situation as I was when I first started. I can't boot using the external drive. I repeated the methods that didn't work just in case for some reason it worked this time.
The original post with details:
[http://ubuntuforums.org/showthread.php?t=1484354&highlight=waterbottle](http://ubuntuforums.org/showthread.php?t=1484354&highlight=waterbottle)

The solution to my problem was to use the Ubuntu live cd on another computer and mount (I think that is the correct word) the iso file to the external hard drive.
Now I get an error that says it can't install the boot loader (don't remember it exactly) using the above method. 

I also can't boot into Windows xp because grub was deleted too. :-|
My idea was to boot onto Ubuntu live from the external hard drive and restore Windows's boot loader from there (since all other methods I tried failed for that too).

This is what I don't have: external disc drive, floppy drive, other usb storage device, and Windows xp recovery cd.

I've never tried the network method since I was confused right at the start.

So my question is for all of you: What should I do? :D

---

### Post by oldfred on 2010-07-22
I still recommend a full install. I think my post in your previous thread was not clear as I mean a full install into the external drive (not internal).

You can also install grub2 to the external and boot many ISO but then you can not save anything. With a full install in the external you can fully use Ubuntu and if you want, also boot ISOs for installs. External should work on most computers you plug it into. My full install to a USB Flashdrive works on both my desktop and laptop, although I did have a bit of drive issue initially as sdf was not in search so I had to manually set hdX,Y correctly to get it to boot.

You may want it encrypted if you are carrying it around also:
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

