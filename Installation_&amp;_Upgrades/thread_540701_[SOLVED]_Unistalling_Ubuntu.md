---
title: "[SOLVED] Unistalling Ubuntu?"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by blasteryui on 2007-09-01
Ok, I inserted Gpartion and I went to my second HDD, I deleted the partions that Linux was on, in other words I deleted everyting on the second HDD, when I restarted my pc it says loading Grub Loader, then it says like error 22. I didn't touch my first hard drive, so my Windows XP is still on it and in tact, now I dont have my windows XP cd so I cant repair it that way, so what do I do?

---

### Post by merlinus on 2007-09-01
Try supergrub.

Download:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Info on use:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by blasteryui on 2007-09-01
Ok, so what do I do? I am looking at the pictures and reading and it looks like I boot windows from the CD, so to boot windows for now on I have to always use the CD...? All I wanted to do was get rid of Ubuntu and all of this happens.

---

### Post by merlinus on 2007-09-01
You burn the .iso (small download) to a cd as a disk image, no more than 4x speed.  Then:[LIST=1]
[*]boot from the cd
[*]English Super [COLOR=#000000]Grub[/COLOR] Disk
[*] Windows
[*]Fix Boot of Windows[/LIST]-merlin

---

### Post by blasteryui on 2007-09-01
I burnt the iso to a disk, the iso is on the disk using my laptop, I burn the iso to a dvd-r. My computer can read DVDS I put it in press f12 and it says it wont read, its saying press f1 to try again or f2 for something else. I dont think it burnt to the cd, I used magic iso, and selected the ISO and it burnt to the CD.

---

### Post by blasteryui on 2007-09-01
> **merlinus said:**
> You burn the .iso (small download) to a cd as a disk image, no more than 4x speed.  Then:
[LIST=1]
[*]boot your SGD CD-ROM
[*]English Super [COLOR=#000000]Grub[/COLOR] Disk
[*] Windows
[*]Fix Boot of Windows[/LIST]-merlin

Ok that sounds right, but read what I wrote below your post, about burning it to a dvd...

---

### Post by merlinus on 2007-09-01
Did you burn the .iso as a disk image?

-merlin

---

### Post by Officer Dibble on 2007-09-01
> **blasteryui said:**
> Ok that sounds right, but read what I wrote below your post, about burning it to a dvd...

Can you boot from a floppy disk drive?

If so, either on a spare Windows PC or a friends Windows PC download a Windows ME/DOS boot disk, boot from it, and then type:

fdisk /mbr

That will fix your problem... well almost... you're then left with the problem of being left with Windows. Get Ubuntu back on there man... :)

---

### Post by blasteryui on 2007-09-01
How do you do that? I looked at the CD it has the 2 folders and the file on the cd, but again it doesnt boot on my other computer, so yeah maybe its not on boot mode or what not. Ok what do I download and what do I do to burn these files as a image file?

---

### Post by merlinus on 2007-09-01
Your burner software may have that option.  If not, infrarecorder is free software for windows that will do this.

[http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/)

-merlin

---

### Post by blasteryui on 2007-09-01
Ok, its downloaded, what are the options I choose?

---

### Post by Officer Dibble on 2007-09-01
#-o

---

### Post by merlinus on 2007-09-01
Open your burner software and look for an option to burn a disk image, NOT a data disk.  Then select the .iso and burn it at 4x.

-merlin

---

### Post by blasteryui on 2007-09-01
No, I downloaded the program you said.

---

### Post by merlinus on 2007-09-01
If you click on the file in windows, it will install, and place an icon on the desktop.

Then use it to burn the .iso to a disk.

-merlin

---

### Post by blasteryui on 2007-09-01
Ok, I clicked Burn image, selected the ISO am going at 4x, all insert the CD and do that windows thing you said, if all works all come back and say it works, Thank you for everything!

---

### Post by blasteryui on 2007-09-01
I burnt the files to the DVD, I inserted the DVD to the first disk tray, it still wouldnt work, so I inserted it into the second disk tray, the DVD one I believe and its still not reading, so either its not burning properly, or my computer isn't reading the disk... I have no CDS either. Only DVDS

---

### Post by merlinus on 2007-09-01
Just to be certain, is your computer set up to boot from the dvd drives before the hard drives?

-merlin

---

### Post by blasteryui on 2007-09-01
I dont think so. Because I had the UBUNTU cd out, when I had it on duel boot, I either chose Ubuntu or windows xp home, so I didnt want ubuntu anymore so I put on gparted, clicked on my second HDD and deleted everything, the 40 gigs, the linux thing, and some other space, BUT didn't toutch the first HDD other words the XP HDD, so I just want to be able to run XP again. But it trys to load the grub when I turn my pc on but it says error 22..

---

### Post by blasteryui on 2007-09-01
Is there a way to put theses files on to a USB way? Such as a SD card or a MP3 player my MP3 player can hold any file, up to 8 gigs is there any way like that? DVDS seem not to work..

---

### Post by merlinus on 2007-09-01
Yes, but your computer will need to be able to boot from the usb device.

Of course, you can always buy a few CD-Rs, and supergrub and gparted will fit on minis.

-merlin

---

### Post by blasteryui on 2007-09-01
Ok, I just checked the DVD and that inra didnt burn the iso to the cd it just said it did and kept the dvd blank, I chose 4X and clicked the image option.

---

### Post by blasteryui on 2007-09-01
Ok, I know the files burnt, I checked the disk on my parents laptop, what i am using right now. They are there, I insert it to my computer and it still wont read t just saying press f1 to try again, I am almost certain my computer cant read it, I DOUBT its the files... So what else can I do, I tried just restarting my computer and lettng it load but again cannot load grub error 22.

---

### Post by merlinus on 2007-09-01
So the cd booted your parents' computer, but not yours?

If so, I would suspect your cd-dvd drive.  Maybe you can borrow an external one.

-merlin

---

### Post by blasteryui on 2007-09-01
Nah, read my other thread.

---

### Post by be4truth on 2007-09-01
Hi blasteryui,
I am surprised that you ask for help but don't follow it really. It feels like you going to a doctor and then not following the advice. Hope you don't blame the doctor afterwards if you health doesn't improve.
If somebody ask you to burn a Cd why do you burn a DVD? Not following the help may lead to more problems instead of solving them. Look how much time merlinus already put into this story.

---

### Post by blasteryui on 2007-09-01
I am happy that hes helping me, and no he knows I am using a DVD, I do not have cds:(. I am sorry but i am really upset, I am running ubuntu off the cd right now, do I need to install ubuntu to the second HDD again and wait tell I get cd's then delete ubuntu off the second HDD then run supergrub? THat makes sense to me, but is that what I should do?

---

### Post by be4truth on 2007-09-02
I hope you understood the situation. When you install Ubuntu on whatever drive it needs to install a boot loader. Usually Linux systems make a backup of your MBR before they replace it with their own. This information sits somewhere in the boot folder ( I never used it.) This boot loader enables you to boot in several operating systems.
To get rid of this boot loader the easiest way is to take your Windows XP cd and go into the rescue shell and fix the MBR. A Windows 98 boot cd does the same job. A bootable windows 98 boot disk on a usb stick (if your bios supports this), a CD or a floppy - where it sits. As long as you can boot it and execute the command to rewrite the Windows MBR entry.
Now pls answer theses questions one by one and as simple and clear as you can:

Does your parents laptop have a floppy drive?
Do you have a friend close by with a XP CD?
Do you have a friend close by with CDs? Maybe your neighbour has? 
Does the computer you want to rescue have a floppy drive?
Do you know how to change your bios settings so that the computer boots from CD and not from the hard drive?

With this information we can go further.

As a quick fix you could reinstall Ubuntu where is was before. It will place a new boot loader in the right place and you will be able to boot into Windows. But this doesn't solve your problem. It only helps you to use your computer again in Windows.

---

### Post by blasteryui on 2007-09-02
> **be4truth said:**
> I hope you understood the situation. When you install Ubuntu on whatever drive it needs to install a boot loader. Usually Linux systems make a backup of your MBR before they replace it with their own. This information sits somewhere in the boot folder ( I never used it.) This boot loader enables you to boot in several operating systems.
To get rid of this boot loader the easiest way is to take your Windows XP cd and go into the rescue shell and fix the MBR. A Windows 98 boot cd does the same job. A bootable windows 98 boot disk on a usb stick (if your bios supports this), a CD or a floppy - where it sits. As long as you can boot it and execute the command to rewrite the Windows MBR entry.
Now pls answer theses questions one by one and as simple and clear as you can:

Does your parents laptop have a floppy drive?
Do you have a friend close by with a XP CD?
Do you have a friend close by with CDs? Maybe your neighbour has? 
Does the computer you want to rescue have a floppy drive?
Do you know how to change your bios settings so that the computer boots from CD and not from the hard drive?



With this information we can go further.

No.
No, I have a windows XP disk.. I clicked repair, I pressed 1 as in the first hdd it asks me to put a administrator password, I put in the password I used to log on to windows, and it doesn't work it lets me do it three times but it then says your try are over or something and if I press enter it reboots, so if you can help me out with that, i can use my windows xp disk.
No
Yes
No..

So basically either you can try and help me with the XP thing or the floppy thing my pc does have a floppy:). by the way.. I am on the messed up pc now I am running ubuntu off the cd, haven't installed it yet, but am running it.

---

### Post by be4truth on 2007-09-02
You know that the administrator password is not the passwd you use to log in. If you installed XP yourself you were asked to supply the admin password. But chances are good that there is no admin passwd. Did you try just to press enter?

---

### Post by PmDematagoda on 2007-09-02
I realize this is off topic, but feel it's necessary, blasteryui, it's better if you learned how to use the BIOS because it can help you a lot, I myself learned how to use the BIOS just by going through and stringing the different terms and options properly to what they do, you can do better by asking someone to help you to make changes in the BIOS.

And did you try be4truth's suggestion about the password because Windows does allow the admin password to be empty whereas in Linux it can't.

---

### Post by blasteryui on 2007-09-02
> **be4truth said:**
> You know that the administrator password is not the passwd you use to log in. If you installed XP yourself you were asked to supply the admin password. But chances are good that there is no admin passwd. Did you try just to press enter?

The windows xp disk that I inserted into the computer isn't the same xp disk that was used to install windows on this computer though. This disk was used to install xp on my other computer, when I did install it to the other computer I never had to put a admin password. So would pressing enter really work? If so all try it now, but would it work?

---

### Post by PmDematagoda on 2007-09-02
It's not the CD that really matters but the computer since the CD cannot be written to. So if you set up a password on to the computer you are trying to set up you need to use that, though since it is in repair mode it could be that there is no password.

So you can try be4truth's suggestion.

---

### Post by blasteryui on 2007-09-02
OK here it goes, prays to the Ubuntu god...

---

### Post by blasteryui on 2007-09-02
Ok thank you guys, it worked I cant believe after trying to figure out 2 hours after attemping the XP thing all I had to do was press enter... Wow.. Thanks again guys I am on XP now:P. The reason why I wanted to get rid of Ubuntu is because I want to run imac, because it has imovie and all thoes things.

---

### Post by be4truth on 2007-09-02
Do me favour and mark the thread as solved. Go tothe top of this page. Go to Thread Tools and mark it solved. That helps. Hope you stay connected to Linux.

---

### Post by blasteryui on 2007-09-02
Haha ok, well the whole reason I wanted Ubuntu was for beryl but beryl wouldn't install it was weird.

---

### Post by PmDematagoda on 2007-09-02
Enjoy your Mac but remember Linux is developing not like Windows so as time passes Linux may come as being the best OS so don't be out of touch with the Linux world. tc

---

