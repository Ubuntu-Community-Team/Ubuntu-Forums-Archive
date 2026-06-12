---
title: "Unable to resize Windows partition - access denied"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by SPARTAN-118 on 2009-12-02
Hi all.

I'm trying to resize my Windows Vista partition (shrink it) in order to have some unallocated space for me to install Kubuntu.

I think it'd be best if I just went and got an External Hard Drive Disk, backed up all my data, and just re-formatted the whole drive and installed Kubuntu instead. However, I don't have enough money to go out and do that. :frown:

So, I'm trying to shrink Windows. Only one problem. Well, two, if you think about it.

In Windows, when I right-click Computer and click Manage, Storage->Disk Management, and select my "C" drive and try to shrink it to the maximum amount it'll allow me (which is only around 5000 or 6000 Mb - not nearly enough space to install Kubuntu, I think), it pauses for a moment, then tells me "Access Denied". (Longest run-on sentence, I know.)
I think to myself, "What the hell? I'm the freakin' *Administrator!*"

So, actually *before* I tried this, I tried resizing the partition in Kubuntu. However, the process was aborted because the installer was "unable to access partiion".

Damn.

So, what'm I supposed to do? I have a dreadful feeling I'll have to end up installing Kubuntu in a WUBI install just like I did Ubuntu... and the reason I uninstalled Ubuntu WUBI in the first place was to ***fully*** install it on a seperate partition!! 

I mean, WUBI ain't so bad. But I had just uninstalled my 'primary' OS so that it wasn't dependent on Windows ***AT ALL***.

What confuses me less than the fact that I'm Administrator but can't perform Administrative tasks is the fact that Windows only says I can shrink it down by about 6GB... and yet, there are over 20GB of available space on the "C" drive... hmm...

---

### Post by gabo.cr on 2009-12-02
I had a similar problem once.
I finally resize the HD using a Ubuntu LifeCD.
The problem was that I "moved" the windows partition so I couldn't boot it again.
So yes, I hate resizing.

---

### Post by SPARTAN-118 on 2009-12-02
Question: How do you move a partition? All I did was select it in the Kubuntu LiveCD and tell it to shrink. Did I end up moving it somehow? If so, how did you get it back to working again with the LiveCD? Like I said, I used the Kubuntu LiveCD originally before trying Windows' built-in DiskPart.exe. Both said the location was either unaccessible or I was denied permission. Either way, if you know of a way to shrink Windows down to a size capable of installing Kubuntu, do tell. Because even if it did work, 5GB does not seem enough...

---

