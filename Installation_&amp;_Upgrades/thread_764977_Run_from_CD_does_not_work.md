---
title: "Run from CD does not work"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by JeremyP99 on 2008-04-24
Utter noob. Downloaded the 8.04 iso, burnt it to CD, booted from it, get the language selection screen, then the main menu. None of the main menu options do anything. Run Ubuntu locks the keyboard for about 5 minutes, and then I can move around the menu again, Test CD simply locked the keyboard.

What to do? 

Dell Precision 370
3mhz
4gb memory
XP SP3 all up to date

TIA

Jeremy Poynton
Frome, Somerset, England

---

### Post by Peter09 on 2008-04-24
Try burning another CD on the slowest settings, occasionally a bad CD can give problems.

PC

---

### Post by JeremyP99 on 2008-04-24
> **Peter09 said:**
> Try burning another CD on the slowest settings, occasionally a bad CD can give problems.

PC

Will do. I could however explore the CD just fine from Windows.

---

### Post by Peter09 on 2008-04-24
I think its more sensitive when trying to boot the system, any small error can cause a problem. Its worth a try.

After that try using the alternate iso, its a text only boot and avoids any problems with the Live CD.

PC

---

### Post by JeremyP99 on 2008-04-24
> **Peter09 said:**
> I think its more sensitive when trying to boot the system, any small error can cause a problem. Its worth a try.

After that try using the alternate iso, its a text only boot and avoids any problems with the Live CD.

PC

OK. Burnt with Nero @8x, and it gave an error message on being read. Burnt with ISO recorder @2x and it gave an error message on being read. DVD Decrypter @2x (verified) reads OK. I'll see what happens next, and use the alternative version if not. However, I need this one to install, am I right? 

Cheers

---

### Post by Peter09 on 2008-04-24
Not sure what you mean by this one..... the alternate CD is a text based installer - so you do not need to load the GUI. It helps on machines with little memory or where there is an issue with the video drivers or similar.

PC

---

### Post by JeremyP99 on 2008-04-24
Hmnmm. Can't get any "Live CD"s to read after selecting a menu option. I downloaded the text versions, that's OK - but there is no option to run Ubuntu, so I am no better off than before.

What I am saying is that I will not install it before I have seen it!

Perhaps I'll stick with XP :-(

---

### Post by Peter09 on 2008-04-24
Did find the following:-

> I've just been installing ubuntu on my friend's Dell Precision 370 PC.
This is the first failed install of Ubuntu I've come across :(

Firstly I had to set the SATA mode into ATA not AHCI mode (I think this
is generally referred to 'legacy' mode).  I believe this is a more
general linux kernel bug / compatibility issue.  It took me aaaages to
work this out.  If it's any colsolation the suse disks didn't work
either.



PC

---

### Post by JeremyP99 on 2008-04-24
> **Peter09 said:**
> Did find the following:-



PC
Hey ho. And they told me it was a breeze! Some other time, maybe.

---

### Post by GTengineer on 2008-04-24
The original ISO u downloaded may have been corrupt so no matter what speed you burn it at it will still be screwed up. Try redownloading the ISO and checksum before downloading it again. I have had problems like this before.

---

### Post by JeremyP99 on 2008-04-24
> **GTengineer said:**
> The original ISO u downloaded may have been corrupt so no matter what speed you burn it at it will still be screwed up. Try redownloading the ISO and checksum before downloading it again. I have had problems like this before.

Where to find the checksum? I searched for "checksum" at ubuntu.org and nothing was returned!

Thanks
Jeremy

---

### Post by GTengineer on 2008-04-24
> **JeremyP99 said:**
> Where to find the checksum? I searched for "checksum" at ubuntu.org and nothing was returned!

Thanks
Jeremy

This is how you check it:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


And you can get the md5sum for 8.04 releases here:
[http://releases.ubuntu.com/releases/8.04/MD5SUMS](http://releases.ubuntu.com/releases/8.04/MD5SUMS)

EDIT: These were updated 4/24 [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

---

### Post by ptcbus on 2008-04-24
I upgraded using the iso image of Alternate setup downloaded through bit-torrents. It worked fine. I have listed the steps [here]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

### Post by JeremyP99 on 2008-04-25
Well. Been wandering through the forum reading about 8.04 and it seems MANY people have problems. Certainly (some?) Nvidia graphics cards are not supported (was under the impression Ubuntu was a breeze hardwarewise), and there may be problems recognising SATA, and there may be corrupt images of the iso around, and I wonder - just how is this easier than the much-abused Windows?

---

### Post by JeremyP99 on 2008-04-25
> **ptcbus said:**
> I upgraded using the iso image of Alternate setup downloaded through bit-torrents. It worked fine. I have listed the steps [here]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

Ah - but I just want to run up Ubuntu and check it out before installing it.

---

### Post by JeremyP99 on 2008-04-25
Well, in at last ! Torrented download, and all well. Watch this space!

---

### Post by John L on 2008-04-25
I've been having the same problem.  As has been said, it seems to be a common experience and one which I have not experienced with previous versions of ubuntu.  

Anyway I decided to try xubuntu 8.04 and it installed no problem.  I find it extremely fast on my machine and had no problems with my 8600 gs nvidia card (desktop effects are limited in this version but it is very functional).  I'm seriously thinking about keeping it as my main os.

JeremyP99 - it sounds like you have sorted out your install problems:)

John

---

### Post by jagadeesan on 2008-04-25
Hi

I have the same issues with a install on Dell GX620.

Is there any solution to this issue?  I have tried 3 downloads and all have the same issue.  I also tried Alternate CD.  But it still loads the Language selection screen.

Is there a way to chose the text based install instead of GUI based install ??

Also, How to set the SATA mode to ATA?  Is it in the BIOS settings of the computer?

BR//Jag

---

### Post by JeremyP99 on 2008-04-25
> **John L said:**
> I've been having the same problem.  As has been said, it seems to be a common experience and one which I have not experienced with previous versions of ubuntu.  

Anyway I decided to try xubuntu 8.04 and it installed no problem.  I find it extremely fast on my machine and had no problems with my 8600 gs nvidia card (desktop effects are limited in this version but it is very functional).  I'm seriously thinking about keeping it as my main os.

JeremyP99 - it sounds like you have sorted out your install problems:)

John

John,

Yes, thanks, and spent an interesting couple of hours playing with Ubuntu this morning. Must check out what the other ?versions? are - for example, what is Xubuntu? Kubuntu? etc. 

One problem I might have is that as yet I am unable to play (lossless) wma files. As I have 2 terabytes of music attached to this PC, almost all in lossless wma format, I have a problem if I can't play them. However ... I will probably install Ubuntu alongside XP, and migrate gradually. 

Off to find how that is done shortly.

Thanks to all for advise and patient assistance. 

Jeremy

---

### Post by JeremyP99 on 2008-04-25
> **jagadeesan said:**
> Hi

I have the same issues with a install on Dell GX620.

Is there any solution to this issue?  I have tried 3 downloads and all have the same issue.  I also tried Alternate CD.  But it still loads the Language selection screen.

Is there a way to chose the text based install instead of GUI based install ??

Also, How to set the SATA mode to ATA?  Is it in the BIOS settings of the computer?

BR//Jag

My discs are SATA and I didn't need to change the Bios for any settings (yet).

---

