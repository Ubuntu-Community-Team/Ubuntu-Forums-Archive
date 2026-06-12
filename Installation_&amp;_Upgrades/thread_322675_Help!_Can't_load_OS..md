---
title: "Help! Can't load OS."
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by holdinout on 2006-12-20
I needed to keep Windows as a dual boot, for my girlfriend and my games. So, using the secondary drive I have I installed Xubuntu, leaving XP on my local drive. Now given the way Windows was acting, I wanted to format and reinstall it on my local drive. Heres the fun part (Convinced me I need to be a Linux user):

During Windows install, everything was going fine for the format of C: (Linux on G up until there was about 30 minutes left. The screen flashed black once, then went back to the install. Two seconds later, I'm at a black screen with a blinking cursor, like DOS. I know NT versions of Windows don't have DOS, so this is puzzling. Especially since you can't type or do anything more than turn the PC off and repeat. If anyone can help me either completely format both drives, or get one OS working, or something, PLEASE! I can't use my computer at all!

Tried booting with Xubuntu disc and Windows disk, didn't work.
I don't have a floppy drive or a start-up disk, so would that mean I don't have a computer?

Help would be greatly appreciated.

---

### Post by Mimsy on 2006-12-20
I'm guessing there was a very, very short power outage in the middle of the install. Computers are disgustingly sensitive to such things.

I'm not one of the experts you're looking for, so I can't be of much help to you, but I have two questions for you anyway:

1. Do you have a current back-up of your important data? If you do, that makes things way easier.

2. Can you get into your BIOS and change boot settings to boot from a live CD? If you can, you could mount your hard drives from the CD and back up your data that way.

I'm sorry I can't be of enough help. Good luck! My fingers are crossed for you, or your computer, whichever you prefer.

/Mimsy

---

### Post by holdinout on 2006-12-20
It's not even the data I'm worried about... Just getting into an OS. I can get into my CMOS but there isn't a boot from live CD option. I've tried changing the boot sequence around a few times, but no matter what order, window wants to continue setup for 5 minutes so it can crash again... happens at the SAME point every time too.

---

### Post by Wall86 on 2006-12-20
have you tried booting to the recovery console on the windows cd? and running like "chkdisk c:/" ? or even run fdisk c:/ to format the drive, then try again?

---

### Post by Mimsy on 2006-12-20
Yes, the iso, burned as an image to a CD, is the live CD. Absolutely right.

Can you boot from a floppy? If you can, you might be able to put a tiny Linux distribution on there, and boot into it. That would at least give you a functioning system if you boot from the floppy, which in turn would give you a lot more options. Damn Small Linux comes to mind. 

I have reached the limits of my ability to help out. Sorry. Hopefully I managed to bump the thread high enough to be noticed by someone capable of helping you. Again, good luck.

/Mimsy

---

### Post by holdinout on 2006-12-20
How do I boot to the recovery console? When I startup, I get the system check screen w/CMOS option. After that, the install just picks up right away, about 35 minutes from finish. It crashes to that blank DOS-like screen. If you can get me in the console for those commands, that'd be great. BTW, no floppy drive in my PC.

---

### Post by Wall86 on 2006-12-20
ok, during your cmos splash screen, does it ask you something like "press esc for boot devices" or something roudn those lines? 

another option, in your cmos, completely disable "boot to hard disk" and just have a "boot to cd-drive"

tell me if that helped at all?

---

### Post by Wall86 on 2006-12-20
oh ya, if you do get to boot to cd, be sure to boot from your windows cd, then, when it asks you like "press enter to install" or like "press R to enter recovery mode" press the button to go into recovery console

---

### Post by Mimsy on 2006-12-20
I have "rented" PCs for a home-made-from-scratch chicken casserole and fudge brownies in the pst. If that is an option for you, great. If not, I personally would try to install a floppy drive to the system and then boot from it. I know, they're obsolete, but for some reason I have at least three of them laying around the house somewhere... (If you live in or near Meridian, ID, I'll lend you one.)

Once more, good luck to you! I'll follow his thread, mainly because I want to know how to solve this if I ever find myself in this situation.

/Mimsy

---

