---
title: "[SOLVED] How to Verify MD5 Checksum on Ubuntu CDs? [Tool needs to handle TXT extensio"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by OzzyFrank on 2007-08-26
Got my head around this whole "MD5 Checksum" thing recently, now find it invaluable for checking the .iso images I download (and for creating checksums for .iso image I create myself). Then it got me thinking how could I verify a CD burned properly, knowing for example that the Ubuntu CDs have the ability to check themselves. Found the answer was getting an app that could create a checksum file full of all the md5s for all files in a given folder, but found none for Linux.

I have successfully gotten **FileCheckMD5** for Windows to run in Wine, and it is used for creating MD5s for whole folders and verifying the burned result after (you have to have the .md5 file on the CD or folder too of course). Trouble is, that unlike very other MD5 file out there, the Ubuntu CD has a "md5sum.txt" file instead of one with an "MD5" or "md5sum" extension... so FileCheckMD5 fails to see it at all (and if you type it in it still doesn't work).

Now, I gather there HAS to be a way to check the various Ubuntu CDs besides the check CD option in the boot menu. This would not only save the hassle of booting a Live CD just to test it, but would be invaluable for the ones we CAN'T test (like I can't test amd64 CDs coz I am i386).

So what utility for Linux/Ubuntu is made for this purpose... checking whole folders/CDs instead of individual files... and that can handle the .txt extension?

---

### Post by wolfen69 on 2007-08-27
when you select which iso to burn in k3b, it automatically generates an md5sum which can be visually compared to the md5 you have. takes about 4 seconds once you get used to it.

---

### Post by OzzyFrank on 2007-08-27
That's interesting, thanks. Still reckon there has to be an app to do this. Actually, that's a bit different, no? I'm looking for something that can verify not one file with one md5 hash, but one that can handle the "md5sum.txt" on the finished CD. Check out that file and you will see it is full of a zillion numbers. Not something I want to compare visually, hehehe. So yeah, has to handle the single file that contains all the md5 hashes for every single file in every folder.

Still, the idea of comparing can be the last resort. I would need to find some little app that compare files for similarity, which i assume would be easy enough to find for linux. Then I could just compare the "md5sum.txt" of a tested CD (which I could just keep on my hard drive) with one just burned.

