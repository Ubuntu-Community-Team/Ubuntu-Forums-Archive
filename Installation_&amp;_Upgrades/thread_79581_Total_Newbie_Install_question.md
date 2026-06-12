---
title: "Total Newbie Install question"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by mattothegeek on 2005-10-20
I have downloaded the PC Live version onto my Imac and now would like to try Ubuntu out on my old Dell.  It is a 450mhz, 256k, 20g, win2000, 1999 vintage machine....

Excuse my ingnorance, but i simply do not know how to proceed from here....Do i have to do anything special when i burn the cd (ie. make it bootable) or do i simple burn the .img file as it came down?

And on to the install, how do i make the dell recognize the live-cd?  Do i just launch win2000 and go to the cd and click auto-run or do i have to boot somehow from the cd on start-up?

FYI, the dell is not currently connected to the internet..does it need to be just to evaluate Ubuntu??

Thanks to anyone that may be able to help.  I just thinking that based upon what i have seen so far, Ubuntu might just be what i need to reseurrect this old machine and make it (eventually) a useful member of my home network.

---

### Post by jonrkc on 2005-10-20
I'm not absolutely clear on what you wish to do, but it sounds like you'd like to see a bit of what Ubuntu is like, by operating the Live CD version for a while.

The Live CD is bootable already.  (So would be your install CD(s) if you decide to install a system later.)  All you need to do is instruct, usually by changing a BIOS setting, your computer to boot from CD as first choice.  It may already be set up that way--it's convenient, as it will ignore an empty CD drive, and go on to boot from hard drive, but will boot from CD instead (like in case of emergencies) if there's a bootable CD present in the CD drive.

To evaluate features of Ubuntu, you would only need an Internet connection going if you wanted to run the browser (Firefox) on the Web or the email client (I think they chose Evolution) to evaluate that. You would have to poke around a little to set up your Internet connection after you were all set with the Live CD desktop running.

Your time of day may very well not show right.  It may take some jiggling to get that right, too, but if you're not going to mount your good files and alter them, but rather just play around on the Live CD, you could just leave it wrong.  I would set it back to within a few seconds of the right time, however, before going back to your regular operating system, otherwise if you're using an NTP time server, and your clock is way wrong, automatic adjustment may be impossible.

---

### Post by mattothegeek on 2005-10-20
[B]I'm not absolutely clear on what you wish to do, but it sounds like you'd like to see a bit of what Ubuntu is like, by operating the Live CD version for a while.
[/B]

Yes, that is exactly what i would like to do.

[B]The Live CD is bootable already. (So would be your install CD(s) if you decide to install a system later.) All you need to do is instruct, usually by changing a BIOS setting, your computer to boot from CD as first choice. It may already be set up that way--it's convenient, as it will ignore an empty CD drive, and go on to boot from hard drive, but will boot from CD instead (like in case of emergencies) if there's a bootable CD present in the CD drive.
[/B]

If i need to change BIOS, would i do that by pressing F8 on startup or some other way?

Also, so i just need to burn the entire file as is (ie. no opening and selecting files from within) and that would be sufficient to boot to?

Thanks for your help...

---

### Post by jonrkc on 2005-10-20
Access to BIOS differs from computer to computer but it's usually via the delete key or one of the Fx keys.  On the computers I've had, there's a brief message right after the memory check when you turn it on from a cold start, that tells which key to press.  

Once you've downloaded the "Live" CD image, all you have to do is to burn it to a CD-ROM or DVD-ROM using the "ISO image" option in your CD burning program.  If you're using the Roxio software, the help file will tell you exactly how to do it.  It's just one step, burn it and you've got your CD ready to go.  The only precaution to take is not to burn at too high a speed (if you have a choice), because the CD must be EXACTLY like the image you downloaded or else it won't work right.  Speeds that produce minor errors acceptable on regular data CD's are sometimes (not always) too high to produce the absolutely faithful copies needed for bootable CD's like installation or "live" ones.  

