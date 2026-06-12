---
title: "Burning ISO"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by boochie on 2010-05-16
I've downloaded 10.04 and I'm not sure what to do next. I unzipped the file but I'm not sure which file I'm supposed to burn to disc. Also I did the md5sum check on the file and the values are always different. Any advice?

---

### Post by ki4anr on 2010-05-16
boochie,

You need to burn the .iso file to a disk. You mentioned unzipping the file and that is a similar situation that I had because I had J-zip ( similar to WinZip configured to associate the file with a zipping program. ( That is for Windows only)
I would advise opening your burning software and search the folder where you downloaded the file to and it will open up the .iso file inside the program to give you the option to burn. I personally use ImgBurn when using Windows and Brassero when using linux. ImgBurn is very user friendly and easy to use. Hope this helps!

Kev

---

### Post by Old_Grey_Wolf on 2010-05-16
I think you need to provide some additional information so that people can help you.

If you downloaded using Microsoft Windows, don't unzip the file. Use something like imgburn to burn the iso to the CD.

Did you do the md5sum on the zip file or the extracted files?

Did you download from the main Ubuntu server or did you use a bit torrent? Bit Torrents are usually faster and produce fewer errors in the download. You can find a bit torrent from the Ubuntu site > Other Download Options > Bit Torrent.

Edit: ki4anr got here first. :)

---

### Post by slooksterpsv on 2010-05-16
Windows:

I personally use ISO Recorder on Pre Windows 7 versions. Otherwise Imgburn is good too.

Linux:

Ubuntu by default includes one - CD/DVD Creator
Kubuntu by default includes k3b.

Mac OS X:

Disk Utility can burn ISO images it's located in: Macintosh HD -> Applications -> Utilities

Other:

Depends on the OS.

---

### Post by 2hot6ft2 on 2010-05-16
> **boochie said:**
> I've downloaded 10.04 and I'm not sure what to do next. I unzipped the file but I'm not sure which file I'm supposed to burn to disc. Also I did the md5sum check on the file and the values are always different. Any advice?

Hi boochie and welcome to the forum.

No need to unzip it. Check the md5sum against the .iso and if it doesn't match I hate to say it but you'll have to download it again. Now there is a better way instead of downloading the whole thing again and that's starting the download of it by torrent, then stop the torrent and close the torrent program delete what you got of the file by torrent and move or copy the one you already downloaded to where the torrent file was.

Open the torrent program again and select it and force recheck. In deluge you do that by right clicking on it and selecting force recheck.
It will check the file against the torrent and fix what's wrong with it then check the md5sum again and if it matches you're ready to burn it.

Use a program like nero or ImgBurn and select "Burn Image to Disc" not a data disc but just what I said "Burn Image to Disc".

The iso is an image of a disc. There are instructions here:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
:popcorn:

---

