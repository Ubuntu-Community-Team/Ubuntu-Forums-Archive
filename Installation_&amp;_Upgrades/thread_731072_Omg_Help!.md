---
title: "Omg Help!"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by gaurdianAQ on 2008-03-21
I have been trying to convert my good pc to ubuntu for the last week now but it doesnt want to work....... I have never had this much trouble installing it before............... I have tryed 4 copies of it lol the first was the one I put on my pentium 3 but when the live cd would not start and what I mean by that is it would boot and I would say start ubuntu and it would get to a certain spot and freeze, so I downloaded the text install only to find out half way through the install the disc is corrupt so then I had no OS on my PC then I got another version which could only get through enough to put the command line on and I was able to manually put on a GUI but it didnt work well, so I thought I would try Gobuntu so I burned it to disc it went through the whole install said it was installed successful but when it was booting the operating system the loading bar froze at the exact same spot as when I tryed running the live disc............ :( sorry for the long post but I am going insane not being able to use my good comp.

If you wish to know what kind of computer I am running, its an MDG Pentium D 3.0 Gig dual core with 2 gigs of ram, 500g hard drive, and a high def 256 meg graphics card, please help ASAP, it runs fine on my 500 mHz comp but not on my 3 gHz dual core lol

---

### Post by gaurdianAQ on 2008-03-21
is there anyone who can help?

---

### Post by mattk132 on 2008-03-21
Ok.  I've had this problem too.  Try starting ubuntu in safe graphics mode on the live cd.:)

---

### Post by zvacet on 2008-03-21
> I downloaded the text install only to find out half way through the install the disc is corrupt 

If you still have that iso on your HDD download same one with torrent and point download to the folder wherre existing iso is.Torrent will just check your iso and if find any corrupted files they will be replaced with good ones.After that check [md5sum](https://help.ubuntu.com/community/HowToMD5SUM) and burn iso on lower possible speed.Check Cd for errors and if you don´t find any go for install.

---

### Post by gaurdianAQ on 2008-03-22
I am using nero 7 essentials to burn the iso on windows I dont even know .torrent is lol when I tryed safe graphics mode it still froze although the disc is a bit scratched I am looking to try out gobuntu and it said the install worked fine. do you think it is just my hardware is being fussy? or should I just once again try downloading another cd or I could wait till 8.04 comes out then maybe it will work

EDIT: had less problems on my 500 megahertz pentium 3 lol

---

### Post by PmDematagoda on 2008-03-22
Use the ISO you downloaded and then burn the Live CD to a new disc again **_at a speed of 4x or less_**, do not burn the CD at a speed faster than 4x.

---

### Post by gaurdianAQ on 2008-03-23
so try gobuntu again? at a slow burn speed got it. I also bought a book called Ubuntu Linux Bible which came with an older version of Ubuntu 6.10 to be precise so if I installed that and it worked could I just upgrade from there to 7.10????

---

### Post by nachomania on 2008-03-23
Nero has, in the past, messed up my LiveCds. Try Burnatonce if you still have access to a Windows comp.

---

### Post by Pumalite on 2008-03-23
Or ImgBurn: [http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Download and install.
Go to Mode>ISO>Burn.

---

### Post by gaurdianAQ on 2008-03-23
if burn at once is free then I will try it

---

### Post by Pumalite on 2008-03-23
ImgBurn is also free and it works in a Windows environment.
(by the maker of the famous DVD Decrypter)

---

### Post by gaurdianAQ on 2008-03-24
ty I will have to try this if this next cd does not work I can upgrade from an older version to a new version right?

---

### Post by gaurdianAQ on 2008-03-24
blarg I think my comp hates me I even tryed a professional disc and it didnt work

---

### Post by Pumalite on 2008-03-24
Clean the lens in you burner or get a new one. First try your CD's in a different computer to be sure that it is your burner that is at fault.

---

### Post by gaurdianAQ on 2008-03-24
so its my cd reader ok how to I go about cleaning that do I just use compressed air?

---

### Post by gaurdianAQ on 2008-03-24
I also get this failed to locate memory thing but it goes to fast for me to see

---

### Post by gaurdianAQ on 2008-03-24
is it possible I have some sort of hardware issue and if so what is it????? I tryed looking in the bios for things that could help there was something that said run in single processor mode but with no luck did that change anything

---

### Post by Pumalite on 2008-03-24
They sell disks that when played in your burner they clean your lens.

---

### Post by aquinashub on 2008-03-24
I have had similar problems installing ANY version of Ubuntu on the exact same MDG system (3Ghz Pentium D - 2Gbs RAM - 500Gb HD). Live CD's will freeze during the splash, text install will get me to a command line, where I've installed a GUI from there, but then HAL fails to initialize, so therefor I get no Network Manager and no internet connection. I have tried Ubuntu Dapper, Feisty, Gutsy and Hardy. All have the same issue. I'm currenty using Debian Etch with Gnome and KDE installed, which works fine, except that I have to set everything up manually. I'd really like to show my mother how easy Linux is to use, since on my other machine it has not only installed fine, but everything has been working out of the box. I tried upgrading Etch to Lenny, only to find that the same problem results! There seems to be a compatibility issue with the newer kernel and these MDG-style Pentium D duos. HAS ANYONE HAD THE SAME PROBLEM? I've searched the bug trackers, and it also seems that others are having a HAL issue on some systems with kernels newer than what Etch uses, which includes any updated versions of Ubuntu. Personally, after much jotting of dmesg and various other system logs, I think this is a real bug.

Kind of makes my heart sink a bit. But alas, we will solve this problem.

If possible, I will attempt to install a base system, then manually hold back the installation of HAL (keep it older than version 0.5.10) and install the rest of the OS on top - this may take some time, but I will let everyone know when I've tried it.

For guardianAQ: When you managed to get into a GUI, did the "Failed to initialize HAL!" error show up?

Any suggestions or ideas would be freakin' awesome!

Thanks everybody!

---

