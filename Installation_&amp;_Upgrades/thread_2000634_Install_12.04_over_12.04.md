---
title: "Install 12.04 over 12.04"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by FredVanH on 2012-06-09
Hi.  Anyone know how I may reinstall Ubuntu 12.04 on a machine that already has it (a bad one) installed?

I had 12.04 installed ok.  After a couple of months, Firefox's Download Helper stopped working dependably.  After reinstalling Download Helper and then Firefox, with no improvement, I downloaded 12.04 (via Windows 7) onto an iso file and burned the iso disc image to cd via Roxio Creator 12 Pro.  When I shut down the Ubuntu machine and powered up with the cd in its drive, I expected 12.04 to install all over again as if it had not been present before.  What really happens is that the existing 12.04 boots up and shows a cd icon marked ~.iso in the dash.

What am I doing wrong?  Any ideas would be appreciated.

Thanks,
Fred

---

### Post by deadflowr on 2012-06-09
Your hard drive is probably set to boot before the cd drive. change that setting in your bios.

---

### Post by deadflowr on 2012-06-09
I revise my initial post and say it might also be a bad burn, that results in unbootability. I've reinstalled tons of times and the two things that have ever prevented loading the live disk are either boot sequence or a bad burn.

---

### Post by VE6EFR on 2012-06-09
Do you happen to have a USB memory stick you can use? Maybe you'll have a little better luck going that route.

---

### Post by gregzeng on 2012-06-09
> **deadflowr said:**
> I revise my initial post and say it might also be a bad burn, that results in unbootability. I've reinstalled tons of times and the two things that have ever prevented loading the live disk are either boot sequence or a bad burn.

Very surprised you like making CD Coasters; so costly, slow & wasteful in very way.  

Unetbootin (flash drive) sometimes fails;  traced that to needing to GPARTED the flash drive completely in FAT32, before installing the ISO.

---

### Post by FredVanH on 2012-06-10
Thanks to all 3 of you!  Sorry I left the thread - I was going out and  thought I'd leave enough time to generate some interest.  Didn't realize  y'all are so responsive and helpful!

deadflowr - I checked and  the bios was set for cd boot first.  Just to be sure, I saved it at that  again - same result.  I guess it could be a bad burn;  although I've  had good luck with that procedure (download iso --> CD) before.  I'll  try again.

VE6EFR and gregzeng - I wanted to try the memory  stick/iso route but was unsure of how to do it.  I've done it many times  while in Windows using VirtualCloneDrive to open the iso as if it were a  cd;  but am new to it in Ubuntu.  No matter what else, I'm going to try  it after the above so I'll know how.  If you could clue me in on the  following, I'll appreciate it:
1. VE6EFR -  Once I have (copy?) the  iso on a flash drive, how do I invoke it or, more to the point, boot up  with it on a machine which has Ubuntu as the only O/S?
2.  gregzeng  -  I have now installed gparted and UNetbootin on my present ubuntu  12.04 machine.  How do I use them (sorry this sounds so newbie-ish;  but  guess what!)?
Thanks much for your advice and any more you may be willing to give!
Regards, Fred

---

### Post by darkod on 2012-06-10
If you already have ubuntu installed, it's very easy to create the bootable usb stick. You don't need unetbootin or similar.

First select an empty usb stick and format it as FAT32.
Then in ubuntu open the dash board and search for Start Up Disk Creator, and open it.
Select the ISO you want to use and the destination usb stick.

That's it.

---

### Post by FredVanH on 2012-06-10
Trying darkod's suggestion (please don't back off, VE6EFR & gregzeng!), I invoke gparted, select the flash drive, but when I go to the Partition submenu, the "Format to" option is greyed out.  I notice that the device's line in the gparted partition window has a picture of a key (locked?) on it.  How may I complete the format?
Thanks, Fred

---

### Post by dino99 on 2012-06-10
plug the stick
then unmount it (but let it plugged)
and gparted will accept it

---

### Post by darkod on 2012-06-10
> **FredVanH said:**
> Trying darkod's suggestion (please don't back off, VE6EFR & gregzeng!), I invoke gparted, select the flash drive, but when I go to the Partition submenu, the "Format to" option is greyed out.  I notice that the device's line in the gparted partition window has a picture of a key (locked?) on it.  How may I complete the format?
Thanks, Fred

