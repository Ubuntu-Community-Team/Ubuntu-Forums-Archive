---
title: "Booting with the new 7.10"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by TurboPotato on 2007-11-18
Hello,

I've been trying to go through and boot the new verison of linux to my desktop machine but I keep running into little snags.  Here's what's going on...


I downloaded the new image off the main Ubuntu site and everything downloaded just fine.  So I'm trying to burn the CD with Nero 7 but when I go to burn the image Nero tells me:  

Foreign Image Settings
Type of Image:  (data mode)
Settings:
block size..
image header size

ect ect..

So I did some RTFM'ing and all I can find are half answers and no real material.  From what I understood it sounded like people wanted me to check the MD5 Hash.  I did that with the MD5summer and it told me that everything is a-ok and working correctly except its still giving me the same crap when I try to burn the image.

What am I doing wrong?

Thanks,
-TurboPotato

---

### Post by zvacet on 2007-11-18
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

I belive that Nero have** burn iso image** option.I didn´t use it for sometime but I think that is all you have to do to burn iso.If you have no luck with it download infra recorder as suggested in above page.

---

### Post by TurboPotato on 2007-11-18
OK well this dosen't make any sence now.

So it still gives me the error when I try and burn the disk with nero but if I ignore it and burn the disk anyway it burns just fine.  I'm burning it at a very low speed (8x first then I tried 4x) and it burns and verifies the data and everything rusn smooth.

So I take the disk out and put it in the computer that I want to install ubuntu on and it boots the disk to the first menu and as soon as I press enter on the "Install Ubuntu" option it pop's up with an error.

I/O Error: Error reading the Boot disk.
With what looks like an error code in the corner: 3242009F.

I burned two disks and still the same thing.

I'm really scratching my head on this one.

Any help?

Thanks.
-TurboPotato

---

### Post by zvacet on 2007-11-19
When you boot your Cd one of the options is to chek CD for errors.Select that option and see results.If you have any error on Cd try this.Download same version with torrent and point download to the folder with iso.Torrent will just chek your iso and replace corrupted files.After that burn Cd and install.

---

### Post by staticvoid on 2007-11-19
or use different burning software...? it might just be nero

sv

---

### Post by Sef on 2007-11-19
Get [Iso Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm").

---

### Post by TurboPotato on 2007-11-19
OK, so this is where it stands...

It looks like that download wasn't completely finished when I downloaded off the main Ubuntu site.  After I opened the torrent and downloaded it that way it finished and I was able to burn it to a disk and start the New Ubuntu.  However, this brings me back to square one with my real problem...

I install everything and it goes along as it normally would, asking me all of the questions and bringing up the partitioner and recognizing everything as how it should be.  I just have a single 160 IDE harddrive that I just bought from Best buy.  Linux recognizes it and so I choose the option to take up the whole hard drive and install itself.  It does this and then asks me to restart.  After I pop the disk out and restart the machine I keep getting the same thing:

"DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

So what I figured is that Grub isn't loaded correctly.  I went though, and loaded Grub into the MBR to see if that would do it.  No go, its still not seeing it as installed on the system.

Any suggestions?  I'm about at my wits end with linux and just gonna go back to windows at this point.

Help me!

Thanks,
-TurboPotato

---

