---
title: "Home made system recovery CD/DVD?"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by digitalTOMO on 2006-09-18
I have installed Ubuntu Dapper Drake for the 100th time this week.  Ive finally got all of my settings, programs, plugins and little tweaks the way that i want them.

I am quite new to Ubuntu so i keep messing things up and end up doing a reinstall because its quicker and easier but then i have to go through installing all the additional software and everything else all over again.

Is there any way that i can make a bootable recovery DVD or CD that i can switch off the computer and put in and it will restore Ubuntu to the exact setup i have now, including all of the additional tweaks and software i have added?

I have spent hours reading other threads and outside message boards about this but they seem a little vague.  If anyone has any ideas can they let me know before i bust Ubuntu again and have to spend ages tweaking everything the way i like it.

Cheers,  Chris x

---

### Post by bswilson on 2006-09-18
> **digitalTOMO said:**
> I am quite new to Ubuntu so i keep messing things up and end up doing a reinstall because its quicker and easier but then i have to go through installing all the additional software and everything else all over again.

You really should not have to do that.  What about the installation are you "messing up"?  I can't really help with the backup, because I've never needed one for anything other than my data [since Ubuntu is so easy to install and configure]...

---

### Post by jamesjtucker on 2006-09-18
What i have done in the past is to create a ghost image from a bootable ghost floppy, and save that image to a usb drive (for laptops) or a second IDE harddrive (desktops), if my system were to crash, i would be able to restore it from that ghost image. The problem: ghost isnt free (but i bet you could find it ;) ). Since i own ghost, i havent tried to search around for a free imaging tool, but a quick google search turns up:
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

I usually refresh my image about once every 6 months, keeping the most current and one prior (just in case). 

Hope this helps!

---

### Post by digitalTOMO on 2006-09-18
messin up all kinds... trying to get things to work, trying new things out...
everything ive messed up ive found the answer to, but i just find it easier to wipe it all and start again and not make the same mistake.  just rather be able to make a bootable backup that i can whack in the dvd drive so i dont have to reinstall loads of stuff.

theres loads of posts on forums and stuff about it but i cant tell whether they do waht i want  to do specifically.

i found one that sounded like what i want to do but it was a walkthrough for Fedora and i dont know if itd work the same with Ubuntu or not.

Cheers anyways, chris x

---

### Post by digitalTOMO on 2006-09-18
cheers jamesjtucker!

that Part Image seems to be like the kind of thing i want but i dont understand how it works if its not bootable.

is ghost that you refer to Norton Ghost?

i dont have a floppy drive either, but dont know if thats necessary.

say if my system failed completely and i had an DVD image of my hard disk, how would i go about getting it back on to my hard disk? just boot up with the DVD in, or would i have to enter a load of commands and things like that?

chris x

---

### Post by digitalTOMO on 2006-09-18
one more thing i dont understand.... if it is Norton Ghost theres also summit similar called Norton Backup and Save or summit like that i they sound like exactly what i need.

they dont appear to have a linux version tho so how do i use it if i get hold of it????

answer that and ill be on my way to safe computing!

chris x

---

### Post by brianbarry on 2006-09-19
Use the custom install image, using the "OEM" installation.  The setup allows OEMs to install the same setup to numberous systems.

Brian

---

### Post by blkish on 2006-09-19
hi

backing up the contents of your home directory (specifically all the hidden files and folders - the ones beginning with a dot) is a good way to preserve most of the settings/preferences for the software you have installed.

most packages keep setting/preference information in these 'dot files'.

to retain a record of the various extra packages you have installed, you could look into also backing up the log from apt (the ubuntu package manager) on your system - you may need to explicitly enable such logging - see [http://www.debian.org/doc/FAQ/ch-uptodate.en.html](http://www.debian.org/doc/FAQ/ch-uptodate.en.html) section 8.5

i would also recommend installing your system with a seperate root (/) and home (/home) partition, and keeping a ghost-type backup of the root (/)

Ghost for Unix (g4u) is a good open-source package for this.

the guys in the server/networking forums may also have other ideas about this, as it's a disaster-recovery/backup type issue.

good luck :)

blkish

---

### Post by keithweddell on 2006-09-19
If you really want to do this you probably need to look at [this Howto]("https://help.ubuntu.com/community/InstallCDCustomization?action=show&redirect=InstallCDCustomizationHowTo").

But it would be much easier to use something like partimage.


Keith

---