### Post by kolinab on 2006-12-20
This thread is a little old so maybe you've done this already - but why don't you pull out your HDDs and format them on a friends computer or at work or something? Kind of a brute force approach.

K

---

### Post by holdinout on 2006-12-20
I had a dual boot setup for XP and Xubuntu, and it was working fine. I wanted to reinstall windows after my Xubuntu setup, because my current version was acting sluggish. I had XP on the master drive, and Xubuntu on my slave. Now during windows installation, the screen "flashed" black, then restarted. The restart would bring me throught the typical BIOS boot screen, followed by a blank DOS-like screen with a blinking cursor.
From here, you can't do anything. So, I've tried EVERYTHING to get on to any OS. If anyone can help me, that would be great. Loss of data isn't a problem, so I put the master drive in my other PC to format it. When I opened My Computer, the drive I wanted to format was partitioned into a 5gig and a 50 gig. The 5gig was the PC was HP's Windows backup files, and the other partiton was for Windows itself. Now, the larger partiton cant be formatted! See, XP couldn't tell me anything about the large partiton(free space, Used space).
My secondary drive for Xubuntu wasnt formatted, and has 2 partitions: Linux and Linux swap. But I still can't boot even from that drive. I can't even load the live CD! I think the larger partiton of my master drive (for Windows) is messed up, and I don't know what to do about it. I even tried to fix it with Acronis Disk Director (partitioner), but that didn't seem to work. ANY ideas would help!

---

### Post by holdinout on 2006-12-20
BTW, tried Windows install CD, Recovery CD, Xubuntu live disk, and even bashing the computer a few times with a rubber mallet... The recovery CD prolly didn't work, cause its for a different PC, but the Windows or Xubuntu CD should work, right? I've re-arranged my boot sequence to every possibility.

---

### Post by holdinout on 2006-12-20
I had a dual boot setup for XP and Xubuntu, and it was working fine. I wanted to reinstall windows after my Xubuntu setup, because my current version was acting sluggish. I had XP on the master drive, and Xubuntu on my slave. Now during windows installation, the screen "flashed" black, then restarted. The restart would bring me throught the typical BIOS boot screen, followed by a blank DOS-like screen with a blinking cursor.
From here, you can't do anything. So, I've tried EVERYTHING to get on to any OS. If anyone can help me, that would be great. Loss of data isn't a problem, so I put the master drive in my other PC to format it. When I opened My Computer, the drive I wanted to format was partitioned into a 5gig and a 50 gig. The 5gig was the PC was HP's Windows backup files, and the other partiton was for Windows itself. Now, the larger partiton cant be formatted! See, XP couldn't tell me anything about the large partiton(free space, Used space).
My secondary drive for Xubuntu wasnt formatted, and has 2 partitions: Linux and Linux swap. But I still can't boot even from that drive. I can't even load the live CD! I think the larger partiton of my master drive (for Windows) is messed up, and I don't know what to do about it. I even tried to fix it with Acronis Disk Director (partitioner), but that didn't seem to work. ANY ideas would help!

Error messages include:

Can't find OS
and
Invalid boot disc, insert system disc and press enter (or whatever it is)

---

### Post by holdinout on 2006-12-20
Heres where im at :
I had a dual boot setup for XP and Xubuntu, and it was working fine. I wanted to reinstall windows after my Xubuntu setup, because my current version was acting sluggish. I had XP on the master drive, and Xubuntu on my slave. Now during windows installation, the screen "flashed" black, then restarted. The restart would bring me throught the typical BIOS boot screen, followed by a blank DOS-like screen with a blinking cursor.
From here, you can't do anything. So, I've tried EVERYTHING to get on to any OS. If anyone can help me, that would be great. Loss of data isn't a problem, so I put the master drive in my other PC to format it. When I opened My Computer, the drive I wanted to format was partitioned into a 5gig and a 50 gig. The 5gig was the PC was HP's Windows backup files, and the other partiton was for Windows itself. Now, the larger partiton cant be formatted! See, XP couldn't tell me anything about the large partiton(free space, Used space).
My secondary drive for Xubuntu wasnt formatted, and has 2 partitions: Linux and Linux swap. But I still can't boot even from that drive. I can't even load the live CD! I think the larger partiton of my master drive (for Windows) is messed up, and I don't know what to do about it. I even tried to fix it with Acronis Disk Director (partitioner), but that didn't seem to work. ANY ideas would help!

