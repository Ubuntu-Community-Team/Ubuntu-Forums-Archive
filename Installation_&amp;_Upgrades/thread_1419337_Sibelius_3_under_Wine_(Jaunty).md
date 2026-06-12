---
title: "Sibelius 3 under Wine (Jaunty)"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by VQIF on 2010-03-01
Sup guys, looks like my limited supply of Linux-fu has run out. 

Basically I am trying to make Sibelius 3 (that's a music notation/composition programme for those that don't know) work under Wine on Ubuntu 9.04. WineHQ [suggests]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=6800&iTestingId=41967") that it should work pretty well - the only functions that fail being silly ones I neither want nor need anyway. 

So far, so hoopy. 

But when I actually go to install it (by popping the disk in and double-clicking the AutoRun.exe - though I have also tried right-clicking and telling it to open with Archive Manager, then with Wine Windows Program Loader), I always receive the following error message. 
[QUOTE=my error msg][/media/cdrom0/autorun.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/autorun.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/autorun.exe or
          /media/cdrom0/autorun.exe.zip, and cannot find /media/cdrom0/autorun.exe.ZIP, period.
[/QUOTE]

Can anyone enlighten me? Further info is obviously available if necessary.

Thanks in advance

---

### Post by gspat on 2010-03-01
I haven't had much experience with wine myself, but some things just seem to work a bit better when you copy the files off the CD first to a folder, and then do the installation. 

Wine's CD reading has always been a bit "iffy" with me.

of course, my only experience with wine has been with installing World Of Warcraft, which comes on multi-disks.

---

### Post by themusicalduck on 2010-03-01
The error suggests that it's trying to open it like an archive instead of a wine program. Did anything happen at all when you selected it to run with wine program loader?

By the way, if you want to open exe files with wine by default, then right click an exe file, go to properties and you can set it on the Open With tab.

To try and run the sibelius install try this in a terminal ```
wine /media/cdrom0/autorun.exe
``` then you can see if there are any errors.

Also, if you can find a setup.exe file instead of autorun.exe, it might be better just to try and run that instead.

---

### Post by VQIF on 2010-03-02
> **gspat said:**
> I haven't had much experience with wine myself, but some things just seem to work a bit better when you copy the files off the CD first to a folder, and then do the installation. 

Wine's CD reading has always been a bit "iffy" with me.

of course, my only experience with wine has been with installing World Of Warcraft, which comes on multi-disks.Have just tried this; same error, I'm afraid.

---

### Post by ajy0852 on 2010-03-02
Instead of double-clicking the exe, try (as suggested above) right-clicking and choose "Open with..." -> Wine.

For me, Finale 2006 has installed pretty well directly off the CD. I can't speak for Sibelius. MuseScore is a Linux program that is pretty good, although less advanced than Finale/Sibelius.

Good luck.

---

### Post by VQIF on 2010-03-02
> **themusicalduck said:**
> The error suggests that it's trying to open it like an archive instead of a wine program. Did anything happen at all when you selected it to run with wine program loader?Yup: I got a faux-XP dialog box saying "The program autorun.exe has encountered a serious problem and needs to close" etc. 
> By the way, if you want to open exe files with wine by default, then right click an exe file, go to properties and you can set it on the Open With tab.
To try and run the sibelius install try this in a terminal ```
wine /media/cdrom0/autorun.exe
``` then you can see if there are any errors.This results in a massive block of fail that I can post here if you really want to see it but otherwise won't bore you with... but no install. The aforementioned block starts off with some assertion-failure stuff though, if that helps. 
> Also, if you can find a setup.exe file instead of autorun.exe, it might be better just to try and run that instead.There isn't a setup.exe for this one. (I'd have thought it would be strange to have both a setup and an autorun?)

---

### Post by VQIF on 2010-03-02
> **ajy0852 said:**
> Instead of double-clicking the exe, try (as suggested above) right-clicking and choose "Open with..." -> Wine.

For me, Finale 2006 has installed pretty well directly off the CD. I can't speak for Sibelius. MuseScore is a Linux program that is pretty good, although less advanced than Finale/Sibelius.

Good luck.Yeah, unfortunately even though I only need the core Sibelius functions (like, y'know, writing music) rather than all the scanning and educational faff they keep bolting on, I still don't find any of the alternatives out there to be satisfactory. 

Still, that said I guess I might as well get MuseScore and have a play about with it.

---

### Post by VQIF on 2010-03-02
Another thought occurs... WineHQ did say that the version Sibelius 3 was tested under was 1.1.24, so perhaps I shouldn't be surprised that my version doesn't perform the same. So should I acquire this older version - and if so, where do I get my mitts on it?

---

### Post by themusicalduck on 2010-03-02
Usually an autorun exe just opens a menu with another button that says "Install" or some such. Then that button launches another .exe file which is the actual installer.

That's why if the autorun exe won't work, then you might be able to bypass it entirely if you can find a setup file somewhere else.

I'd suggest just looking through the folders on the CD to see if you can find another exe which resembles a setup file. There might be a folder named Sibelius with a setup.exe file in it? 

In theory having the newer version of wine is better than using the older version, although it might be worth trying the older version if this fails. Which version are you using at the moment? The older version is in the repository as package wine, the newer version is called wine1.2.

Also, I've had a quick go with musescore, and it looked pretty good.. but I had some problems with sound and could only get it to work with jack. Might work better for you though.

---

### Post by Mark Phelps on 2010-03-03
Did you check the links on the app page on the WineHQ site?  

The rating for Sibelius v3 is Bronze -- the lowest you can get other than Garbage -- typically meaning that (1) only some of the functionality works, (2) major hacks are needed to get it working.

---

### Post by VQIF on 2010-03-03
> **themusicalduck said:**
> Usually an autorun exe just opens a menu with another button that says "Install" or some such. Then that button launches another .exe file which is the actual installer.

That's why if the autorun exe won't work, then you might be able to bypass it entirely if you can find a setup file somewhere else.

I'd suggest just looking through the folders on the CD to see if you can find another exe which resembles a setup file. There might be a folder named Sibelius with a setup.exe file in it? 

In theory having the newer version of wine is better than using the older version, although it might be worth trying the older version if this fails. Which version are you using at the moment? The older version is in the repository as package wine, the newer version is called wine1.2.

Also, I've had a quick go with musescore, and it looked pretty good.. but I had some problems with sound and could only get it to work with jack. Might work better for you though.Well, I'll be damned. There *was* an alternative install.exe hiding there; I just didn't look carefully enough before. Still took right-clicking and specifying Wine to make it work, though, but now I know that, I'll know for the future. 

Now I just need to make the sound devices work... Will try this Jack business. 

Thanks to all for your help!

---