If you have a way to check the "MD5SUM" figure of your downloaded image against the figure posted on the Web for that file you downloaded, you can tell if the download was error-free.  I'm sorry that I don't know the way to do this with Windows.  It may well be in the very complete Windows help files, though.  Or in the Roxio help files.  The MD5SUM figure is a checksum figure that only matches if there are zero differences between the downloaded and source file.

Be sure to post back with your results!  Good luck.

---

### Post by dbott67 on 2005-10-20
[QUOTE=mattothegeek]....Do i have to do anything special when i burn the cd (ie. make it bootable) or do i simple burn the .img file as it came down?[/QUOTE]

When you burn the .ISO to the CD, you need use your CD burning application (i.e. Nero) to select 'burn an image/iso'.  It's not the same thing as making a CD bootable.  There is generally a specific option to burn an image to disk.

-Dave

---

### Post by Herman on 2005-10-20
Mattothegeek, click on my signature link and you will find some information on BIOS'es that you might find useful. I'm sorry but you'll have to do a lot of scrolling for it.
There is a bit of information in there on how to get your BIOS boot order set up, but it's way down close to the bottom of the page, and it's a very long page.
You'll know when you get there, it's got big blue pictures, (you can't miss it!)

 There's an award BIOS in the example, but you might be able to figure out what to do with other kinds of BIOS'es too from seeing that example and applying a some logic and reasoning.

There's a lot of other information in your way before you get to that though, I'm sorry about all the scrolling. It's my first web site and I just wanted to get it all done, I'll fix it up as time goes on.

---

### Post by jonrkc on 2005-10-20
And keep in mind that once you have your boot order set up for CD first, hard drive second, you can leave it that way; it won't delay booting more than about one second (to check if there's a disc in the CD-ROM drive), and that way you'll always be set to boot from CD-ROM should the need arise, or for making system repairs, adjustments, etc., that need to be done from OUTSIDE the installed system (because the repairs or adjustments may change the actual contents of components needed to RUN the installed system).

---

### Post by mattothegeek on 2005-10-23
Thank you all for your help....but, I am still not able to boot from the Live CD i burned...

I reset the bios to boot from cd-rom first, but i see it spin,,but then it immediately goes to the screen to allow for Win 200 or Nt boot..

very frustrating...any ideas?

---

### Post by jonrkc on 2005-10-23
I wonder if you burned it at too high a speed, OR didn't burn it with the ISO image mode, OR got some error during download.

1.  Did you check the md5sum given on the website against the one for the image you downloaded?  Just do the command md5sum followed by the name of the image you downloaded, to get its checksum, then see if it matches exactly the figure given on the website where you downloaded from.

2.  If it matches, the image is OK.

3.  That would rule out too high a speed burning, and error during download.  I don't know if failing to use the special ISO mode in the software would still produce a CD-ROM that gave the correct md5sum but wouldn't work anyway, or not (I suspect it wouldn't).  But you might double check that you used the special mode that Nero (or whatever burning software you're using) provides for burning an ISO image to CD-ROM.  As another poster said, it's different from making a regular CD-ROM that is capable of booting.  It's a special kind of image.

Hope this helps.

Your machine is obviously set up OK, so that's out of the way.

Once you get this situation licked, it will be a breeze to do similar operations in the future, so don't be discouraged.

---

### Post by UbuntuPaul on 2005-10-23
mattothegeek and I are in the same boat; I just downloaded the iso and this is my first post.

Thanks to all who helped him - you also helped me.  My question (related) is:
Upon boot of the iso image, are you given a choice of partition or does Win2K go bye-bye immediately?  I purposely did not try the "Live" CD because I figure I'm doing it or I'm not!  Full speed ahead . . . just want to know if it blanks out all partitions.