I do have a few Floppy Drives around, guess I'll get back to the stone age for a bit... 

Thanks Mimsy, when I get it, if I get it, Ill post or PM you.

---

### Post by holdinout on 2006-12-20
Anybody!?!?!

---

### Post by budgie9 on 2006-12-20
> **holdinout said:**
> Heres where im at :
I had a dual boot setup for XP and Xubuntu, and it was working fine. I wanted to reinstall windows after my Xubuntu setup, because my current version was acting sluggish. I had XP on the master drive, and Xubuntu on my slave. Now during windows installation, the screen "flashed" black, then restarted. The restart would bring me throught the typical BIOS boot screen, followed by a blank DOS-like screen with a blinking cursor.
From here, you can't do anything. So, I've tried EVERYTHING to get on to any OS. If anyone can help me, that would be great. Loss of data isn't a problem, so I put the master drive in my other PC to format it. When I opened My Computer, the drive I wanted to format was partitioned into a 5gig and a 50 gig. The 5gig was the PC was HP's Windows backup files, and the other partiton was for Windows itself. Now, the larger partiton cant be formatted! See, XP couldn't tell me anything about the large partiton(free space, Used space).
My secondary drive for Xubuntu wasnt formatted, and has 2 partitions: Linux and Linux swap. But I still can't boot even from that drive. I can't even load the live CD! I think the larger partiton of my master drive (for Windows) is messed up, and I don't know what to do about it. I even tried to fix it with Acronis Disk Director (partitioner), but that didn't seem to work. ANY ideas would help!

I do have a few Floppy Drives around, guess I'll get back to the stone age for a bit... 

Thanks Mimsy, when I get it, if I get it, Ill post or PM you.

Seems we are all shooting in the dark here, so I may as well add my few cents worth.
I think what may have happened, is your partition table is screwed up. You are going to I think, need a FDISK or like program and destroy all the partitions on that disk and start again. You will then have to recreate the partitions you want and then set the first, the C: drive ACTIVE (Sorry for the shout but it is to point out the stage you will need to do.) XP and Windows will only install to an 'active' drive
You can then set the rest of the drive as Extended then partition that part up accordingly.
I hope the drive is not damaged, but it would seem unlikely.
I have had this sort of thing happen in the past. I just hope you can access the drive and recover it as I have managed to do
Are you sure you can't boot from a CD, most machines can if they have no floopy, just asking again to try and help.

---

### Post by holdinout on 2006-12-20
OK, cross fingers, j/k... FDISK, is it in my Windows directory? If not search google? I need all the info I can get before I get back to business on the broken PC, So detail on how to use FDISK would be appreciated... Would it be easier for me to just have one drive, partitioned out for windows and linux, or have a seperate drive for each? I was using seperate drives before, as I'd prefer. My guess is, it doesn't matter...

---

### Post by holdinout on 2006-12-20
Wait, so I use FDISK through dos right? So I would only need a DOS boot disc?

---

### Post by budgie9 on 2006-12-20
> **holdinout said:**
> OK, cross fingers, j/k... FDISK, is it in my Windows directory? If not search google? I need all the info I can get before I get back to business on the broken PC, So detail on how to use FDISK would be appreciated... Would it be easier for me to just have one drive, partitioned out for windows and linux, or have a seperate drive for each? I was using seperate drives before, as I'd prefer. My guess is, it doesn't matter...

Sent you a private message.

---

### Post by K.Mandla on 2006-12-20
That error message suggests the Windows portion has a hosed master boot record. I suppose you could rebuild it from the Windows XP disc with the fixmbr program, but if data loss is not an issue, just wipe it and start clean. Leftover installations have given me errors in the past. 

I don't know if this will solve the problem for you or not, but if it were me I would. ...

