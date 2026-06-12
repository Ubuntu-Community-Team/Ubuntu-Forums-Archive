---
title: "Installation Failed"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by Zucriy Amsuna on 2010-01-17
[COLOR=indigo]"The installer encountered an eror copying files to the hard disk:[/COLOR]
[COLOR=indigo][/COLOR] 
[COLOR=indigo][Errno 30] Read-only file system[/COLOR]
[COLOR=indigo][/COLOR] 
[COLOR=indigo]This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. ..."[/COLOR]
 
[COLOR=navy]Before I try changing CD drives, re-formatting the hard drive (again), or cleaning the CD drive, I must add that Xubuntu did open. I got rid of all traces of the previous operating system (WinME), and Xubuntu seems to work pretty well. The installation stopped at 41% of copying files. Should I aim for a finished installation or is this fine? Are there any programs that I will need to install to fix? Thanks.[/COLOR]

---

### Post by Jose Catre-Vandis on 2010-01-17
Sounds like this is on a fairly old PC. Had similar problems with an old laptop that didn 't like reading the CDs, even after checking the integrity and md5sum (you might wish to try those two?)

If you have a USB port you could always create a USB stick installation and try that way.

Also, you could download the Alternate CD and try that way. 

You may need to run saome checks on your HDD as well

Will be worth going through the full install to avoid problems later, but if it works for you now......

---

### Post by Zucriy Amsuna on 2010-01-17
[COLOR=navy]Thanks. I'll try the alternate CD first.[/COLOR]

---

### Post by Leppie on 2010-01-17
using the alternate cd, install the base system only
once able to get into the base system, install the xubuntu desktop:
```
sudo apt-get install xubuntu-desktop
```this makes you less dependent on the cd (but more dependent on your internet connection, but using a dsl connection this shouldn't be a problem).

---

### Post by Zucriy Amsuna on 2010-01-17
[COLOR=navy]The alternate CD claims to have an abundance of corrupt files, thus preventing the installation of anything. Everything before that worked fine.[/COLOR]
[COLOR=#000080][/COLOR] 
[COLOR=#000080]Also, there was no Internet connection detected; I've no idea why it couldn't detect anything. It's a direct connection from the router.[/COLOR]

---

### Post by Leppie on 2010-01-17
did you check the md5sum after downloading and after burning the image?

---

### Post by Zucriy Amsuna on 2010-01-17
[COLOR=navy]How do I do that? This page doesn't help: [/COLOR][[COLOR=red]https://help.ubuntu.com/community/HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")[COLOR=navy] Nothing seems to work. I downloaded the .iso on a different computer--WinXP (because the WinXP was about 80x faster with the downloading...), and made the CD. The computer I wish to have as Xubuntu is now a 41% downloaded Xubuntu that seems to work fine after trying a few things.[/COLOR]
[COLOR=#000080][/COLOR] 
[COLOR=#000080]I watched a video of the installation of Ubuntu, and the percentage bar zipped from about 60% to 100%. So maybe it doesn't really matter all that much, but just in case...[/COLOR]
[COLOR=#000080][/COLOR] 
[COLOR=#000080][/COLOR]

---

### Post by Leppie on 2010-01-17
> **Zucriy Amsuna said:**
> [COLOR=navy]How do I do that? This page doesn't help: [/COLOR][[COLOR=red]https://help.ubuntu.com/community/HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")[COLOR=navy] Nothing seems to work.
on this page, if you scroll down to the windows section (after the mac section) a linkis provided to the small freeware tool [winmd5sum.]("http://www.nullriver.com/index/products/winmd5sum") i've used it on windows, so i know it works.

[/COLOR]> **Zucriy Amsuna said:**
> [COLOR=navy]I downloaded the .iso on a different computer--WinXP (because the WinXP was about 80x faster with the downloading...), and made the CD.[/COLOR]
this is funny, because my xubuntu install has much better download results than my xp install.

> **Zucriy Amsuna said:**
> [COLOR=#000080]I watched a video of the installation of Ubuntu, and the percentage bar zipped from about 60% to 100%. So maybe it doesn't really matter all that much, but just in case...[/COLOR]
i don't remember how the progress bar behaves...

---

### Post by Zucriy Amsuna on 2010-01-17
[COLOR=navy]I am installing Xubuntu on an old WinME computer; the thing is naturally slow and would have taken over 40 hours to download the .iso (or so it said as the remaining time slowly continued to rise over the course of downloading for ten minutes and only having downloaded 500 KB in that time).[/COLOR]
[COLOR=navy][/COLOR] 
[COLOR=navy]The md5sum is normal; nothing seems wrong with the files in other ways, either. I think it may be the hard drive (and possibly the CD drive) being too old.[/COLOR]

---

### Post by Leppie on 2010-01-17
if the bios supports usb booting, you could try creating a usb installer.

---

### Post by Zucriy Amsuna on 2010-01-17
[COLOR=navy]It does. However, on my journeys through the interwebs, it hasn't solved any one of the problems other people were having. Also, I lack a flash drive of capable capacity at the moment... I might try it later when I get a good flash drive.[/COLOR]

---