I am in the process of investigating all possible "help" sources and also searching these forums to minimize my repeating questions - but this was my first search and I've already learned a lot.  Thanks to all of you.

---

### Post by jonrkc on 2005-10-23
You will have a choice for dual-booting.  I've never done it that way because I only use Linux, but you can keep Windows and have Linux too, provided you have enough disk space.  The installation disk should walk you through the decision-making, but beware that it IS possible to wipe out whatever's on your disk (including Windows) if you don't think about what you're doing.  

Somebody who dual-boots might offer advice here.

---

### Post by UbuntuPaul on 2005-10-23
Thank you very much, johnrkc.  I was actually finished, partitioned, both running well.  Instructions couldn't have been easier.  I also didn't know it came with Palm Synching software - fantastic!

This will do me for the time being until I learn it - then I'll be like you and just have Ubuntu.  Simple things like how to uninstall, equivalent of "notepad" in a quick launch icon to copy from the web, and Intellipoint mouse driver so I get my extra mouse buttons - all simple stuff and all things I will figure out this week.

The look of the thing is marvelous, it's very "self explanatory," and I couldn't be happier.  I hit the "partition amount" button with a little nervousness - but what the heck - if it had wiped anything, probably all the better!

Take care and thanks - be back when I've studied a little more!  Anyone with tips on the above mentioned - feel free to email me.  Hopefully soon I'll be able to do some "helping" in return.  Cheers! /p

---

### Post by jonrkc on 2005-10-23
Glad things worked out so well.  The mouse customizing can be a little tricky, but you will find lots of posts about it both here and elsewhere.  

I use a Palm Tungsten E and have used JPilot for the desktop half of my operation since abandoning Windows in January '03.  JPilot is not extremely elegant, but it's reliable and easy to use.  The KDE synch thing is probably more attractive, but I've not tried it.

My worry now is what I will do with my personal data--I've kept it in Palm form since about 1994, or whenever the Palm Professional came out--when my Tungsten E gives out eventually.  Palm is going to Microsoft OS and so I won't be using Palm instruments anymore.  This has preoccupied me for the past few weeks and I don't have a solution yet.  I suspect I'll just go back to a paper planner so I can still have backups on desktop.  But that means mastering the fundamentals of a Linux database and devising my own templates, etc.--something I would have enjoyed a LOT more several years ago (since I'm 65 now and have better things to do).

Oh, well.  Kind of off-topic, I know.

Both Nedit and Gedit are good easy-to-use editors to use instead of Notepad.  Nedit in particular has loads of customization and special features for programmers, etc.  The classic many Linux users swear by, and the rest swear at, is Emacs.  Investigate it and you'll see why.

Good luck getting further into things.  Oh, and I like the looks of my Linux setup a lot more than I did Windows, too.  And I can work exactly the way I want to, as far as desktops, etc.  That's a plus.

---

### Post by mattothegeek on 2005-10-24
Thank you all for your help, but i think what i should do is just order the Live CD and full-install cd and go from there....My problems could very well be in the cd burning that i did on my Imac G5....i have had some minor issues burning cd's before and this could be another one....

I will get back once i receive the cd's in the mail...thanks for your help...

A little off topic...but, the real reasons i wanted to try Ubunutu are twofold: 1. as i said, this is an "old" dell that i know will work fine with an operating system that is not as bloated and ineffecient as windows and 2.) i want my 11-year old son (who is fairly computer proficient) to understand other op systems as we use an Apple at home (which he loves), Windows at school (which he tolerates), and Linux....

Would be curious to hear from the experts on here about my logic...and again thanks for the help.

---

### Post by jonrkc on 2005-10-24
I'm not an expert (in this field, anyway), but to me your logic is impeccable.  It's very useful to be able to understand at least basic usage of different OS's.  And almost any Linux distro will suit an older computer better than Windows will.

Sorry your CD-burning didn't work out.  Hope you enjoy the discs you're ordering!

---