[LIST=1]
[*]Download a copy of [Killdisk]("http://www.killdisk.com")
[*]Yank the Xubuntu drive and leave only the XP drive 
[*]Wipe the drive with Killdisk
[*]Rebuild your Windows installation
[*]Plug your Xubuntu drive back in
[*]Rebuild Grub so they're both available at boot: [uwiki]GrubHowto[/uwiki] (or [this howto]("http://www.ubuntuforums.org/showthread.php?t=224351"), which might be better)
[/LIST]
There's also a page in the wiki on [uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki], which might be useful to you.

---

### Post by Wall86 on 2006-12-20
wonderful world of windows, if ya want to fdisk, plop that hdd into another computer, go start>run>command then, make sure that you know what the drives letter is on that computer then just type: fdisk x: where x is the drive letter, if that does not work, you disk might be pooched,

but your BIOS does finish right? does your BIOS recognise all of your partitions?

---

### Post by Iokua on 2006-12-20
Maybe I'm having trouble understanding the problem, but if you can't even run the LiveCD then you might want to check your BIOS boot sequence. Make sure CD-ROM is listed ABOVE both hard drives, so it checks for CD-ROM before going to the boot sector on either drive. It sounds to me like it's trying to boot to a corrupt MBR. Even if the large partition on your XP drive is messed up, you should still be able to boot to CD-ROM or to your other drive (as determined by your BIOS settings).

---

### Post by r4ik on 2006-12-20
Not sure but this might help,

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_restore_GRUB_menu_after_Windows_installation)

Good luck !

---

### Post by hal10000 on 2006-12-20
If you install windows to a computer which has a previous linux installation, then your mbr (master boot record) is overwritten by the windows installation without a backup or even inform you about.
Don't hesitate, nothing is lost (except your partition table), it's just invisible.

But to help you, I must know something more about your system:
Are your harddrives/CD/DVD sata or ide (or maybe SCSI) ?
Where are your drives (CD and disks) connected to? (I suggest you have two IDE controllers with each (max.) two disks/CD/DVD connected) Tell me exactly where they are connected to.

Take care for the correct jumper settings on all of your disks / CD's.

---

### Post by aysiu on 2006-12-20
Posting the same thread three times is frowned upon and counterproductive. I've merged all your threads so people who want to help you can see easily what's already been suggested.

---

### Post by holdinout on 2006-12-21
> **Wall86 said:**
> wonderful world of windows, if ya want to fdisk, plop that hdd into another computer, go start>run>command then, make sure that you know what the drives letter is on that computer then just type: fdisk x: where x is the drive letter, if that does not work, you disk might be pooched,

but your BIOS does finish right? does your BIOS recognise all of your partitions?
aysiu, sorry guys, wasn't getting anywhere and my girl was close to castrating me.

Hal10000, that explains what happened then. It's got a DVD rom, IDE I'm pretty sure, plugged into the motherboard as well as my hd(s). Im always careful about jumper settings, thanks though.

Iokua, been through BIOS many times, and it's safe to say I've tried all the possibilities.

K.Mandla, basically did that. Once Windows is up I'll be installing linux again, since I only had it for a few days before this mess.

Got my neighbors PC, installed the problem hd (windows, always the problem :)), deleted all the partitions, created one volume, formatted. Next I will put the hd back in the problem PC and install windows onto it. After that, I'll re-install Linux on my second drive.

Thanks for all the help guys! I'll let you know soon...

---

### Post by holdinout on 2006-12-21
OK, Tried restarting with XP install disc, and the Live CD in and got this one:
NTLDR is missing
Press Ctrl+Alt+Del to restart

Tried restarting with XP install disc in

I'm gonna try double checking everthing in bios and double checking jumpers (:D hal10000).

---

### Post by Russty of Oz on 2006-12-21
Did you try booting windows using the Super Grub disc?

---

### Post by hal10000 on 2006-12-21
> OK, Tried restarting with XP install disc, and the Live CD in and got this one:
NTLDR is missing

You can fix this by booting your windows installation-CD an using the "Repair installation" mode (I guess It's done by choosing the "repair a previous inst. of windows" point or by preeing the "R"  key).
And maybe you can also fix it by using the Super grub disk, as Russty of Oz said.

If you get a write permission to your windows installation, then you can also simply copy the ntldr.exe from your windows-CD (I guess it' in the \i386 folder) to your C:\partition.

---

