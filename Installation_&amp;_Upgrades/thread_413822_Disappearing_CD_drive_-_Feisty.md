---
title: "Disappearing CD drive - Feisty"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by tony72 on 2007-04-19
I can see that this is going to be a pretty busy forum over the next few days :), but hopefully someone can spare a minute or two to point me in the right direction. I haven't been able to find an existing post on this issue.

My LG CD drive, which works absolutely fine under Ubuntu 6.10, seems to have a strange problem under 7.04. While the installer can read the disc fine (BTW I did verify the disc after burning) and I can boot from the CD fine, once booted into Ubuntu I can't access the drive. When I boot from the CD, then try to browse the CD (the very CD I just booted from) by double-clicking the CD-RW icon in the file manager, I get an "Unable to mount media/There is probably no media in the drive" error! When I boot from the harddrive, then insert a data CD, Ubuntu seems to be convinced it's an audio CD (displays "CD-RW Drive: Audio Disc" in the file manager). It also displays "Audio Disc" when the drive is empty. If I insert an actual audio CD, it can't play it, if that tells us anything.

Can anyone give me a clue how to fix this, or start diagnosing the problem? Preferably spelt out, 'cos I'm pretty much a newbie (just started using Ubuntu a few weeks ago).

---

### Post by ajgreeny on 2007-04-19
Could be something to do with feisty seeing all hard disks as sata even if they are really IDE and then not updating the fstab file to make your cdrom recognisable in the system.  Have a look for **hda becomes sda** in these forums and also **disappearing cdrom**.  This may give you some help.

Also when your cdrom has automounted after booting and inserting a CD try "mount" in the terminal which will tell you what is mounted and how your system sees it.  You could then edit your fstab file to take account of this apparent change.  Make sure you do a backup first, however, just in case it all goes wrong.

---

### Post by tony72 on 2007-04-19
Ok, thanks for the suggestion, you pointed me roughly in the right direction. All it was is for some reason, the cdrom line in fstab was set to "noauto", I changed that to auto and it's fine. I feel ignorant, but this kind of thing is not obvious to a windows user like me :(. I'm trying.

---

### Post by tony72 on 2007-04-19
Ok, this issue is not quite resolved after all. Was changing the fstab line to auto the right thing to do :confused:? With that change, it still doesn't mount a disc on insertion as it used to, but if I then double-click the CDROM1 icon in the file manager, the disc is mounted, the icon suddenly appears on the desktop etc. I can't just eject the disc with the eject button on the drive as I used to, I have to right-click on the icon in the file manager, and click "Eject". And if I boot up with a disc in the drive, it does get mounted automatically, but when I try and eject it by any method, I get a "You are not privileged to eject the volume" or something like that, I have to do a "sudo umount /dev/hdb" before I can eject it! 

Any ideas? At least I can now get information off my CDs, but something is obviously not configured right. Help!

---

### Post by tony72 on 2007-04-20
Nobody? It can't be a big thing, but I haven't managed to find anything relevant in the forum.

---

### Post by ajgreeny on 2007-04-20
Well, here is my cdrom entry in the fstab file for my dapper machine:-
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Ok I know this is dapper but at least it shows that it is normally set to noauto as yours was.  Sorry, but I don't know what else to suggest to help you, other than to say that I don't think I have ever been able to eject a mounted CD in the drive by just pushing the button on the drive, it must be unmounted first.

I have just checked that point to be sure I was correct, and I was!  I have to right click the icon and use eject, or unmount the drive first.

---

### Post by ajgreeny on 2007-04-22
Just in case it may help you in your further searches, here is a site which explains all about the fstab file in your system, and why the floppy and cdrom are noauto by default;  there is no point trying to mount them when there may normally be no disk in the drive.  Makes sense.

In any case this site/article has explained a lot to me about fstab setup in the past, and I thought it could perhaps be of help to you in future, if not right now.

---

### Post by jasorn on 2007-05-13
[FONT="Courier New"]Hello,

I don't know if this will help anyone but I thought I'd post the fix I used when I was getting the 'not privileged to unmount' message for my usb drive.

I searched a bit and saw some answers talking about modifying fstab.  The thing that bothers me about that is I'm not supposed to have to do that.  When things are working right mounting and unmounting should just work.

Well, it was an fstab thing! Automatix put the following two lines in my fstab.  But rather than 'fixing' the line, I simply removed it and let the system handle my thumb drive automagically.  All is well now.

# Generated by Automatix
/dev/sdb1   /media/sdb1   vfat    iocharset=utf8,umask=000  0    0[/FONT]

---

### Post by aliennet on 2007-06-21
Same problem unitl today.
It was solved (or rather I think it depends on the kernel upgrading) from 2.6.20-16-386 kernel. Try it.

---

### Post by alyssa on 2007-10-20
I need serious help.  I recently converted to Ubuntu and I lack any knowledge of how to follow the directions that have been posted about disappearing cdrom drives, dvd drives, etc.  I have updated **every** video/audio codec to watch dvds then found out that Fiesty has issues mounting and unmounting cdrom/dvd-rw drives.  I then used synaptic package manager to install the kernel 2.6.20-16-386 and still I cannot mount media.  My knowlege of the use of the terminal extends as far as knowing that when I type in sudo I am giving a command.  I have no idea how to edit the fstab and I have spent days trying to get a dvd out of my dvd-rw drive and haven't dared to mount another cd in the other cdrom drive or a usb stick.

These are the error messages I get.
Attempting to play the dvd through Totem or opening the dvd in the Computer File Browser
ERROR: Unable to Mount Media, There is probably no media in the drive.

Attempting to eject disc
ERROR: Cannot Eject Volume: You are not privileged to eject this volume.

Please in the clearest and simplest directions tell me exactly what to type into the terminal to fix this problem.  And please don't feel condescending if you write out every action.  I would greatly appreciate any help anyone has to offer for an utter novice.

Thank you.

---

### Post by thinktyler on 2007-10-25
To fix the priv's issue you have to change your fstab.

Press Alt+f2 or open up terminal and type
"gksudo gedit "/etc/fstab"
Replace auto with noauto. Do this on all of your CD-ROM.
Save the file.
Reboot.

I"m not a linux guru or do I have any code knowledge... 

This fixed my issue.

---

