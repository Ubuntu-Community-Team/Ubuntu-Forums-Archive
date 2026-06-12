---
title: "Installation on a laptop problem"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by scottrick49 on 2007-02-20
Hi,

I am trying to install 6.1 onto my laptop.  My laptop currently has windows xp on it but i have created a partition with 10gb for Ubuntu.  I am using the live cd to install. 

I am able to boot to the CD with no problem.  I get to the Ubuntu start-up menu and choose install.  All goes well for a little bit but sometime right after the screen with the Ubuntu logo and the progress bar, my CD-rom seems to run into trouble.  It will start and stop reading the disk over and over and over again.  After a long while (like 10 minutes or so) the installation will fail, due to i/o errors.

I don't have any trouble with the cd rom when i am using it in windows.  I even burned the installation cd's with the drive I am using to read them.  I burn music cd's all the time with the laptop and they play fine in my car, etc.  I know that sometimes laptops have more issues and was wondering if anybody has seen anything like this in the past.  Any help is appreciated.

---

### Post by Fully216 on 2007-02-20
Did you check to make sure the image you downloaded was not corrupt?

Since you use windows, I would recommend using md5summer or md5 checker to make sure.

[http://www.md5summer.org/download.html](http://www.md5summer.org/download.html)
[http://www.softpedia.com/get/System/File-Management/MD5-Checker.shtml](http://www.softpedia.com/get/System/File-Management/MD5-Checker.shtml)

---

### Post by scottrick49 on 2007-02-20
No I didn't.  Good suggestion; I will try this when I get home.

---

### Post by deeppurple on 2007-02-20
I too have had exactly the same problem for days  !!!

except it doesnt error it just keeps on access the hard disk !!

On the screen the big no entry sign appears with

..
There was an error starting the GNOME settings daemon

Some things such as ....

The last error message was

Did not receive a reply. Possible reasons include... blah blah blah


Any clues

---

### Post by stchman on 2007-02-20
> **scottrick49 said:**
> Hi,

I am trying to install 6.1 onto my laptop.  My laptop currently has windows xp on it but i have created a partition with 10gb for Ubuntu.  I am using the live cd to install. 

I am able to boot to the CD with no problem.  I get to the Ubuntu start-up menu and choose install.  All goes well for a little bit but sometime right after the screen with the Ubuntu logo and the progress bar, my CD-rom seems to run into trouble.  It will start and stop reading the disk over and over and over again.  After a long while (like 10 minutes or so) the installation will fail, due to i/o errors.

I don't have any trouble with the cd rom when i am using it in windows.  I even burned the installation cd's with the drive I am using to read them.  I burn music cd's all the time with the laptop and they play fine in my car, etc.  I know that sometimes laptops have more issues and was wondering if anybody has seen anything like this in the past.  Any help is appreciated.

Hello, I have installed a few distros of linux and I have found this to be the best method if you have Win 2000/XP installed.

You say you have a 10G partition with nothing on it.  You need to make that partition free space.  Right mouse on My Computer and lick manage.  Then go to Disk management.  Take that 10G and delete that partition.  This will cause the drive to become free space.  Ubuntu will ask you if you want to use available free space.  This should work.

---

### Post by scottrick49 on 2007-02-20
I have checked the checksum and it is correct.  

When I said I have a 10 gb partition with nothing on it, i meant that htere was no partition either.  It is simply free space, as you describe.  That hasn't been the problem.  The installation has never reached the point where it asks for the drive I want to install to.

---

### Post by scottrick49 on 2007-02-21
Anyone else have any ideas?

---

### Post by steve on linux on 2007-02-22
I have a similar problem - see the thread I started yesterday (no replies yet).

I tried the alternate install with a similar result.  What kind of laptop are you using?

---

### Post by Fully216 on 2007-02-23
I would also double check to make sure you choose the correct install discs.  For example, AMD processors have a different install compared to intel systems.

Did you play around with the live CD at all or just go directly to the install?  I would try browsing the internet, listening to music, etc to get a feel for the compatibility between the distro and your hardware.  It is usually a good indication if it boots fine however.

---

### Post by scottrick49 on 2007-02-23
I know I am using the correct CD.  

I have not tried to boot using it as a live CD - i will try that once I get off from work.  I have noticed a similar problem when booting with a Gentoo live CD - the cd drive seems to start and stop again and again with no result.  I wonder if my cd drive has some problem with linux?  Both distributions would reach the boot menu and begin the process fine, but after a bit they would run into this problem.

---

### Post by rasbach on 2007-02-23
You wouldn't happen to be using a SD-R2412 model CD/DVD combo drive would you?  I have been pulling my hair out trying to get Ubuntu on my Laptop (again).  I've used three different install disks (all check out good),  and I've been using them for many installs too! 

I have a Toshiba A35-s159 and it has that model drive, which is very common (Toshiba/Fujitsu/HP/Compaq).  It almost seems as though my drive is failing and causing the install issue, but I'm seeing laptop CD-ROM issues pop-up on these forums all of a sudden.

---

### Post by rasbach on 2007-02-23
I should add some info:

-I do not have any other OS installed
-I am using both Live and Alternate CD's
-This is true for both 6.06 and 6.10
-This laptop has seen many Linux installs (Ubuntu, SuSe, RH, FC2,3,4)


The problem seems to occurr when it's going through the process of retrieving packages from the CD and fails to grab package 294 or something like that.

---

### Post by scottrick49 on 2007-02-23
I'm not sure what model my cd-drive is; i'm not actually sure how to check that on the laptop, since i don't think it says on the outside and i'd rather not open my laptop up to find out.  I will try to find out once i get off work.

My drive will start spinning for one or two seconds, and then stop, start again, then stop, over and over again until eventually the install fails.  Just like you said, I have tried many different installation CDs and the problem happens with all of them.  I want to say it is a mechanical problem with my drive but because it works fine in windows, I don't think it is.  Heck I burn cd's with the same drive all the time and use them with no problems.

---

### Post by rasbach on 2007-02-23
Have you been able to burn CD's/DVD's with it since you started having this issue?

---

### Post by scottrick49 on 2007-02-23
yes; i burned a new cd just the other day and i was listening to it fine in my car;  i've been trying to get ubuntu installed on and off for a couple weeks now

---

### Post by Russty of Oz on 2007-02-23
I am having this problem too, I am trying to install ubuntu on a friends Acer laptop.  I have tried a Ubuntu live CD and also tried the Ubuntu Ultimate DVD's for 1.1 and 1.2.  With the live CD and with Ubuntu Ultimate 1.2 after the initial install screen the screen goes black and the disc is still loading.  All the discs are OK as I have used them on my 2 desktop computers.

---

### Post by Russty of Oz on 2007-02-24
I just found this on the net, the only thing is I don't know where to type it???

[B]1. Install from CD

I am not sure what happened when I use default parameter (just press enter), the kernel just hangs. But it is easy to bypass the problem. You can install with parameter:
linux acpi=off noacpi
After that, it will go smoothly[/B]


Can anyone help here?

---

### Post by scottrick49 on 2007-02-27
yeah i would like to try that too; anybody know how to give it that parameter?

---

### Post by Fully216 on 2007-02-28
To boot with these options, you need to edit options in the grub boot menu found in /etc/grub/menu.lst.  On a side note, these options are architecture specific.  They mainly apply to i386 and amd64 systems.  You might also try pci=routeirq in additions to pci=noacpi and acpi=off parameters just in case a driver is getting the interrupt request messages mixed up.

If you have a non-working version of install, type e in the grub menu to edit it.  For the live CD, I believe you push the function key, possibly F1.  Someone else will need to confirm this for me though.

---

### Post by r_duke on 2007-03-01
you can add the command line parameters before booting. when you insert the Live CD press F6 and add the parameters behind the -- . that is [COLOR="RoyalBlue"]-- noacpi[/COLOR] f.e.
hih, r_duke

---

### Post by Russty of Oz on 2007-03-01
> **r_duke said:**
> you can add the command line parameters before booting. when you insert the Live CD press F6 and add the parameters behind the -- . that is [COLOR="RoyalBlue"]-- noacpi[/COLOR] f.e.
hih, r_duke

I have tried that but the screen still turns off!  

I got Freespire to work (sort of) the only thing is I can't get the wireless to work and also the sound doesn't work.  I tried searching the Freespire forum and although there was something that was suppose to fix it "eaisly", I just couldn't understand it, and the Freespire forum doesn't seem to be as well used as Ubuntu, so help is slow coming.  I gathered this from the responses to other's posts on this subject.

So, the outcome of all this is that my friends laptop will have to remain a Windows only machine until I can find a Ubuntu version that works with this screen.

Thanks to everyone who has so kindly tried to help here.  At least I still have Ubuntu working perfectly on MY PC's. :) 

Russty.

---

### Post by foznot on 2007-03-01
Just a thought, but try passing acpi=off and see if that won't let you boot. I have had a couple problems with the install cd and that seems to clean things up for me. When the gui boot options load, hitn [esc] and that will take you to the command prompt. Then you can use the [f keys] better and they will give you some examples.

---

### Post by dolphin_oracle on 2007-03-02
I had this same problem on a Sony PCG-FXA32.  The installation would hang while selecting packages I think, with the CD drive spinning up and down over and over.   I was using the Xubuntu 6.10 alt cd.  At first I though it was related to ACPI, but that turned out to be false.  I then gave the entire hardrive to the the installer to partition as it saw fit, and still it hung up.  Same place. What I had done was start setting up a network connection, but it couldn't be configured since the wireless card (Rt61 based) has a broken module in edgy.  I didn't know that at the time, but I restarted a 4th time on installation and skipped network setup.  I thought it was going to hang in the same place, but after a minute, it continued on. 

Hope this helps.

---