In Gparted, right-click on the partition with the lock and select Unmount. The lock should be gone. You can format it after that.

Before you can use it in the Start Up Disk creator you might need to unplug it and plug it back in because it will need to get mounted again. Not sure about this, try it without and then with unplugging.

---

### Post by FredVanH on 2012-06-12
I'm not there yet but thanks to all 4 of you. I think I now have a flash drive with a bootable (I wish) install procedure on it.  Now I need to know how to use it to install!

deadflowr was right - I think I had a bad burn on the Win7-created CD.
VE6EFR and gregzeng were right - a formatted flash drive seems to be the way to go.
darkod and dino99 were right - Startup Disk Creator seems great, once I formatted it with Gparted per their advice.
My first Startup Disk Creator run went bad because I tried using as input the CD which had been created from the Win 7 download in Win 7 - it got a read error.
I then downloaded 12.04 to my Ubuntu machine and Ran Startup Disk Creator using that file in its Downloads folder as input.  It seemed to run fine!

Now I boot up with that usb flash drive inserted but instead of an install I just get my existing (the one I'm trying to install over) 12.04 opening screen.  The ubuntu.com instructions said to set the boot order so USB is first, by using F12 on bootup.  I have a Compaq 5320US, a 2001 machine, whose bootup screen has only 2 options - F12 for Network Boot (it goes nowhere) and F10 for Setup.  This takes one to the Compaq Computer Corporation Setup Utility.  In there, under the Storage submenu, is the Boot Order Option.  I have set "First" to "USB Device", as opposed to "IDE CD-Rom Drive", Diskette Drive (A", "Hard Drive (C", and "Compaq Ethernet Controller".  I exited and saved correctly and later verified that that indeed is still the boot order.  - but I still did not get the Install procedure invoked when I booted up.

Next, I went in to the Bios again and set the "USB Device" option as the_ only_ option, as opposed to before when the other options were alternate options.  This produced the same results.

What do I not know?  I just want to boot up the install with the flash drive.
Thanks for any help,
Fred

---

### Post by darkod on 2012-06-12
It seems it's not booting from your usb but that's strange. If you have an option for "usb device" in the boot order it means usb boot is supported. So, it should work.

Can you try the usb on another computer, just to confirm it's booting fine on another machine? That would rule out an error on the usb.

---

### Post by FredVanH on 2012-06-12
I have 3 other machines (mine, my wife's and our laptop) all running Win7.  I'd hate to screw them up.  I'm thinking that, if I try it, the Ubuntu 12.04 install will stop for a manual decision before it can screw up the Win7.  Without making any promises, do you agree?

In my previous post, I misspoke about one thing.  When I set "USB" device as the _only_ option, I did not get the same results as before - I got "Non-system disk or disk error.  Replace and strilke any key when ready".  This was a loop.

Thanks, Fred

---

### Post by darkod on 2012-06-12
No, no, no... Just see if it boots with it, and when presented with the choices Try Ubuntu or Install Ubuntu, select the Try just to see if it loads.

Yes, you can stop the install process but there is no need to even start it. Much safer. :)

Only work with Try Ubuntu, never start the Install Ubuntu.

---

### Post by FredVanH on 2012-06-12
Good thought!  It did work on another machine, after some tweaks.  The other machine was a ZT, new in November 2011.  It had the following boot choices:  Hard Disk, CDROM, USB-FDD, USB-ZIP, USB-CDROM, USB-HDD and Legacy LAN.

At first I chose USB-FDD because it was the first one - it did not work (went to HDD).  Then I read up and it said that USB-FDD could not be any larger than a floppy.  Then I chose USB-ZIP because it said that's like a Large floppy.  This worked!  I "tried" Ubuntu successfully! (Nice going!).

Back to my old machine .. all it has is one USB choice - "USB".
As I belatedly mentioned above, when I set the bios for "USB" _only_ (no fallback to HDD), instead of going to HDD I just got "Non-system disk or disk error.  Replace and strike any key when ready" - a loop.

Does all this mean that because my bios is too old to handle the flash drive boot, I'm screwed?  If so, any known workarounds?
Thanks for the progress so far,
Fred

---

### Post by black veils on 2012-06-12
i think you should try again with a disc, but use another burning app. the other thing is the discs you are using might not supported by the disc drive.

within a windows operating system, use this to burn your cd/dvd:

[http://infrarecorder.org/?page_id=5](http://infrarecorder.org/?page_id=5)

where there are links saying **installer**, click to download, the first is for 32-bit, the second is for 64-bit.

also, burn at the slowest speed.

---

### Post by FredVanH on 2012-06-13
Thanks, black veils, for the good advice!  I re-downloaded ubuntu 12.04 on the windows 7 side, converted the iso to a cd using ImgBurn which already was installed there, took the cd to my ubuntu machine and it installed 12.04 like a champ over the old 12.04.  This takes care of the immediate problem and I'm grateful.

I, of course, will be looking into why Roxio couldn't do the same thing as ImgBurn.  A possibility is the fact that before Roxio I had downloaded 12.04 and there was some confusion at the end of the download and maybe that iso was flawed before it got to Roxio.

Still unanswered (and I still seek the answer) is why the flash drive version, as modified by Startup Disk Creator, did not work on my machine when it did work on a newer machine  (please refer to my previous reply #15).  Any ideas, Darkon, VE6EFR or gregzeng? (Anyone - anyone?).
Thanks for all help,
Fred

---

### Post by black veils on 2012-06-13
ah yes i forgot about imgburn, i have used that before, it is good also.

as for the flash drive, the only time i have known such a thing to occur is when the bios is too old to allow it. i had to do some crazy research to install on a machine one time, it was funny. i ended up using plop boot manager, i installed it to a floppy, then got the flash drive to boot. but now that you have the cd/dvd thing sorted, you shouldnt need to boot from a flash drive (?)

---

### Post by FredVanH on 2012-06-13
Actually, I intended to use InfraRecorder as you suggested; but got confused and used ImgBurn - I had both installed.  All's well that ends well, as you just mentioned - I'm just curious about the "old bios" problem, which I surely have.  Your observations seem valuable and I'll pursue that on google.  I also saw a post somewhere referring to a fix for that and I'll see if I can find it again.  Thanks again!
Fred

---

### Post by black veils on 2012-06-13
the fix for old bios is to update the version, i dont recommend messing with the bios, but thats me.

---

### Post by FredVanH on 2012-06-13
You're probably right!  I've already checked with the HP-Compaq site for a bios update and they never heard of my model, a Compaq 5320US (c. 2001).

Your "plop" experience and the knowledge that there is some other prog out there claiming to fix the problem is still intriguing and whether I actually try them, or they go the way of all good ideas for which there isn't quite time, remains to be seen.

Anyway, I'm very grateful to you and Darkod, dino99, VE6EFR, gregzeng and deadflowr for sharing your knowledge.  I learned a lot from each of you, which I guess is what this forum is all about, and hope I may pass it on some time.  I'm leaving this thread open for now in the hope that a few more ideas on getting the flash to work on an old machine might come forward  for consideration.

Thanks again, all!
Fred

---

### Post by black veils on 2012-06-13
> **FredVanH said:**
> 
Your "plop" experience and the knowledge that there is some other prog out there claiming to fix the problem is still intriguing


well it isnt a "fix" as such, you would use a bootable cd with plop, after you boot to it, this all takes about 2 seconds, you are given a choice of other places to boot from, so you would choose usb flash drive (hdd), you should successfully boot to the flash drive, and proceed as planned for whatever you are wanting to do. but what would be the point in going through that, to boot from a flash drive, when you can boot from the cd/dvd?

maybe there is a long term fix, i saw something about installing plop to the mbr, but i really dont consider that as an option, as it could break you system, thus i dont know anything more about it. i dont understand how that could override the bios anyway, maybe it is not the intention. 

the only option is to update bios, which i personally wouldnt bother dealing with.

surely you can live without being able to boot a flash drive?  :P

---

### Post by FredVanH on 2012-06-13
You're right!  I'm done with _this_ problem.  I just like to have a bag of tricks ready for the _next_ unexpected fiasco.  I encounter a lot of stuff that seems unsolvable and later find out that 16 others had the same problem and solved it with something of which I never would have thought.

---

### Post by noobalicious on 2013-02-12
Plug the dvd rw or whatever you have into the sata 2 port. NOT sata 3.

---

