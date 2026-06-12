---
title: "diablo 2 LOD and lucid lynx"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by amnite on 2010-04-06
so has anyone had any luck with this game and 10.04? I havent, when i tried to install first i had to get past the dang safe run thing, then when i had to change disks and mount them even when they mounted it would say please insert play disk, and no matter what it wouldnt rad it. So i installed it on my windows and tried playing it from there but when i clcik on the game it says inser expansion disk which is in and mounted and can never get it to acknowledge its even there.... any help?

---

### Post by EnglishRob on 2010-04-07
Not sure if it helps, but the WineHQ site has some details on how to get it to run.  I was able to run Diablo II LOD fine on Ubuntu 9.10 without the CDs, I believe Blizzard actually released an official No CD patch.

Having installed 10.04 (Beta 1) on my laptop (fresh install from scratch) and then copied over the original .wine folder from my previous install I'm finding that Diablo II LOD starts but seems to crash on the main menu when I have visual effects enabled (I've got a basic Intel graphics chipset).  This is using Wine 1.1.14 and Diablo II LOD 1.12

I've yet to try it on any other versions of Wine (or using PlayOnLinux which is also in the Ubuntu 10.04 repositories).

If it helps, the 1.12 and a newer 1.13 patch for Diablo II LOD can be found on the Blizzard FTP site [**here**](http://ftp.blizzard.com/pub/diablo2exp/patches/PC/) and according to the Wine HQ web site [**here**](http://appdb.winehq.org/appview.php?iVersionId=315) you need to copy some files from the installation and expansion CD which aren't copied during installation.  These files are D2MUSIC.MPQ on the installation disc and D2XMUSIC.MPQ and D2XVIDEO.MPQ on the Expansion disc (the files will need to be copied into ~/.wine/drive_c/Program Files/Diablo II).  You can find the .wine folder in your home folder under places by pressing Ctrl and H to display hidden folders.

Hope this helps, I remember I had to do a bit of messing around to get it to work.  I gather it's something to do with the copy protection on the CD, this might be why it won't work in Windows?

Anyway, good luck.

Rob

---

### Post by EnglishRob on 2010-04-07
I'm just trying to reinstall Diablo II again using PlayOnLinux, turns out the d2music.mpq file is on the Play Disc rather than the Install Disc as I originally mentioned.

Rob

---

### Post by amnite on 2010-04-07
Im gonna try the lpay on linux myself, ive done all the tweaking i can with wine to no avail... I think it has something to do with the linux beta and wine's beta. Ill let u know or if you get done first lemme know

---

### Post by EnglishRob on 2010-04-07
Just another update...

I managed to get Diablo II (without the LOD patch) installed okay although there was no sound.  Luckily though someone has managed to compile a version of Wine with Pulse Audio support.

You can find the PPA [**here**](https://launchpad.net/~neil-aldur/+archive/ppa).  Just add the line **ppa:neil-aldur/ppa** into your software sources and then install the wine 1.2 package.

Rob

---

### Post by amnite on 2010-04-07
I cant even get that done with playonlinux smae issue doesnt even recognize the new cd has been inserted, really fricking annoying the heel outta me...

---

### Post by Yfrwlf on 2010-04-20
> **EnglishRob said:**
> Just another update...

I managed to get Diablo II (without the LOD patch) installed okay although there was no sound.  Luckily though someone has managed to compile a version of Wine with Pulse Audio support.

You can find the PPA [**here**](https://launchpad.net/~neil-aldur/+archive/ppa).  Just add the line **ppa:neil-aldur/ppa** into your software sources and then install the wine 1.2 package.

Rob

Also having the no sound problem.  The movies all have sound, but inside the menu and in the game itself there is no sound.  Why would an older version of Wine, in Karmic and such, be integrated with PA, but a newer version isn't?  Was working fine in Koala...

---

