---
title: "Ubuntu version 'roll back' gone horribly wrong"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by whatisdot on 2008-09-17
Hello all,

Not too long ago, I was enjoying my version of Ubuntu 7.  As I was updating my software, I saw a button for "Upgrading" to Ubuntu 8.  I figured "why not?"  I had been having so much success with Ubuntu 7 that I thought Ubuntu 8 would have more fixes, better support, etc.
Anyway, after upgrading, my system started to freeze every now and then.  At first I thought it was a hardware problem, but I traced it to a kernel issue involved with Ubuntu 8.  After a while it became unbearable; it would freeze moments after logging in.  I finally decided I had had it and decided I wanted to roll back to Ubuntu 7.
Now, there aren't many resources for doing this.  To upgrade to Ubuntu 8 was as easy as the click of a button, but to go back to Ubuntu 7 seemed almost impossible, short of completely reinstalling.
After searching, tirelessly, I realized I would have to get creative...  I tried booting from the U7 livecd, tried to install it over the version I had (on my SATAII internal drive: 300GB) without reformatting.
Can't be done...
So I tried installing another drive (IDE internal: 6GB), installed U7 to that, and tried copying that installation to the SATAII disk.
Seemed to go ok...
Now I have all the files necessary on my SATAII drive, I believe I have GRUB configured correctly, but NOW I realized that all of the device references in /dev didn't copy from my IDE to the SATAII.
I have been searching high and low for a way to make the system recreate the files in /dev but I can't find anything relevant in my searches.
I can't get GRUB to boot because it can't find my /dev/sda (because it doesn't exist)!


For those with short attention spans:

* Ubuntu makes it easy to upgrade, but they need to make it easy to downgrade as well.

* The Question: How can I get the system to recreate the block references in '/dev'  ???

SATAII (300GB) - I am trying to fix (reformat not an option)

For now, I'm running from the U7 LiveCD.

Thanks in advance,
Dave T.

---

### Post by whatisdot on 2008-10-01
Okay, I think that some of the problem has to do with udev.  I guess I'll just have to try to mess around with it some more...  It's a shame too, I was really starting to like Ubuntu. :(

---

### Post by Therion on 2008-10-01
IMO, the "easy" way to up/down-grade is to backup Home, do a fresh install, and then do a "restore" of Home, if you will, from the backup.

---

