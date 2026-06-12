---
title: "Iomega"
date: 2004-10-23
forum: Installation &amp; Upgrades
---

### Post by jcscar on 2004-10-23
I have an internal Iomega Zip250.   I can't find this drive even when there is a disk inserted.

A lesser important matter to me, I also have a 5 in 1 usb drive that doesn't show up. However I can work around not using this if I need to.

---

### Post by jcscar on 2004-10-24
The five in one is working now, just need to know about the zip

---

### Post by tmh on 2004-11-11
Just figured this one out myself with some help from the #debian irc channel. The short-term solution is

sudo modprobe ide-floppy

The longterm solution is to add ide-floppy to /etc/modules (which will make it work on startup)

---

### Post by randy on 2004-11-11
After you install the ide-floppy device your zip drive will probably be listed as a SCSI device.  (At least it as on my system).  It will more than likely be /dev/sda.

---

### Post by jcscar on 2004-11-12
I typed your command but nothing...

I looked for sde but found nothing..
sda-sdd are used already

---

### Post by randy on 2004-11-13
Is your zip drive listed anywhere in your dmesg output?

---

### Post by RevJack on 2004-11-13
I have a USB Iomega Zip 100 zip drive. How do I get Ubuntu to see and mount it?

---

### Post by randy on 2004-11-14
My 100 meg usb zip is picked up as /dev/sda.  My disks are mounted automatically by gnome-volume-manager.

---

### Post by RevJack on 2004-11-14
I should've clarified. My USB Iomega Zip 100 zip drive IS picked up and recognized and mounted in Gnome. I need to know how to get it recognized and mounted in KDE 3.3 using Ubuntu's Hoary edition.

---

### Post by randy on 2004-11-14
You might be able to have gnome-volume-manager startup when your kde session starts up.  Otherwise you'll have to use the mount command.  man mount for more information.

---

### Post by RevJack on 2004-11-15
Ok, thanks!

---

### Post by wayover13 on 2004-11-15
This is a bug in my view.  Internal ATAPI IDE zip devices are not as common as they used to be, but they're still out there.  I see no good reason why they should be excluded from auto detection/auto mounting that the Gnome desktop environment is supposed to provide.  I can modprobe and edit /etc/modules and manually mount with the best of newbies, but that's a hack for what the desktop environment is supposed to be doing.  What's needed, at the least, is a clear set of instructuions for users with internal ATAPI zip drives to get them integrated into the desktop and working like they're supposed to.  So that the drive is detected and placed in /etc/fstab and desktop icons appear for them when a disk is inserted--just like with CD's and USB drives.  Anything short of that is a kludge to the desktop enivronment crying out for a fix.  So, how about instructions for a REAL fix?

James

---

### Post by TravisNewman on 2004-11-15
[QUOTE=wayover13]This is a bug in my view.  Internal ATAPI IDE zip devices are not as common as they used to be, but they're still out there.  I see no good reason why they should be excluded from auto detection/auto mounting that the Gnome desktop environment is supposed to provide.  I can modprobe and edit /etc/modules and manually mount with the best of newbies, but that's a hack for what the desktop environment is supposed to be doing.  What's needed, at the least, is a clear set of instructuions for users with internal ATAPI zip drives to get them integrated into the desktop and working like they're supposed to.  So that the drive is detected and placed in /etc/fstab and desktop icons appear for them when a disk is inserted--just like with CD's and USB drives.  Anything short of that is a kludge to the desktop enivronment crying out for a fix.  So, how about instructions for a REAL fix?

James[/QUOTE]
 The fix is, add ide-floppy to /etc/modules, and then GVM will pick it up. The seems to be what everyone on this thread is saying.

---

### Post by wayover13 on 2004-11-15
[QUOTE=panickedthumb]The fix is, add ide-floppy to /etc/modules, and then GVM will pick it up. The seems to be what everyone on this thread is saying.[/QUOTE]

