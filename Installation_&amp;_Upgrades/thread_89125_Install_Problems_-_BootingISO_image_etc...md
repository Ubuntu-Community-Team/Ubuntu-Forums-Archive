---
title: "Install Problems - Booting/ISO image etc.."
date: 2005-11-11
forum: Installation &amp; Upgrades
---

### Post by Aryxa on 2005-11-11
Hi Guys,

I have downloaded Ubuntu ad burnt it to disc, yet it will not install.

I have downloaded the the install i386 ISO. (I have an acer aspire)
Yet, when it is on my desktop it is a Winrar file. I unzip it to another file and then I open up NERO and I burn a data disc that is bootable.

I changed my BIOS settings so only the CDROM boots and it still will not boot it.

If I try to boot the Live disc, I get some dos stuff that doesn't do anything.
Yet I can open the Live disc from Windows to browse it somewhat. :confused: 

Any thing I am missing here? I have downloaded the install disc 3 times and the live 2 times, it's killing my bandwidth, but I really want to try it.

I thought it would be easy, I cannot find any pre installation information, or any documents on this.

*pulls hair out*

---

### Post by missmoondog on 2005-11-11
going through the exact same thing too. i've downloaded the iso twice today and burned them. got a major memory error when trying to install the first time. second time, it doesn't do anything. after checking the iso file on a windows computer with winrar, it says the iso file is damaged (missing headers) i noticed both times that i downloaded the iso, it started out saying the file was 632mb's. after the download was finished, it was actually 617mb's.  what gives?

---

### Post by Aryxa on 2005-11-11
Yep, mine are 617mb also.

I have solved my problem.

I removed Winrar off my computer, and I downloaded Ubuntu from a different server. The filed showed as an .iso not as a winrar folder. I think this was the main problem. 

I then opened Nero and burnt an "ISO image to disc"

It booted first go, and I felt fuzzy as I saw the Ubuntu screen, I have waiting for!!

*wriggles in seat*

---

### Post by missmoondog on 2005-11-12
the install (Ubuntu) i was attempting last night was so new, it didn't even have unrar/rar on it. no other version of Ubuntu or anything. totally fresh, clean computer. both the copies i downloaded were while using Ubuntu on another computer and burned with graveman. i only checked the iso after attempting to install. i did attemp 1 time to download in windows and burn with nero. same result. :(


have now solved problem and happily dual booting xp pro/ubuntu 5.04 on 2 machines (snuck it in on wifes puter!) and as the soul os on 3 other machines!!

---

### Post by mercenary on 2005-11-12
Newbie alert, danger Will Robinson!

Read PC World's review of Umbuntu 5.04 and decided to try the live version.  Tastes great, less filling on my AMD XP 1300 running ME.  Then I download 5.10 and try to install as the only OS on a 13G drive that currently contains a clean Win98/ME install and it errors out while attempting to install the kernal into the target system.  Kernal package 'Linux-386'.  Since I'm not sure how to view the bootstrap log, I do the next best (only?) thing, I select Check CD-ROM Integrity.  This fails around 65% into the check.  Don't remember the big harry file name.  I make a second attempt at burning from a different download site and get similar results.  I'm using Nero 5.x and it seems perfectly happy with .iso files.  So I grab the girlfriend's HP lap top and download from a 3rd site and burn with some barebones burner software provided by HP that also seems perfectly happy with .iso files.  This time the install runs longer but in the end, I get the same results.  I run the intregity test again and it makes it 99% of the way through and then fails on a different file.

I've ordered the factory disks, but would really like to kick the tires on Umbuntu.  I was hoping the conversion would go more smoothly so I can recommend it to friends and relatives fed up with Gatesdows and all the Internet security issues.

---

### Post by taurus on 2005-11-13
Just a suggestion.  After you have downloaded the iso file and before you start to burn it (as an image file, not a data file), run a checksum to make sure that it matches the value from where you've downloaded it!!!  Sometimes MicroSuck bites a big one when you download something big...  If the chechsum matches, then you are in good shape; otherwise, you will be wasting your time and a CD (unless you use CD-RW)!  ;)

---

### Post by missmoondog on 2005-11-13
as i already stated. didn't download the iso's using microsuck anyway. is ubuntu as lousy at downloading large files too? cheksums have checked out good on every download.

---

### Post by wilford on 2005-11-13
[QUOTE=Aryxa]
I removed Winrar off my computer, and I downloaded Ubuntu from a different server. The filed showed as an .iso not as a winrar folder. I think this was the main problem.[/QUOTE]


Hi. I also downloaded Ubuntu and its also in winrar form. My question is this:

1) Do i really need to uninstall winrar on my computer, delete my downloaded ubuntu and re-download ubuntu?

2) Or can i just uninstall winrar on my computer and burn the downloaded ubuntu to a cd?

3) Or maybe i can just edit my downloaded ubuntu to .iso format?

What do you think? :D

---

