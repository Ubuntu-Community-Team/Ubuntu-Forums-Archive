---
title: "Installation Doesn't recoginze CD-Drive"
date: 2006-03-25
forum: Installation &amp; Upgrades
---

### Post by Ameralis Zaiir on 2006-03-25
Hi,

I've got a CD of Ubuntu V5.10 I got from a friend (he ordered a bunch of copies from shipit) and started the installation on my laptop.
After I choose the language and keyboard setting I get a message that the installation doesn't recognize the CD-ROM drive. (but if it doesn't recognize the cd drive how did it boot and load the installation from there? ](*,) )
What should I do?
<please note that I am kind of a noob in linux so please try and explain simply :\>

Thanks in Advance.

---

### Post by Herman on 2006-03-25
I can't tell you how to fix that exactly, but I can tell you a similar story, so that you won't feel alone.
My 'Book PC', (pictured in my avatar), was able to have the earlier 'Warty' version of Ubuntu installed in it quite readily. It worked extrememly well with 'Warty' in it too.
When 'Hoary' came out, I found I had the same problem as you are reporting, with the 'Book PC', although all our other computers had no problems having 'Hoary' installed.
Then 'Breezy' was released for general use. The 'Book PC' was able to install 'Breezy' without any problems, as were all our other computers here.

It is quite possible, then, (but not guaranteed), that an earlier or a later release of Ubuntu will go in to your machine without any problems. (Wait for Dapper, or install Dapper early and hope it will work well for you, it should be getting pretty good by now, check the opinions on others first though, please).

If it was a desktop you would easily be able to try temporarily plugging in a different CD-ROM or DVD drive, (from another machine maybe), but with a laptop you would need one that's made for it most probably.

I hope you find something here helpful, Regards, :D Herman

---

### Post by stefaninbern on 2006-03-27
I have exactly the same problem with installing Kubuntu 5.10 on my machine (Travelmate 212tx) But where do I find an older version of Kubuntu? 

It hangs when it wants to load the linux atapi cdrom driver .... it says:

Module 'ide-cd' for 'Linux ATAPI CD-ROM' is being loaded ...

Is there no other way to solve this problem?

---

### Post by Drewman on 2006-04-01
Maybe this is what happened. I found this on another forum. Perhaps it should be on the download page.

"you need to burn the content of the image
Submitted by Friedrich on Mon, 2006-01-23 08:47.
Probably you just burned the ISO file on the CD. That won't work. You must burn the content of the ISO image to the CD, not the image itself. Otherwise the CD won't boot. Therefore (when using Windows) you should use a program like Nero Burning Rom, which has a function called "burn image"."

---

### Post by stefaninbern on 2006-04-01
Thanks for your reaction, but that does not solve the problem. Because the kernel boots, i am sure i have burned the image properly. The failure takes place during the (pre-) installation proces.

---

### Post by 5-HT on 2006-04-01
[quote=stefaninbern]I have exactly the same problem with installing Kubuntu 5.10 on my machine (Travelmate 212tx) But where do I find an older version of Kubuntu? 

It hangs when it wants to load the linux atapi cdrom driver .... it says:

Module 'ide-cd' for 'Linux ATAPI CD-ROM' is being loaded ...

Is there no other way to solve this problem?[/quote] 
I had a similar issue.
There may be a few ways to get around this using some boot options.

Generally, when you are presented with the install screen, you type something along the lines of: ```
linux <bootoption> 
``` ; where <bootoption> is the bootoption without the <>

First try using 'pic=noacpi' as a boot option.
If that doesn't work, try 'irqpoll'.
If it's still a no go, using 'acpi=off noacpi' may work, but you'll loose ACPI.

This may be of help Ameralis Zaiir as well.



Hope that helps.

---

### Post by dglnz on 2006-05-08
I have this problem too installation stops at the ide-cd bit.

I have had breezy working via a online upgrade.

took a few nights to do (56k modem <G>).
worked and worked well except for th  ReseifFS falling over (and it  was by boot partition too <Grrrr>).

so you could install 5.04 and then change via sources.list al hoary references to breezy (which is what i did).

just wanted to update voa cdrom rather than then internet repositories first.

hope the above helps.

---

### Post by Herman on 2006-05-09
>  so you could install 5.04 and then change via sources.list al hoary references to breezy (which is what i did).
just wanted to update voa cdrom rather than then internet repositories first. That sounds like a good idea ! :-D (Herman)

---

### Post by Azerial on 2007-09-01
> **Ameralis Zaiir said:**
> Hi,

I've got a CD of Ubuntu V5.10 I got from a friend (he ordered a bunch of copies from shipit) and started the installation on my laptop.
After I choose the language and keyboard setting I get a message that the installation doesn't recognize the CD-ROM drive. (but if it doesn't recognize the cd drive how did it boot and load the installation from there? ](*,) )
What should I do?
<please note that I am kind of a noob in linux so please try and explain simply :\>

Thanks in Advance.

I have a similiar Problem.

First, I had a CD of 6.06 from a friend who got a bunch from shipit and ran the install on my brand new custom built pc.

Gave me some kinda Kernal Panic error and something to do with apic whatever that is (linux newb myself)

So I downloaded the iso of 7.04 and used img burn to burn it to a DVD, this time I got I/O errors and it froze up.

So I downloaded the iso of 7.04 alternate non-live with text installer, it didnt Recongize my CD Drive just as you complain about and IM like wait WHAT? how did you just boot this far into install then?

Anyhow.

I redownload 7.04 live cd, check the hash, its good, burn to a CD instead of a DVD with imgburn, at a speed of 1x.  It installs flawlessly.

So i open it up play around a little get a feel for the OS (first timer)

Everythings working fine, Time to backup all that data from my old XP Home machine that I burned to like 18 Data CDs like my firefox bookmarks, pictures, and other stuff... amazingly I actually left the porn behind XD.

WELLLLLLLL somehow, after installing fine with that CD Drive (lite on cd burner/dvd burner combo drive, SATA) It decides to tell me MY CD DRIVE DOES NOT EXIST WHEN I GO TO PLACES>COMPUTER>CD-ROM 1

,,,,,,,,,,,,,,,,,,,,,,,,  wtf?

So basically If the nice people of the ubuntu and/or tech spot (I have two threads one on ubuntu forums and another in tech spots forums about this problem) cannot fix this for me... Im gonna end up throwing Linux out the window. 

Don't get me wrong, Linux is great, or So everything else about it is. but If I cant use my friggin' cd/dvd combo drive with this OS whats the point of even keeping it on my system

my problem thread [http://ubuntuforums.org/showthread.php?t=540008](http://ubuntuforums.org/showthread.php?t=540008)

---

### Post by manbish on 2008-01-29
> **5-HT said:**
> I had a similar issue.
There may be a few ways to get around this using some boot options.

Generally, when you are presented with the install screen, you type something along the lines of: ```
linux <bootoption> 
``` ; where <bootoption> is the bootoption without the <>

First try using 'pic=noacpi' as a boot option.
If that doesn't work, try 'irqpoll'.
If it's still a no go, using 'acpi=off noacpi' may work, but you'll loose ACPI.

This may be of help Ameralis Zaiir as well.



Hope that helps.

I have been trying to install 6.06 alternate on an Acer TravelMate 202T.  So far not much success, but I have managed to get the CD-ROM recognised.  At the initial install screen when booting from the CD, I have selected the F6 option and added the word irqpoll to the string.  I have got ss far as install base packages, but these appear to be corrupt.

---