Really?  So, you don't have to edit /etc/fstab or create a mount point for the device (say, /media/zip0)?  Do you know this from experience, from logical deduction, or are you guessing this is all that's needed?  I'm no Linux expert, but my expereince using it thus far indicates that editing fstab might be necessary as could creating a mount point.  If Ubuntu/Gnome somehow automate that part of things, I'd be interested to know.

James

---

### Post by TravisNewman on 2004-11-15
[QUOTE=wayover13]Really?  So, you don't have to edit /etc/fstab or create a mount point for the device (say, /media/zip0)?  Do you know this from experience, from logical deduction, or are you guessing this is all that's needed?  I'm no Linux expert, but my expereince using it thus far indicates that editing fstab might be necessary as could creating a mount point.  If Ubuntu/Gnome somehow automate that part of things, I'd be interested to know.

James[/QUOTE]
 I don't really know where it mounts it, but I have an lpt port zip 100 drive, and after modprobing the necessary modules, it picked it up and mounted it automatically when I inserted a disk. Whether or not this is typical, I don't know, but I DO know that it seems like that's what people are saying here.

---

### Post by wayover13 on 2004-11-15
[QUOTE=panickedthumb]I don't really know where it mounts it. . . but I DO know that it seems like that's what people are saying here.[/QUOTE]

Oh?  Did you read Randy's remark to the effect that "You might be able to have gnome-volume-manager startup when your kde session starts up. Otherwise you'll have to use the mount command. man mount for more information" (assume he meant to write "gnome" where he wrote "kde").  I'd say your reading (or interpretation) skills are not such that you shouldn't be claiming to have such unique knowledge about what people are saying on this thread.  And your vague grasp of what's happening technically mean that you're guessing.  Maybe someone else will have something more substantial to offer.

James

---

### Post by TravisNewman on 2004-11-15
No, dude, he meant KDE. He was replying to the post right before it that said:
> 
I should've clarified. My USB Iomega Zip 100 zip drive **IS picked up and recognized and mounted in Gnome**. I need to know how to get it recognized and mounted in **KDE 3.3** using Ubuntu's Hoary edition.
Please take the time to read things before you start jumping down my throat for not reading things, or not having good "reading and interpretation skill" when YOU misread it to begin with, and made the assumption that he meant to say Gnome when he said KDE.

And your use of my quote was way out of context. Using the "..." to take out the part of my post that had the most substance. If someone said "I don't support eating babies" you can't quote them as saying "I ... support eating babies." What I'm saying is that I don't know where it mounts it but I do know that it mounts it on my PC, and that people on this thread are saying that it mounts on theirs.

And I don't claim to have a unique grasp of what people are saying on this thread. When someone says "My drive is picked up and mounted in Gnome" I think it's safe to say they mean what they say.

No offense, but you have a funny way of showing appreciation when people try to help you

---

### Post by wayover13 on 2004-11-15
[QUOTE=panickedthumb]No offense, but you have a funny way of showing appreciation when people try to help you[/QUOTE]

It's not help.  Allow me to demonstrate.  I've just now added ide-floppy to /etc/modules and rebooted.  The zip drive does not show up under computer > disks.  Whether there's a disk in the drive or not, there's no icon representing the drive, either under computer > disks or on the desktop.  Now, I'll go and create mount points under media: zip0 and a symlink to it--zip.  Next, I'll edit /etc/fstab and add the block device representing my zip drive (/dev/hdb) pointing it at the mount point.  I save it.  I again look under computer > disks: there sits an icon represnting my zip drive.  Double clicking mounts the disk and allows me to view the contents and puts a zip disk icon on the desktop.

Now, the question about help.  How has your insistence that this whole thread resolves down to the point about adding ide-floppy to /etc/modules helped in all this?  I think my initial post made it clear that I understood what this step was for, and that I could perform it.  That post went on further to talk about the need for setting out some steps for people who want to get their internal ATAPI IDE zip drives working.  Bringing all this focus on the ide-floppy step such as you've done has acted to detract from understanding and implementing the whole process that actually leads to the drive being represented iconically and its files becoming accessible.  It has hindered, rather than helped.  By my own experimentation, and without having to monitor this forum to read what are essentially moot points, I could have accomplished this more quickly.  I don't dispute that you were "trying": what you were trying to do is not clear, but it certainly did not result in help.  If it's offering something else under the guise of help, I feel no obligation to show appreciation.  Instead, I would ask you to more carefully consider your own motivations.

