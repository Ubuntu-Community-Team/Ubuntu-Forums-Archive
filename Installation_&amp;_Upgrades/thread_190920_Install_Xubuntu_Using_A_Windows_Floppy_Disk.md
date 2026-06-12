---
title: "Install Xubuntu Using A Windows Floppy Disk"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by mtn on 2006-06-06
Hi,

I have an old P166 that I would like to try Xubuntu on. Problem is it will only boot from a: (floppy drive) or c: (primary hard drive). What I did with Win98 was boot from a Win98 boot disk that would then allow me to access the ide cd rom  (e: ) and I could then just type "setup".

My question is, is there a way to do something similar with Xubuntu?

The PC does not have USB. It does however have a network card. I found this thread [http://www.ubuntuforums.org/showthread.php?t=176314&highlight=floppy+boot+disk](http://www.ubuntuforums.org/showthread.php?t=176314&highlight=floppy+boot+disk) 
and followed the links there. I have also read numerous other threads in this forum and searched Google but I have not found I solution to this problem. Most threads talk about installing without a cd rom or using a usb stick.

Any ideas?

---

### Post by catlett on 2006-06-06
You could try the "smart boot manager". It is an application that fits on a floppy and allows you to boot to devices not supported by your comoputer normally i.e. your cd-rom. Go here and download it. Then follow the instructions to install it to a floppy in windows.
To be a little more detailed, it is a bootloader. It will search your computer for installations and give you access to them. INCLUDING installations on cd's
Once you get it on the floppy, put in the install cd and the floppy. Restart your computer and the floppy will boot to a menu that wil give your cd-rom as an option to boot. (If all goes well)
[http://btmgr.webframe.org/index.php3?body=about.html](http://btmgr.webframe.org/index.php3?body=about.html)

It's easier from here [http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

---

### Post by rcarring on 2006-06-06
How much memory does your p166 have? If it is less than 128mb ram, dapper may not boot at all.

---

### Post by mtn on 2006-06-07
Thanks for reply. Smart Boot Manager looks really good. Unfortunatly I'm not techy enough to work it out. Having read the instructions I just don't have a clue where to start!

It only has 40Mb Ram so it might not be worth trying anyhow. If I could get Smart Boot Manager to work I might try a lighter distro thouhg not sure what that might be at the moment, would have to have read about and do some reading about SBM!

Cheers anyway

---

### Post by confused57 on 2006-06-07
Go to this page:
[https://wiki.ubuntu.com/SmartBootManagerHowto](https://wiki.ubuntu.com/SmartBootManagerHowto)

Download the SBM and rawrite files to the same folder.  You'll need to unzip the rawrite zip file.  You may need WinZip to do this...if you do, you could download the trial version of WinZip(free for 30 days) to unzip it.   Once it's extracted, format a floppy, double click on the rawrite.exe file...a window will open with a menu to copy the SBM file "as an image" to floppy.

If you are successful in making the SBM floppy, start your computer with the SBM floppy and the alternate install CD inserted, making sure your computer will boot from the floppy drive first.  The SBM menu will open with an option to boot from CD, press "enter", I have to do it 3 times consecutively.

If you're dualbooting, be sure to read through this first:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Good luck, ask if you have any other questions.  The only problem you may have is compatibility with your hardware, but Ubuntu seems to support older hardware rather well.  The Desktop(LiveCD) will not run on your computer with only 40 mb ram.  You may be able to do a server install and look into doing a low memory installation:
[https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

This last method would be your best bet...do the server install first using the alternate iso CD.

---

### Post by mtn on 2006-06-08
Thanks for this very comprehensive post, really superb. SMB worked perfectly. Took about 30 secs to create a boot disk once I got on to a MS machine. Can't believe all these years I have been mucking about with Windows/DOS boot disks!

I initially used the normal Xubuntu Desktop 386 Dapper 6.06 install disk and it started ok but then after starting install spent ages on a blank screen with the CD Rom going, so I reset the machine and burnt a Xubuntu Alternate 386 Dapper 6.06 install disk and used that. This worked fine, switched in to low memory mode straight away and went through the install process no problem. Although it could not configure the network card.

I now have Xubuntu installed but it starts up in the terminal. I only just managed to make my way around DOS (many years ago) and don't know how to start a GUI which is what I need. I did find a mention about typing this in to the terminal &#8220;sudo antivir-gui&#8221; but that didn't work. Google and this forum have turned up nothing, though that is not that surprising as I don't really know what I'm looking for.

Any tips about starting up a GUI would be really appreciated.

Thanks

---

### Post by mtn on 2006-06-09
Any help with the above would be great.

---

### Post by halitech on 2006-06-10
did you try startx?

---

### Post by mtn on 2006-06-13
Thanks for your help.I have not tried startx, i'll do that when I get a chance.

I'm new to alll this so thinkn I might have messed up by starting a new thead about this [http://ubuntuforums.org/showthread.php?t=192991](http://ubuntuforums.org/showthread.php?t=192991)

I think I'm gong to have to give up on this at the moment due to not having enough time to try and sort it. Thanks again all of the above.

Mike

---

### Post by prosper927 on 2008-01-12
I have an old Portege 620CT with windows 95 on it. The PC doesn't have a CD-ROM Drive, no usb, and no network card; it only has the floppy drive.  I would like to install Ubuntu to this PC. I read about smart boot menu but it still requires the CD ROM to which this PC doesn't have. Is there any other way to be able to install Ubuntu to this PC? My nephew who is in high school intend to use it and I would like him to learn more about Ubuntu. Please help.

---

