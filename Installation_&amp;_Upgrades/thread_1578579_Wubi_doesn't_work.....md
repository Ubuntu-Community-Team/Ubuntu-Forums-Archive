---
title: "Wubi doesn't work...."
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by PPM5895 on 2010-09-20
Hey everyone. It's my first time ever using Ubuntu and I'm using Wubi to install it. 
Whenever I try to use Wubi, it gives me some error about no disk or something about parameters. The error opens in a window that's impossible to close so I have to log off/back on or reboot to make it go away.

I'm running Windows XP and I've isolated Wubi to its own folder. 

Please help.

Thanks in advance. :)

---

### Post by wilee-nilee on 2010-09-20
Could I interest you in a real dual boot, if you have tried out Ubuntu enough from a live cd to consider this.

---

### Post by PPM5895 on 2010-09-20
I haven't tried Ubuntu at all. I'm a noob. Dx
I'm going to try a live CD right now. There should be some way to actually install it and do a dual boot from there, right?

---

### Post by wilee-nilee on 2010-09-20
> **PPM5895 said:**
> I haven't tried Ubuntu at all. I'm a noob. Dx
I'm going to try a live CD right now. There should be some way to actually install it and do a dual boot from there, right?

Yah you can install but make sure you confer with us first on the resizing of any Windows partitions. The key here is that you can resize XP with gparted in the live cd, but you want to reboot XP to let it run a auto chkdsk if it does, and make sure it is okay before installing Ubuntu.

If your computer will boot a thumb use this program to load a thumb and it will be a better trying out atmosphere, only it wont save your work in it. There is no persistence file for saving information, it runs like a live cd.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by PPM5895 on 2010-09-20
O-O
Um OK. I definitely want to keep XP and I have ~30GB left on the hard drive.

And Ubuntu is still 3 hours away from downloading... >___>

I plan on using a CD, because I don't have a 2gb flash drive anymore. :(

I'm more than a little worried that my hard drive will run out of space.

---

### Post by wilee-nilee on 2010-09-20
> **PPM5895 said:**
> O-O
Um OK. I definitely want to keep XP and I have ~30GB left on the hard drive.

And Ubuntu is still 3 hours away from downloading... >___>

I plan on using a CD, because I don't have a 2gb flash drive anymore. :(

I'm more than a little worried that my hard drive will run out of space.

I think your on the right track, Ubuntu will run better installed in a partition like normal then the Live cd or a Wubi install. Wubi does run well though when it is set up. The one thing you might want to remember about OS and a HD is that a 30% not used space, within the operating partition is recommended for peak use. So you might want to consider your options like a external to store and have a backup of everything. 

Just trying to help, you may know all of this already, it is just better to error on the side of caution for me to make sure you are aware of some things.

---

### Post by PPM5895 on 2010-09-20
Looks like my hard drive's max capacity is 149gb and I have 26.2 free gb of space. ._______."

Maybe it's time to get rid of some old files.

Thanks for all your help, willee. :D
I'll probably need more help in a couple hours when Ubuntu finishes downloading.

---

### Post by wilee-nilee on 2010-09-20
> **PPM5895 said:**
> Looks like my hard drive's max capacity is 149gb and I have 26.2 free gb of space. ._______."

Maybe it's time to get rid of some old files.

Thanks for all your help, willee. :D
I'll probably need more help in a couple hours when Ubuntu finishes downloading.

No problem, the only thing here that worries me is that when you shrink the XP partition it will be moving a lot of data towards the front of the disc so, as always I have to say make sure you have everything backed up.

Just for your help as well here is a very good defragger that optimizes=moves everything but the unmovable to the front of the disc. I would download it and defragg with the optimization until it is completely defragged. This runs pretty fast you may have to run it twice to make sure. I love free software.;)
[http://www.auslogics.com/en/software/disk-defrag/](http://www.auslogics.com/en/software/disk-defrag/)

There is also another great cleaner you may or may not be aware of that is good to use as well.
[http://www.piriform.com/](http://www.piriform.com/)

I would run both of these before proceeding, look through the ccleaner setup and if you have any questions on how to get the most out of it let me know I will be available  or another 8 or 10 hrs or at least awake anyway. Lots of other great people on the forum though that can help in case you need help and I am not here.

Post your computer model and if you know the graphic card/chip information. With Linux there are problems at times in this area due to very little manufacturers support.

Also do you have a XP install disc if not download this as well. If you need to reload the XP bootloader to the mbr at some point you will have to have a XP disc. This is insurance, say we install and everything is good except you have a driver problem in Ubuntu that can't be fixed you can just reload the MBR and your straight into XP with its native bootloader. There is a Linux bootloader called lilo that will boot windows, but I prefer recommending the native programs.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

Just burn it to a cd then you can put the iso where you need.

---

### Post by PPM5895 on 2010-09-20
This computer was just defragged a couple of days ago, so it should be good there.

---

### Post by wilee-nilee on 2010-09-20
> **PPM5895 said:**
> This computer was just defragged a couple of days ago, so it should be good there.

Cool, just trying to make sure all the ducks are in a row so to speak with XP. ;)

---

### Post by PPM5895 on 2010-09-20
I notice it says Ubuntu Development Release under your join date and stuff. Does that mean you're one of the developers for Ubuntu?

---

### Post by wilee-nilee on 2010-09-20
> **PPM5895 said:**
> I notice it says Ubuntu Development Release under your join date and stuff. Does that mean you're one of the developers for Ubuntu?

Lol, you can choose from your account a notation, it just means I'm using Maverick,  but also Lucid, Arch Linux, Slackware, and Debian as of yesterday, XP, and W7. I am just a average user really, I'm just familiar with what your trying to get done. Learned what I know though from spending way to much time on the forums, and just finding it to be fascinating. Really I have learned the most by watching the people who really know this stuff on the forum.

---

### Post by PPM5895 on 2010-09-20
Ah cool. :D

---