So, here's my attempt at help.  For anyone reading this thread with an internal ATAPI IDE zip drive, my experimentation indicates that simply loading the ide-floppy module is not enough to get it iconified and accessible.  The additional steps of editing /etc/fstab and creating a mount point were required in my case.

But I'm not convinced this is the best or final answer.  Ubuntu seems to be using devfs or udev (have a hard time keeping those straight), so there may be some process monitoring filesystems and dynamically creating mount points and icons that is not picking up the zip drive and/or disks inserted into it.  Why, I don't know.  Maybe that process needs some sort of tweaking?  Perhaps a better fix could be implemented, if that's the case.  I reissue my call for the clearest, simplest workaround possible for this problem.  I also reemphasize my point about this lack of zip support being an Ubuntu bug that needs fixing.

As for me, I'm still waiting for some helpful input.  Anyone have a clearer understanding of this and a more elegant solution to getting internal ATAPI iDE zip drives integrated with the desktop environment than the one I've described?  Please offer it.  modprobe ide-floppy is only part of the solution according to my experimentation.

James

---

### Post by TravisNewman on 2004-11-15
OK I got my ide and usb mixed up when reading the thread. I admit that (I've posted elsewhere in the forum about my ADD ;)) Some of the stuff you were bringing into the discussion involved the previous discussion about usb as well, so I got things mixed up even more, and I apologize for that.

The fact remains, you were being very rude and that's not a way to get help or get things changed. Regardless of whether what I said worked for you, you accused me of not reading a particular post correctly that you didn't read correctly (though I did misread some things), you twisted my words, and you insulted my intelligence on more than one account. Perhaps I gave incorrect information because I got two terms mixed up, I admit that, but that's no excuse to be rude. And questioning my motives? What would my motives be if not to help? Do you think I was trying to steer you in the wrong direction? No, I got two terms mixed up. There, you insulted my character.

On to the substance of your last post, you probably have the simplest workaround for mounting a zip drive. What you're suggesting isn't a bug report, it's a feature request. There are no bugs revealed in this thread about zip mounting, only lack of features. The only way to make it simpler would be to enable the necessary modules for internal zip drives automatically, regardless of whether one is in the PC or not, unless there was a hardware detection system like exists in redhat. Again, it's all feature requests, not bugs. I agree that it needs to be addressed, however, but it's not something that needs to be "fixed" its something that needs to be "implemented."

---

### Post by jcscar on 2004-11-15
>  Allow me to demonstrate. I've just now added ide-floppy to /etc/modules and rebooted. The zip drive does not show up under computer > disks. Whether there's a disk in the drive or not, there's no icon representing the drive, either under computer > disks or on the desktop. 

I've added ide-floppy to /etc/modules and rebotoed
  The zip still isn't working

> Now, I'll go and create mount points under media: zip0 and a symlink to it--zip.  

How do I do this????

> Next, I'll edit /etc/fstab and add the block device representing my zip drive (/dev/hdb) pointing it at the mount point. I save it. I again look under computer > disks: there sits an icon represnting my zip drive. Double clicking mounts the disk and allows me to view the contents and puts a zip disk icon on the desktop. 

What do I need to change? 

Please give more details so that I (a newby) may get this working.  My school uses zip drives, they are easier to use here then flash drives because of access.. I'd rather not climb under the desk to plug in a flash drive and possibly forget it...

Thanks for all the help thus far.

---

### Post by TravisNewman on 2004-11-15
sudo mkdir /media/zip0
sudo ln -s /media/zip0 /media/zip
sudo nano /etc/fstab
inside this file add this line, changing /dev/hdX to the location of your zip drive (/dev/hdb, /dev/hdc, or /dev/hdd, depending on where it is, and the # is the partition number, which for me defaults to 4, that may not be typical:
/dev/hdX# /media/zip0 auto rw,user,noauto 0 0
Hit ctrl+O to save, and ctrl+x to exit.

That should do it.

And a note: can a mod go through and delete anything that isn't useful? Regardless of whose fault it is, there's a lot of stuff that doesn't need to be here.

---

### Post by troutrou on 2004-11-15
[QUOTE=panickedthumb]sudo mkdir /media/zip0
/dev/hdX /media/zip0 auto rw,user,noauto 0 0
[/QUOTE]

Ah great, Gnome indeed did mount it automatically, didn't have to  do a "mount" by hand. Nautilus shows a nice Zip drive icon.

However when I try to read a disk, it said it could not mount the volume because it could not determine the filesystem and that none was specified ! :o(

Any idea ? :o(

---

### Post by TravisNewman on 2004-11-15
[QUOTE=troutrou]Ah great, Gnome indeed did mount it automatically, didn't have to  do a "mount" by hand. Nautilus shows a nice Zip drive icon.

However when I try to read a disk, it said it could not mount the volume because it could not determine the filesystem and that none was specified ! :o(

Any idea ? :o([/QUOTE]
 Oh oh, sorry!
The first part of the fstab line should be /dev/hdX# for partition number. The parallel drive for some reason always uses 4 as the partition number, so I'd try that first, then try 1.

---

### Post by jcscar on 2004-11-15
my zip drive is hdd
I tried using /dev/hdd1 and /dev/hdd4 however I keep getting the "mount: special device /dev/hdd# does not exist."

this is out of my dmesg "hdd: IOMEGA ZIP 250 ATAPI, ATAPI FLOPPY drive"   am I doing something wrong?

this is the line I entered in fstab

"/dev/hdd4	/media/zip0	auto	rw,user,noauto 	0	0"

---

### Post by jcscar on 2004-11-15
I figured it out!! All by myself. I got rid of the number in the fstab line.. if I just left it at 
```
/dev/hdd	/media/zip0	auto	rw,user,noauto 	0	0
``` it worked great

---

### Post by TravisNewman on 2004-11-15
[QUOTE=jcscar]I figured it out!! All by myself. I got rid of the number in the fstab line.. if I just left it at 
```
/dev/hdd	/media/zip0	auto	rw,user,noauto 	0	0
``` it worked great[/QUOTE]
 Huh. I dug out an old internal zip and had to put in a partition number to get it to work. interesting.

---

### Post by troutrou on 2004-11-15
[QUOTE=panickedthumb]Oh oh, sorry!
The first part of the fstab line should be /dev/hdX# for partition number. The parallel drive for some reason always uses 4 as the partition number, so I'd try that first, then try 1.[/QUOTE]

HDB4 worked ! :-) 

I also have another ZIP 100 drive, on the parallel port, tired HDD1 as you suggested, but didn't work. Gnome picket automatically read the etc/fastb file and put a second ZIP drive icon in the "computer" location, but when clicking on it it says that HDB1 does not exist.

Well, we are progressing anyway ! :-)

I also have a similar problem with my SCSI scanner, I have to run modprobe sg everytime, to get Sane to detect it. Is there something I could do (etc/modules ?) so that the /dev/sg0 module (the scanner) is created automatically when Ubuntu starts ?

I really hope all this will be "fixed" for the new realease of Ubuntu. :-(

---

### Post by wayover13 on 2004-11-15
[QUOTE=panickedthumb]OK I got my ide and usb mixed up when reading the thread. . . so I got things mixed up even more, and I apologize for that.[/QUOTE]

I see your bid and match it.  I got mixed up too (about KDE) and I apologize for that.

> The fact remains, you were being very rude and that's not a way to get help or get things changed. Regardless of whether what I said worked for you, you accused me of not reading a particular post correctly that you didn't read correctly (though I did misread some things), you twisted my words, and you insulted my intelligence on more than one account. Perhaps I gave incorrect information because I got two terms mixed up, I admit that, but that's no excuse to be rude. And questioning my motives? What would my motives be if not to help? Do you think I was trying to steer you in the wrong direction? No, I got two terms mixed up. There, you insulted my character.

We were sort of even-steven before (one mistake, one apology).  Not sure where we stand now.  Maybe we should both admit to being rude and offer an additional apology?  I'm game if you are.  I apologize for being rude.  Let's see you match that :)

> On to the substance of your last post, you probably have the simplest workaround for mounting a zip drive.

I was afraid of that . . .

> What you're suggesting isn't a bug report, it's a feature request. There are no bugs revealed in this thread about zip mounting, only lack of features. The only way to make it simpler would be to enable the necessary modules for internal zip drives automatically, regardless of whether one is in the PC or not, unless there was a hardware detection system like exists in redhat. Again, it's all feature requests, not bugs. I agree that it needs to be addressed, however, but it's not something that needs to be "fixed" its something that needs to be "implemented."

Something as simple and common as an internal ATAPI IDE zip drive not getting configured and integrated into the desktop isn't a bug?  Ok, a serious shortcoming, at least?  I think it's a real black mark on this otherwise great distro.  PLEASE fix it, developers who might be reading this!

James

---

### Post by TravisNewman on 2004-11-15
Agreed, I was rude, and I get rude when I'm flustered. I didn't think I was until I re-read. Caught up in the moment I guess. So yeah, sorry bout that. Even stevens? *shake*

Shouldn't be too hard to have some sort of a detection script run to see if there's other optional media such as all the flavors of zip drives, etc, but this isn't really the place to ask for it unless a dev decides to read this thread. I don't know where the right place to ask IS, maybe just find a developer and grab his email and see what he says. But I'd say the most you get is a script to detect it in the "Expert" mode of the install. The default install is pretty much always going to stay as simple as possible, and it would probably result in more questions for the user.

---

### Post by wayover13 on 2004-11-15
[QUOTE=troutrou]However when I try to read a disk, it said it could not mount the volume because it could not determine the filesystem and that none was specified ! :o(

Any idea ? :o([/QUOTE]

I get an error when I try to mount mine as well, but when I click "ok" in the error message pane, it mounts anyway.  Eject from the dropdown menu doesn't work either.  So, it's sort of a kludge.  This method will get the thing working and somewhat integrated into the desktop, but there are issues to be resolved for it to work like it's supposed to.

My fstab line required using the partition number 4 as well (/dev/hdb4).  Not sure of the /media/zip symlink is absolutely needed: I was pretty much cloning the floppy entry.  There some sort of trickery going on behind the scenes with automounting and making icons appear on the desktop that I don't understand real well, and I presume the symlink relates to that.

James

---

### Post by wayover13 on 2004-11-15
Here's what I'm getting about internal ATAPI IDE zip drives from this thread: the 100 MB drives require a partition number.  Seems like 4 is the way to go (I recall having to use sda4 on another distro where I had an external usb zip 100, too).  For the 250 MB ones, it seems specifying the partition number is NOT needed.  So, the /etc/fstab entry for zip 100's will be /dev/hdx# and for zip 250's /dev/hdx (no # for the 250).  Hopefully some folks with these internal zip drives will be able to get them working at least provisionally using this thread.  Anyone with a more elegant/simple solution should please post it here for the benefit of others.

James

---

### Post by TravisNewman on 2004-11-15
I have the question to top them all:

What were the Iomega engineers thinking when they designed these things?!?!

---

### Post by viorel on 2004-11-16
Does anyone have any idea how i have to setup FSTAB in order to mount my USB-stick? I have a Kingtson DataTraveller 256Mb. Thanks!

---

### Post by troutrou on 2004-11-16
So now that my IDE ZIP 100 works with "hdb4", what is the device name for my other ZIP 100 drive, which is external on the parrallel port ?

I looked at the output of the 'dmesg' command and it seems it's called 'lp0' (it even found my printer on it).

So I tried '/dev/lp0' in etc/fstab, but when clicking on the icon, it says it can't mount it because 'lp0 is not a block device' ......

Anyone managed to get a parport ZIP working ?? :-/

---

### Post by TravisNewman on 2004-11-16
parallel port zips ar /dev/sdx4, so if you have no other scsi devices (virtual or otherwise), it's dsa4. Don't ask why it's 4, but every howto I've dug up on the net says 4.

---

### Post by troutrou on 2004-11-16
[QUOTE=panickedthumb]parallel port zips ar /dev/sdx4, so if you have no other scsi devices (virtual or otherwise), it's dsa4. Don't ask why it's 4, but every howto I've dug up on the net says 4.[/QUOTE]

Ah well, I tried sda4 but it says it doesn't exist :-(

I DO have a SCSI device (an AGFA Snapscan 1236s scanner), but it uses device sg0 not sdX.

It's already bad enough that Ubuntu doesn't create all the required devices automatically, but it's really not cool that they don't at least provide a full list devices, what peripheral they represent, and how to set them up by hand.
Really make mes angry, spoils an otherwise lovely distro...

I guess I will have to search the net outside Ubuntu then, like you did :-(
Maybe start with debian sites, as I guess that's what it likely to be the mlost relevant to us.

---

### Post by troutrou on 2004-11-16
I made some progress !

Did a quick search on Yahoo for 'zip parallel howto', came up with this link: 
[http://en.tldp.org/HOWTO/ZIP-Drive-2.html](http://en.tldp.org/HOWTO/ZIP-Drive-2.html)

Basically just did a 'modprobe ppa', then just did a 'mount' and Gnome instantly put a loooovely additional ZIP icon next to my IDE ZIP icon ! :o)
And I could even print to my laser pritner "through" the ZIP drive without problems, worked perfectly :-)
Then did a 'eject sd4' and my lovely external drive handed the disk to me, and Gnome automatically removed the icon from the desktop !

Very sweet ! :o)

However I also had to do that 'modprobe' command to get my SCSI scanner to work, and every time I restart the machine, I have to do 'modprobe sg' again to make my scanner work. So I guess I will have to do the same for my external ZIP drive then :o(
However the IDE ZIP drive seems to stay in place, probably due to the 'ide-floppy' line we added in the /etc/modules file ? So maybe there is a line we could ad to that file that would make Ubuntu mount SG and SD devices at startup ?

If only Ubuntu supplied documentation on the /etc/modules file.... :o(

Vince, slowly getting there...

---

### Post by TravisNewman on 2004-11-16
for anything you have to modprobe, for example, sg and ppa, you can put them in the /etc/modules

---

### Post by troutrou on 2004-11-16
Did it, it worked :o)

So in the end, all the problems I was having with Ubuntu:

1) mounting my other IDE hard drives and partitions
2) SCSI Scanner
3) IDE ZIP100 Drive
4) Par port ZIP100

were easily solved by just adding a few modules to etc/modules then tweaking fstab and creating mount points.

So, given this is all so simple (now that I know how to do it ie ! ;o), I can only hope that the next release of Ubuntu will take care of that !
It's supposed to be user friendly no ?....

There is one last thing I don't understand clearly, and would like a howto written about, is the way Ubuntu uses this "/media" folder. I understand this is were you must put your mount points, if you want Gnome to automatically mount removeable media and put an icon in the /computer location and desktop ? Is that it ?
Then, how does it work ? I mean why do you have for example a "floppy0" folder with a 'floppy' link to it ? What's the mechanism behind that ? Why can't we just put a folder with the name we want, so that the icon on the desktop has a nice name, not "Zip0" or "Zip1" ! I would like a clear howto guide on this, will try and post the mailing list about this, as I do'nt think I am gonna be heard by the Ubuntu guys if I ask on this forum :o(

Anyway, things are improving fast, my Ubuntu is really very sweet, perfect looking Gnome, all my peripherals working perfectly now, I love it ! :o)

---

