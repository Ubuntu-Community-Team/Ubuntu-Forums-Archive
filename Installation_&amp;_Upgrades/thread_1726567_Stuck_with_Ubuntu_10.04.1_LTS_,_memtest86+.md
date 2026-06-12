---
title: "Stuck with Ubuntu 10.04.1 LTS , memtest86+"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by Struggling1 on 2011-04-11
My laptop (Acer 3680) crashed some months ago when I was trying to upgrade it from 8.04 to 10.04.  I tried various fixes to no avail.  I have since bought a new hard drive in the hopes that I can revive it.  Turns out my laptop cannot read CDs, so trying to install any operating system - whether on the old or new hard drive - won't work (I tried with a Windows XP CD and an Ubuntu one - no luck).  Then, using a different laptop, I decided to download the latest Ubuntu onto a memory stick.  While this memory stick is recognised in the Acer BIOS, it will not boot, even when I put it first in line.  I get a message about BOOTMGR or something. Or was it disk error press any key to restart? I have fiddled with the boot order countless times with no luck.  Most of the time I get a 'no operating system' message.  I have since reinserted the original Ubuntu hard drive because I don't want to somehow corrupt the brand new one. It keeps running memtest86+ over and over again to the point of insanity.  When I restart and quickly press esc, it turns out the only system listed is Ubuntu 10.04.1 LTS, memtest86+.  I can't get rid of it.  At the bottom of the screen, there's the option to press c for a command line. On doing so, I see a message about minimal bash like line editing, and below, is written grub> with a flashing cursor.  What magic command should I type to make the computer work?  Any help would be greatly appreciated.  Please go easy on the geek speak because I don't even know what a kernel is.  I just want my old lap top to work again, so simple step by step instructions are what I'm after.  Ta.

---

### Post by Dutch70 on 2011-04-11
What did you use to create the bootable usb stick? 
I suggest [[COLOR="RoyalBlue"]Unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/"). If you have problems with that, please post the exact errors here & clearly define which route you'd like to take. 

Also a paragraph or 2 for readability would have been nice. ;)

---

### Post by Struggling1 on 2011-04-11
Geez.  I didn't even know that I can't just download Ubuntu onto a memory stick and insert it in the hopes that it will automatically work as a boot disk.  Thanks.  Will this in any way damage my primary laptop which I'm using (an HP with Windows 7).
I can't afford to lose this one too seeing as it's new.

I've just downloaded the Unetbootin onto my desktop, and I will try to see if I can manage to get it to make the usb stick bootable so I can put the operating system on it.  Will report back.

I know you're probably thinking this person is one sandwich short of a picnic, and you woudn't be far wrong.

---

### Post by Dutch70 on 2011-04-11
> **Struggling1 said:**
> Geez.  I didn't even know that I can't just download Ubuntu onto a memory stick and insert it in the hopes that it will automatically work as a boot disk.  Thanks.  Will this in any way damage my primary laptop which I'm using (an HP with Windows 7).
I can't afford to lose this one too seeing as it's new.

I've just downloaded the Unetbootin onto my desktop, and I will try to see if I can manage to get it to make the usb stick bootable so I can put the operating system on it.  Will report back.

**I know you're probably thinking this person is one sandwich short of a picnic, and you woudn't be far wrong.**

LOL ...nope, when I started with Ubuntu, I didn't even know the difference between a web browser and an operating system & if you look at my join date, you'll see it wasn't all that long ago.

Running Ubuntu from a live cd/usb will not change anything on your computer until you decide to install.

I do recommend making your recovery disk if necessary before I even started to play with it. Regardless of what you do with Ubuntu. 

Since you're creating usb sticks now, you may want to check out Kubuntu also. Very nice!!!

---

### Post by Struggling1 on 2011-04-11
As far as I can tell, I've now managed to make the usb stick bootable.  However, when I tried to drag the Ubuntu ISO file into it, I got an error message that there wasn't enough space!!!  Ah.  I'll have to go out and buy a new memory stick with buckets more volume and start over.  Thanks for the tips. :-)

---

### Post by Dutch70 on 2011-04-11
I've helped people on here to successfully create a usb stick with a 1GB stick. 
Have you cleared everything off of the stick and formatted it to FAT32?
How big/small is it? ;)

Have a look at this thread
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?p=10561083[/COLOR]]("http://ubuntuforums.org/showthread.php?p=10561083")

---

### Post by Struggling1 on 2011-04-11
I had not done that, but I have just formatted as FAT32 it as you have advised.  Now what?  Do I drag the Ubuntu Iso into the memory stick?

---

### Post by Dutch70 on 2011-04-11
Google gives this, as well as many other how to's.
[[COLOR="RoyalBlue"]http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/[/COLOR]]("http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/")

---

### Post by Struggling1 on 2011-04-11
You're a star, Dutch70.  I followed the link and I've started the process.  It's a tad slow.  The memory stick has 1GB.  Will let you know what happens.

---

### Post by Struggling1 on 2011-04-11
I am almost there!  I'm in a water, water all around situation.  There is not a drop to drink.  I managed to make the usb stick bootable, and voila!  I started the installation process on the beleagured Acer.  My computer had been little more than a dust trap for several months, so this in itself is a happy day.

However, it's stalled on the "who are you page."  I've entered a username and password etc.  It says "ready when you are..." though the orange line has stopped inching towards completion (if that makes any sense). It's about 80% there. The forward tab is dead, and going backwards just takes me well, backwards.  How long does this screen stay on for?  I guess I just have to be patient, eh?  Or should I go back and make changes?  I'd ordered it to write on the entire disk.

---

### Post by Struggling1 on 2011-04-11
So it turns out it had stalled simply because it took issue with my using a capital to write my name!!! [http://ubuntuforums.org/showthread.php?t=1696071&highlight=Installation+stalled](http://ubuntuforums.org/showthread.php?t=1696071&highlight=Installation+stalled)

Sheesh! :-)

HOWEVER. The problem is solved!!!  I have managed to install it!!!!  Oh, Dutch70, if only I had found you before I spent several hundred Euro buying a new laptop and getting extorted in broad daylight for the new MS Office!!!  My laptop is alive again, but better because this version of Ubuntu looks swanky.  Thank you so much for your assistance and patience :-)  
Finally, for the life of me, I can't find the place where I mark this problem as solved.   :lolflag: Ah, My two brain cells will eventually figure it out. Mwah!

---

### Post by Dutch70 on 2011-04-12
> **Struggling1 said:**
> So it turns out it had stalled simply because it took issue with my using a capital to write my name!!! [http://ubuntuforums.org/showthread.php?t=1696071&highlight=Installation+stalled](http://ubuntuforums.org/showthread.php?t=1696071&highlight=Installation+stalled)

Sheesh! :-)

HOWEVER. The problem is solved!!!  I have managed to install it!!!!  Oh, Dutch70, if only I had found you before I spent several hundred Euro buying a new laptop and getting extorted in broad daylight for the new MS Office!!!  My laptop is alive again, but better because this version of Ubuntu looks swanky.  Thank you so much for your assistance and patience :-)  
Finally, for the life of me, I can't find the place where I mark this problem as solved.   :lolflag: Ah, My two brain cells will eventually figure it out. Mwah!

Nice work Struggling1!!! Glad to hear everything is up & running. 
Another laptop resurrected & another happy Ubuntuer...lol. 
Hope to see you around more often. 

Best regards.

---

