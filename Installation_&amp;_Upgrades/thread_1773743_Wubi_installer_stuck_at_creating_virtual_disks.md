---
title: "Wubi installer stuck at creating virtual disks"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by Fouzan on 2011-06-02
Hello everyone, 

I need help regarding the windows based ubuntu installer. Its stuck at creating virtual disks for the past 3 hours ... this isnt normal i assume because i installed ubuntu previously via a bootable USB and it didnt take an hour to install!!!

What to do now?? 

Thank you for any help in advance.

---

### Post by MartynT on 2011-06-02
I have a similar problem.

After asking for my initial details (install size, password etc.), the installer's progress bar quickly makes it 1/3rd of the way across and then stalls (it's been there an hour now).

I presume the file server must be down ?

It's very frustrating.  I just want to get going quickly !

---

### Post by Fouzan on 2011-06-02
Its NOT a file server issue, the files downloaded .. its during installation (creating virtual disks) that the installer simply goes to infinity and never finishes!!

---

### Post by Frogs Hair on 2011-06-02
I would suggest downloading the Ubuntu ISO and using the Wubi option on the disc . I have let friends use my discs for Wubi installations with great success . A Wubi installation goes much faster from a disc and you have a live cd and the option to dual boot as well.

---

### Post by Fouzan on 2011-06-02
The WUbi option on the USB drive is also downloading the whole damn ubuntu iso from the internet again after extracting for 12 minutes the installation from the disk??? What gives??

---

### Post by bcbc on 2011-06-03
Don't run Wubi from a USB drive. It doesn't work (except in some unique circumstances) and it will copy the entire USB partition before failing e.g. 4GB USB with single partition means it copies 4GB to your hard drive, then fails, then tries to download the ISO again.

The easiest way to install wubi is:
1. download the desktop CD from the release you want
2. download the wubi.exe from the release you want in the same folder
Run wubi from there.
(so for 11.04, go to [releases.ubuntu.com/11.04]("http://releases.ubuntu.com/11.04/")

If it's getting stuck creating the virtual disks, run chkdsk and defragment prior to running. Not sure of any other reason it should get stuck.

---

### Post by Fouzan on 2011-06-03
What do you mean same folder?

Do i extract the ISO file and run the WUBI therein? Because i had both the ISO and wubi separately before and wubi always goes to the internet to download the iso, how will it realize that i have the iso downloaded on my pc and locate it to install it?

I am sorry but this is getting confusing. I've tried installing this in so many ways already and got no joy ...

---

### Post by Fouzan on 2011-06-03
I put the ISO file and wubi in the same folder and ran them and it still went online to download the file.

This is a mess. There are no clear instructions or guide to installing from wubi anywhere or any explanations as to why the wubi installer goes online everytime n wastes time when the ISO is saved locally. I thought this process would be easier than installing windows but sadly it isnt.

---

### Post by Frogs Hair on 2011-06-03
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by bcbc on 2011-06-03
> **Fouzan said:**
> I put the ISO file and wubi in the same folder and ran them and it still went online to download the file.

This is a mess. There are no clear instructions or guide to installing from wubi anywhere or any explanations as to why the wubi installer goes online everytime n wastes time when the ISO is saved locally. I thought this process would be easier than installing windows but sadly it isnt.

If it's still going online then you either:
1. have the wrong releases mixed 
2. the CD desktop ISO has a bad md5sum

or less likely
a) you downloaded a dvd or alternate cd iso
b) you downloaded the 64bit but your computer is 32bit
c) ... something new and mysterious 

Why don't you grab the log file from the %temp% folder, and post the contents here - that will give a definitive answer. Just post it between [CODE[SIZE="1"] [/SIZE]][/CODE] tags (click # above) because it will be long.

---