### Post by missmoondog on 2005-11-13
i'm thinking the ubuntu installs are the worst part of the whole thing. out of the 10 cd's i got from them, only 2 of them will even begin the install. 1 of those 2 only gets to 42% then says try burnning the cd at a slower speed!! the last one has actually done 5 perfectly clean installs in a row now.  :(

---

### Post by aysiu on 2005-11-13
ISOs get burnt as disc images (by Nero or Easy CD Creator or whatever program you have). They should not be extracted or touched in any way before the burn. Do not use WinRar, FreeZip, WinZip, or Stuffit Expander on an ISO. Just burn it as a disc image (not data).

---

### Post by BreezyCricket on 2005-11-14
I have tried 3 different Downloads of the 'ISO' Files, made sure the checksums were correct, used 2 different burners, on 2 different PC's, and tried both Nero and Easy Media Creator with all the different combinations, with the same result.

The CD burns fine, but in all cases the Data Verification fails.

---

### Post by wilford on 2005-11-14
[QUOTE=aysiu]ISOs get burnt as disc images (by Nero or Easy CD Creator or whatever program you have). They should not be extracted or touched in any way before the burn. Do not use WinRar, FreeZip, WinZip, or Stuffit Expander on an ISO. Just burn it as a disc image (not data).[/QUOTE]

Hi aysiu. So in other words, if i downloaded it as .rar i should uninstall winrar and winzip and download it again? 
Or is there a shorter process because the download takes several hours.. :D thanks

---

### Post by mcduck on 2005-11-14
[QUOTE=wilford]Hi aysiu. So in other words, if i downloaded it as .rar i should uninstall winrar and winzip and download it again? 
Or is there a shorter process because the download takes several hours.. :D thanks[/QUOTE]
Don't look at the file's icon, I'm sure that the filename ends in .iso, or then you are downloading it from a very strange place ;) And sure you don't need to uninstall anything from your computer, just don't use use winrar or winzip to the file. They sure can open .iso-files, and that's why it has a rar-icon.

So download the image, check the md5-sum, open your favourite roaster app and burn the file as image. You could also burn it at slower speed to make sure that nothing goes wrong. I never use more than 12x for important disks..(if it doesn't still work, could also check the md5-sum of the burnt disk to make sure that the problem's not there)

---

### Post by missmoondog on 2005-11-14
yes, i know quite well how to burn an iso. even a dang nOOb at linux  like myself can do this. even though i cheated and used a windows box, i should still be able to burn the image with whatever software i happen to be using, if the file isn't foobarred to begin with. 

just so happens though that i downloaded the file earlier again today. used the first link in the list of mirrors this time. have used a different one everytime. no problems with this one at all. install went absolutely flawless.  now a happy dual bootin' fool. 

have to keep windows, mainly, just for my scanners. stupid visioneers! but, also for the lousy dependability and slowness of burning cd's under linux.

tomorrow, i start upgrading my other 4 boxes!!

---

### Post by aysiu on 2005-11-14
[QUOTE=BreezyCricket]I have tried 3 different Downloads of the 'ISO' Files, made sure the checksums were correct, used 2 different burners, on 2 different PC's, and tried both Nero and Easy Media Creator with all the different combinations, with the same result.

The CD burns fine, but in all cases the Data Verification fails.[/QUOTE] Sounds like you have a hardware issue, then. If it's not the CD, it's your computer. I hate to say it, but it's probably the case.

---

### Post by Aryxa on 2005-11-15
For me, after burning 6 discs of the winrar file of the .iso to disk, it did not work *for me*
So, unistalled it and it worked. It maybe was corrupted etc.
I have burnt .iso files before and I had no problems.

Technically you do not have to uninstall winrar as it is still an .iso file..

Do not unzip the file just burn it to disc!

Sorry for the confusion.

---

### Post by missmoondog on 2005-11-15
[QUOTE=aysiu]Sounds like you have a hardware issue, then. If it's not the CD, it's your computer. I hate to say it, but it's probably the case.[/QUOTE]

that would be to hard of a call to make for the average user. the short time i've been playing with ubuntu, that would be my very last choice. it's very easy to see that anything to do with burning files may have issues under linux. whoever burns the cd's that get sent out from shipit, proved that to me. got the 10 cd's they sent out, only 2 of those will even begin to get passed 42%.

---

### Post by BreezyCricket on 2005-11-15
Quote
```
Sounds like you have a hardware issue, then. If it's not the CD, it's your computer. I hate to say it, but it's probably the case.
```

This is the strangest problem I have ever encountered.

Using Nero v 7.0, I burned 6 ISO Files to disk. 

I had checked to make sure there was no problem with the downloads and of the 6, Ubuntu was the only one which failed verification.

I downloaded another copy, from a different source, and went through the same procedure using this copy and a few other ISO files, and again, Ubuntu is the only one that failed data verification.

I then tried using each of these 2 Ubuntu Files with a selection of other ISO's using Easy Media Creator v 8.0 from Roxio, and again Ubuntu was the only one which failed.

I repeated this scenario on another PC, using 2 more 'new' Ubuntu ISO's and another selection of images, and, once again, Ubuntu was the only one which failed, on every occasion.

???

---