But guys, there has to be something like FileCheckMD5 (which I have to say I really recommend, even though it can't handle the .txt entension). If not, can someone please write one please? Hehe...

---

### Post by maybeway36 on 2007-08-27
The command-line md5sum tool can be used on txt files, too.
Mount your CD drive, then open a terminal and type:
```
cd /media/cdrom
md5sum -c md5sum.txt
```
You can even take the MD5 sum of the entire CD and compare it to that of the iso - use the CD drive's location in /dev (usually /dev/scd0).

---

### Post by OzzyFrank on 2007-09-02
I found a nifty little freeware utility for Windows that does the trick, and runs fine in Wine. It is **MD5summer** and is just a single .exe that you can copy to your Wine folder (or run straight off your Windows drive I suppose).

Weirdities: Will always give a message about ascii characters before scanning any of the Ubuntu CDs, but you just OK it. It will scan the Live CDs fine, but the Alternative ones all throw up 7 errors, 4 somewhere in the first third of the scan, the other 3 right near the end (this is the same for X/K/Ubuntu, and all were tested OK the standard way via the boot menu). So far in Ubuntu it worked fine for the Live CD I tested, but twice on an Alternative it seemed to stop at the same point, which is where I gather the first "errors" detected in Windows were.

So, not perfect, but it is something (at least it works in Windows "perfectly"). Would still like something like this for Linux though (without the "errors")! I just figured with all the Linux ISOs and MD5s out there, and so many of the Linux CDs having MD5s for the whole CD, there would be apps for this. Amazingly, the Windows world better caters for this need, yet I had barely touched an ISO before using Ubuntu, and I didn't even know what MD5 checksums are till recently. Now I use** MD5 Checker**, another Windows freeware app, for single ISO files, and now this MD5summer for the burned result.

So I'm not really complaining, but expressing how genuinely surprised I am that no one in the Linux world has made an user-friendly MD5 checker for all those ISOs we download. And yeah, why not one that tests the whole CD when burned (if it has one of those huge MD5sum.txt files of course, like the Ubuntu family, which many of us burn over and over again)? I know there is the command line, but for testing multiple ISOs and CDs, little gui apps are quicker.

For those who are going "Hang on, what were the errors?" in MD5summer, here's the result that speaks of missing files and the odd mismatched md5, followed by a few lines showing what the rest looks like:

.\install\netboot\pxelinux.cfg\default ERROR: X:\.\install\netboot\pxelinux.cfg\default does not exists.
.\install\netboot\pxelinux.0 ERROR: Checksum did not match.
.\pool\main\l\linux-source-2.6.20\firewire-core-modules-2.6.20-15-generic-di_2.6.20-15.27_i386.udeb ERROR: X:\.\pool\main\l\linux-source-2.6.20\firewire-core-modules-2.6.20-15-generic-di_2.6.20-15.27_i386.udeb does not exists.
.\pool\main\l\linux-source-2.6.20\pcmcia-storage-modules-2.6.20-15-generic-di_2.6.20-15.27_i386.udeb ERROR: X:\.\pool\main\l\linux-source-2.6.20\pcmcia-storage-modules-2.6.20-15-generic-di_2.6.20-15.27_i386.udeb does not exists.
.\pool\restricted\l\linux-restricted-modules-2.6.20\nic-restricted-firmware-2.6.20-15-generic-di_2.6.20.5-15.20_i386.udeb ERROR: X:\.\pool\restricted\l\linux-restricted-modules-2.6.20\nic-restricted-firmware-2.6.20-15-generic-di_2.6.20.5-15.20_i386.udeb does not exists.
.\pool\restricted\l\linux-restricted-modules-2.6.20\nic-restricted-modules-2.6.20-15-generic-di_2.6.20.5-15.20_i386.udeb ERROR: X:\.\pool\restricted\l\linux-restricted-modules-2.6.20\nic-restricted-modules-2.6.20-15-generic-di_2.6.20.5-15.20_i386.udeb does not exists.
.\pool\restricted\l\linux-restricted-modules-2.6.20\linux-restricted-modules-2.6.20-15-generic_2.6.20.5-15.20_i386.deb ERROR: X:\.\pool\restricted\l\linux-restricted-modules-2.6.20\linux-restricted-modules-2.6.20-15-generic_2.6.20.5-15.20_i386.deb does not exists.
.\dists\feisty\restricted\binary-i386\Release OK
.\dists\feisty\restricted\binary-i386\Packages OK
.\dists\feisty\restricted\binary-i386\Packages.gz OK
.\dists\feisty\restricted\debian-installer\binary-i386\Packages OK
.\dists\feisty\restricted\debian-installer\binary-i386\Pac

Actually, I might start a thread on this, as it happens for all the Alternative CDs, which are all tested fine, so am interested to see if anyone knows why... especially since the CD self-test doesn't complain about a thing, and it is reading the same checksum file. Cheers

---

### Post by OzzyFrank on 2007-09-02
Come to think of it, since I don't really need a UI just simplicity, a launcher to **md5sum -c md5sum.txt** will do fine for now (though of course still interested in any apps out there for the job). All the Ubuntu CDs have the same checksum file, and many other distros name it the same thing, so a launcher will suffice. Then I can just hit the Up key and enter and run it again for another disc.

Oh, the Alternate CD scanned without error this way, but I really should ask whether errors are presented at the end, or whether you need an extra option for that (in case I am assuming the scan went OK because there was no compaint at the end).

Thanks to maybeway36 for the md5sum code. Cheers

[EDIT] **md5sum: WARNING: 1 of 530 listed files could not be read**

Tried it on one I knew was faulty and it does indeed present you with errors at the end. For anyone interested in looking at making a script for this, then a launcher to that - since for me making simple "Application in terminal" launchers to commands like **md5sum -c /media/cdrom0/md5sum.txt** and **cd /media/cdrom0 && md5sum -c md5sum.txt** failed, follow this thread:

[http://ubuntuforums.org/showthread.php?p=3297459&posted=1#post3297459](http://ubuntuforums.org/showthread.php?p=3297459&posted=1#post3297459)

---

### Post by OzzyFrank on 2007-09-02
Actually, since the question (at least in the title) didn't specify a gui tool for this task, and using md5sum works fine, I'll mark this as Solved. I may as well include the terminal command **[COLOR="Blue"]cd /media/cdrom0 && md5sum -c md5sum.txt[/COLOR]** for those who need it, and the script I will link a launcher to:

[COLOR="Purple"][B]#!/bin/sh
cd /media/cdrom0
md5sum -c md5sum.txt[/B][/COLOR]

For me, making a shortcut (or launcher rather) to the script resulted in errors, so I'll mention for those who need it that if you can't get it running (after properly setting permissions etc) then open a terminal in that folder and type** ./scriptname.sh** (replace with the proper name). More in the thread mentioned above. Cheers

---

### Post by OzzyFrank on 2007-09-03
OK, the launcher to the script works, so it was one of those rare moments Ubuntu could have actually done with a reboot after some updates and new apps. Seriously LOVE how 95% of new apps and updated ones work 100% without the need for a reboot... so can forgive the odd time something appears screwy for the rest of the session. Usually isn't the terminal though, hehe!

OK, but now I have the terminal hopping up and doing the scan, but then it disappears. Tried a 2nd disc and did the same, so concluded the terminal was being closed as it was "the end of the job" so to speak (I'm familiar with the occasional need to put "pause" into MS-DOS batch files for this same reason). So did the old** ./md5-cd.sh** from a terminal in that folder and sure enough all is fine, and the terminal stays, allowing me to verify all went well and then run it on more CDs. So my next question is what last line do I have to add to that script to get the terminal to hang around, so I can verify the disc scanned positive and then continue using that terminal.

**WARNING**: If you do not answer this, I will start a new thread, nyuck nyuck nyuck nyuck!! (OK, it isn't THAT bothersome, but I am SO close to having a simple desktop launcher to give me the perfect md5 checker for Ubuntu CDs). Cheers

**[COLOR="Red"][[EEEEK!! This was supposed to go in the other thread, hahaha! Anyway, for those wanting the same result as I, read this thread and follow the other one from the link above.]][/COLOR]**

---