### Post by Fouzan on 2011-06-03
Figured it out. It was none of the above.
I went to that wubi page suggested by frogshair (apparently no direct link from the ubuntu main site?) and it stated how to install wubi on a pc with no internet .. and then it hit me ... i shut my net down and THEN ran the installer and it installed without going online. Apparently the installer is by default set to go online to search for the latest iso?? Maybe? .. thats what i deduced.

Anyway thanks for all the effort and help extended by frogshair, martyn and bcbc.

---

### Post by bcbc on 2011-06-03
> **Fouzan said:**
> Figured it out. It was none of the above.
I went to that wubi page suggested by frogshair (apparently no direct link from the ubuntu main site?) and it stated how to install wubi on a pc with no internet .. and then it hit me ... i shut my net down and THEN ran the installer and it installed without going online. Apparently the installer is by default set to go online to search for the latest iso?? Maybe? .. thats what i deduced.

Anyway thanks for all the effort and help extended by frogshair, martyn and bcbc.

It's not supposed to do that. Post that log so we can see and I'll create a bug report if necessary.

PS great that you got it figured out though!

---

### Post by kato223 on 2011-06-03
> **Fouzan said:**
> I put the ISO file and wubi in the same folder and ran them and it still went online to download the file.

This is a mess. There are no clear instructions or guide to installing from wubi anywhere or any explanations as to why the wubi installer goes online everytime n wastes time when the ISO is saved locally. I thought this process would be easier than installing windows but sadly it isnt.


From my experience for installing WUBI, is that when you have the .ISO downloaded, use a virtual drive in Windows, there are many free ones out there like Slysoft's Virtual Clone Drive, etc..  Mount the .ISO there, and the autoplay will launch the WUBI automagically.  :)  I have found that if you have any memory card slots on your computer it will error saying that it cannot access the drive, ignore those by repeatedly clicking continue until the errors go away.  With doing the WUBI install this way, it has never gone online to download the ISOs again.

---

### Post by Fouzan on 2011-06-03
> **kato223 said:**
> From my experience for installing WUBI, is that when you have the .ISO downloaded, use a virtual drive in Windows, there are many free ones out there like Slysoft's Virtual Clone Drive, etc..  Mount the .ISO there, and the autoplay will launch the WUBI automagically.  :)  I have found that if you have any memory card slots on your computer it will error saying that it cannot access the drive, ignore those by repeatedly clicking continue until the errors go away.  With doing the WUBI install this way, it has never gone online to download the ISOs again.

Hmm i didnt load the iso on a virtual drive. I thought the Wubi extractor would figure it out itself. Besides i havent installed any of those virtual drive kits (alcohol, daemon tools etc)

bcbc, how do i get the log file?

---

### Post by bcbc on 2011-06-03
> **Fouzan said:**
> Hmm i didnt load the iso on a virtual drive. I thought the Wubi extractor would figure it out itself. Besides i havent installed any of those virtual drive kits (alcohol, daemon tools etc)

bcbc, how do i get the log file?

You don't need to mount the ISO - although it apparently works, and solves the problem of matching the wubi.exe to the ISO. But I always just make sure the ISO is in the same folder as wubi.exe - this is sufficient.

Wubi will go online (if internet is available) to retrieve the md5sums for the ISOs. If internet is not available it retrieves these instead from the ISO itself (but it favours the online ones).

Anyway... to get to the log file, open Windows Explorer and enter **%temp%** in the address bar. Then for release 11.04, the log file is called wubi-11.04-rev211.log. If you hide extensions wubi-11.04-rev211. Open it using notepad.

---

### Post by MonocleMike2 on 2011-10-19
I have had a load of trouble trying to install from USB stick.  Please see this thread:
[http://ubuntuforums.org/showthread.php?t=1863650](http://ubuntuforums.org/showthread.php?t=1863650)

In the body of that thread is the log file from after I hit Quit on the wubi install.

Can anyone tell me what and how to modify what is on the stick so that it works next time?  I still have the ISO image saved on my Windows hard drive.  I used Unetbootin to create the stick - is that the problem?  Would it work better with usb-creator which I can now get from the stick?

---