### Post by gabo.cr on 2009-12-02
When resizing a partition you may end up moving it.
You can see that when the list of operations to accomplish is about to resize and move a partition.
After a change is made you cannot go back to the previous partition edition.
Sometimes you may get a "denied permission" trying to make changes in a Windows partition when Windows needs to make a HD check (like when Windows did not close correctly after shutting off the OS)
Check this link also:
[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

---

### Post by raymondh on 2009-12-02
> **SPARTAN-118 said:**
> that Windows only says I can shrink it down by about 6GB... and yet, there are over 20GB of available space on the "C" drive... hmm...

You're running into the so-called "immovable files" that Vista likes to put/scatter around the HD.  These are MFT's, etc.  Here's a read-through and a POSSIBLE workaround.  Understand that there are risks in the workaround that may affect your Vista install so proceed with 3 things:

1.  caution (ask/research for further clarifications if unsure)
2.  A Vista install disc (not the OEM supplied recovery CD's)
3.  A working (tested) back-up of your personal files

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

As for ADMINISTRATOR privileges ..... sorry, don't have a clue.

I gather you're no longer using WUBI :)

Regards,

---

### Post by SPARTAN-118 on 2009-12-03
I guess I'm either going to have to stick to Windows for now until I get a EHDD or use WUBI.

I really believe my Windows Vista is screwed. Every time I start the computer CHKDSK runs, and that's *every* time. In fact, my laptop's hard drive may even be failing, since Ubuntu Karmic even ran a disk check once, though neither CHKDSK nor Karmic said anything was wrong (bad sectors, etc.). gabo.cr, Windows doesn't need to run a disc check at all. It does it every time it starts.

raymondh, the only thing I have close to a Vista disc is a Home Premium upgrade disc, and I don't think you can use that to fully install Vista. To tell the truth, I don't really give a damn about what happens to Vista, since the only reason I'd keep it would be to play games, and my computer can't do that anyways (1.6GHz processor, 1GB of RAM and a crappy onboard graphics chip). The only thing I'm worried about are my files, though if need be I can start from scratch. I'll just put my *absolute necessary* files onto CDs or a USB drive, if I can find a 8GB+ one for cheap. My music, photos, and documents are examples of files I absolutely _MUST_ have. I've read about unmovable files such as shadows, but ones that take up over 20GB? No wonder Vista sucks for hardware requirements.

So, if I *did* end up backing things up onto a hardcopy of some sort, how would I uninstall Vista? Just tell the LiveCD to take up the whole drive? Or would I have to format the drive, etc.?

Also, as a side note, every time I select my locale in the disc as "Canada", the installer closes. Though I think that's irrelevant.

---

### Post by gabo.cr on 2009-12-03
You can do a guided installation with Ubuntu (taking over the hole computer) and it would delete all partitions and Vista.
Your HD should work like brand new, except for any errors on the physical drive.
About choosing the location (Canada) on the installation process, I would recommend to run a test on the Ubuntu installation CD to make sure it has no errors.

;)

---

### Post by wilee-nilee on 2009-12-03
The upgrade disc is probably a bootable install disc, but confirm this with the source you got it from. If it is it will overwrite vista so you don't want to do this without backing up. As you said this was not a option with the purchase of a external HD. I would just find out what that upgrade disc actually is and if it is actually a install disc, then wait until you can backup and reinstall the vista using the custom install to install in part of the HD then install kubuntu.

You also could if you know anybody with a Ubuntu setup load a thumb drive with Kubuntu at least a 4 gig size and set the persistent to use the whole thumb with usb creator. This would give you kubuntu with being able to update it and add stuff and it will run as fast as Kubuntu installed on the HD. A bigger Thumb would be even better.

If widows is running a checkdisc every time if you skip it it will continue to do it until you let it fully run and let it restart, have you let this happen?

---

### Post by SPARTAN-118 on 2009-12-03
> **wilee-nilee said:**
> If widows is running a checkdisc every time if you skip it it will continue to do it until you let it fully run and let it restart, have you let this happen?

Yes, every time. Every single time...

Anyways, I've installed via WUBI for now, wanted to avoid that, but I can't stand Windows at the moment.

I got the Windows Vista Upgrade disc from Best Buy, and there weren't any other discs besides the ones that said "Upgrade" on them. Looking at the box now, the original price was about $180, though I got it for much less than that. That price seems about right if you wanted to install the whole OS rather than just upgrade, and below the Upgrade box up in the top corner of the front of the box it says: 
> For users running Microsoft Windows 2000 Professional, Windows XP, or Windows Vista only. **Backup and clean install may be required.** See back of the box for details.*

I'm guessing that that most likely means you can install Vista on a totally clean HD. Though I doubt I'm going to need it, because I plan to have *only* Kubuntu on my computer. Oh, and don't tell me I *absolutely* need Windows on my PC; I don't. I have a friend who works at a Nuclear Power Plant and writes the software needed to run things, and he does it all with Kubuntu (don't know how) and has the OS installed on ***9 computers*** at home. Even his like, 10-year-old daughter has an older computer with a Kubuntu OS on it, though her parents think she's too young to have internet access readily available to her in her own room right now.

I really wish I had his technical experience right around now... I have his Skype but he's never on...

---

### Post by wilee-nilee on 2009-12-03
Well the good thing is that if you do want windows again you seem to have a install disc so, all you have to do to have just Kubuntu is described in another post. The only difference basically between the upgrade disc and full price install disc is the key.

Sarcasm
Now come on you have to have MS to be in the in crowd. ;)

---

### Post by SPARTAN-118 on 2009-12-03
Crap. Just. Crap.

Somehow when I connected to the internet and updated some files it really screwed Kubuntu up. Now whenever I try to select it in the Windows Vista Bootloader a "beep!" sounds and a GNU Grub (basically, a command line grub) appears.

I have absolutely no idea what to do. Trying "boot" produces an error saying no kernel is selected. ****. If I somehow lost all the files I _just_ transferred back to Kubuntu's partition then I'm going to be very mad at myself. *VERY* mad at myself.

I don't know how, but checking the "9.10 disc" line in the Software Sources part of KPackageManager (or something like that) might have screwed it up. It seemed to be working fine before I did that. Then I proceeded to work online for a bit before clicking the tray icon and telling it to reboot. That's when I found out I could no longer boot into Kubuntu, and why I am now asking for your help on the matter. If anybody has a command they could drop by me that could tell the GNU Grub to boot Kubuntu 9.10 then I'd be real happy.

Thanks, 
Matt.

EDIT: I forgot to mention, when the GNU Grub screens appears it says ```
[COLOR=Red][Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/file name.]
```

[COLOR=Black]Sh-grub> is the command that appears, or something similar.[/COLOR]
[/COLOR]

---

### Post by bisclavret on 2009-12-30
This is three weeks after the fact, but has anyone tried using QUALITY partitioning software to partition and format the drive BEFORE running Kubuntu or Ubuntu or Wubi? Partition Magic is a great program for partitioning the hard drive easily, quickly, and SAFELY. The partitioning utility used by Ubuntu, Wubi, and OpenSUSE are iffy at best. Several people have screwed up their Windows OS with it. Also, Ubuntu is bad to partition the hard drive and then overwrite the Windows boot sector, effectively ruining the Windows OS. 

In case you're clueless about why anyone would want a dual boot system, it's so the person can try out Linux or another OS before destroying their current OS setup, personal files, etc. From all I've heard about Linux in its many forms, I'm not sure I even want to put up with the hassle. I want to retain my current OS in case some of the functions I need are not available in Linux. I'm running Windows XP SP2, and I like the way it's set up. I do heavy graphics, video, and audio manipulation, so I want an OS that will allow me to run the necessary apps to do what I need to do as quickly and efficiently as possible. XP is stable, although more of a resource hog than most other systems (Vista being the biggest hog of all). If I can work with graphics, video, and audio files in some version of Linux and it is faster, then I will switch. IF not, I want to go back to Windows XP--the same setup that I had before trying Linux. The reason people are getting so upset over losing their Windows OS is because they already have it set up pretty much the way they need it. Linux is just a possible alternative to Windows at this point. 

Frankly, I haven't seen anything yet from Linux that impresses me in the least. It's been how many years since Linux was first released? In all those years, it seems that Linux is still in the "Maybe It'll Work and Maybe it Won't" category under the "Hit or Miss" section of the "Amateur Class" operating systems. Windows is far from perfect, and every new version goes through the typical trial period after release during which service and security releases have to be written and made available to correct flaws that the developers missed or that didn't surface during the testing phase of its development. With Linux, though, from what I've read about it (written by Linux users on Linux forums), it's just one problem after another. If Windows and Linux were automobiles, Linux would be considered a lemon--especially its installer and partitioning utilities. SOMEONE working on Linux's development should have a working knowledge of Windows operating systems in order to write an installer with dual boot options that actually recognizes the Windows OS and is capable of avoiding Windows' boot sector--and capable of recognizing the very partition that it created while installing the Linux OS. Hit or miss just don't cut it. Dependability and quality product is what matters. For some people a stable and dependable OS is necessary, and nothing less will be tolerated. Linux developers just don't seem to get the concepts called quality and dependability.

---

