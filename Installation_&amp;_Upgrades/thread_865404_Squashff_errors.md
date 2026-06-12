---
title: "Squashff errors"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by god0fgod on 2008-07-20
The first time I tried to install ubuntu I went into this busybox shell or whatever. The second time it left the loading screen and then gave a huge list of Squashfs errors, whatever they are. They went on and on next to an increasing number in square brackets. It was very fast to see much of the errors but I know there was two that repeated and it involved something to do with failing to read blocks.

Can anyone help? Thank you.

Oh and I'm trying to install ubuntu 7.10.

Processor: Intel(R) Pentium(R) 4 CPU 3.06GHz HT
Memory: 1022MB
Hard Disk Model: ST3160812AS

---

### Post by god0fgod on 2008-07-20
I should also say I get an error something like "pci cannot allocate resource region 3". This is before the loading screen.

I managed to get further while using "ide=nodma". A cursor that I cannot move, appears. The terminal half appears and I get an error like "there was an error while creating the child process for this terminal". Can't remember it exactly. I cannot do anything from this point. 

Any thing else I can do?

---

### Post by god0fgod on 2008-07-20
I'm getting "PCI: cannot allocate resource region 3" after the loading screen now. following that I get quite a few "Module unknown". :( Or it was perhaps "Module not found". Can't remember.

---

### Post by Rocket2DMn on 2008-07-20
If you are getting squashfs, the cd is probably corrupt, either because of a bad image or a bad burn.  You should check the md5sum of the .iso file, and if it checks out, burn it to a cd-r at a slow speed like 4x to help prevent write errors.
[uhelp]community/HowToMD5SUM[/uhelp]
[uhelp]community/UbuntuHashes[/uhelp]

---

### Post by god0fgod on 2008-07-21
I'm not getting them any more after placing "ide=nodma". The CD is a requested one because my burned copy wouldn't work. I tested the CD for defects and it was fine.

I have done research and it seems ubuntu hates IDE for some weird reason. The fact that this PC uses IDE for the hard drives is proving a problem.

Since I'm getting "PCI: cannot allocate resource region 3" and "module not found" problems and ubuntu doesn't boot probably at all, what could I try bearing mind this computer's hardware uses IDE connections?

I will also say that after the load screen it seems it starts to do those checks with the "[ OK ]" but it then stops rather quickly and shows the "PCI: cannot allocate resource region 3" error etc.

And thank you for the reply, Rocket2DMn. It is much appreciated.

---

### Post by god0fgod on 2008-07-21
I just got further by added the boot options acpi=off and noapic. Ubuntu kinda loads but has many problems. The start up sound goes all weird and there are many other problems. I have this video - htttp://www.godofgod.co.uk/my_files/ubuntu_install.mp4 After the video I try to click ont he show desktop button and then it says it is unsupported. I then load the examples folder and it goes black before appearing the folder and crashing.

---

### Post by Rocket2DMn on 2008-07-21
The LiveCD is not likely to have support for many codecs, esp. proprietary ones.  The LiveCD isn't usually a "sign of things to come" - most problems people have with the LiveCD are fixed after installation.  For those that aren't, it is easy to troubleshoot them after the OS is already installed.

---

### Post by Ronno6 on 2008-07-21
I've seen other references to the   ide=nodma   line being added to boot time options. 
I'm new to this whole Linux O/S, live CD's etc. I.m trying to install or run Mythbuntu a mew AMD64 build, and all I get is the SQUASHFS errors by the pageload. I've burned several ISO's on different disks at different speeds and on different burners, but all have the same result. 
How does one add that nodma line to a live CD at or during bootup? Or, should there be a native O/S on the HD before attempting this?

---

### Post by avtolle on 2008-07-21
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) will help you in adding the line to the live CD during bootup. Given that you are receiving so many errors, I wonder if the iso from which you burned the CDs is corrupt. Did you do a md5sum check before burning the iso as an image?

---

### Post by Ronno6 on 2008-07-21
I have not verified the MD5SUM . There is a program that I need to download in order to do this ?

---

### Post by avtolle on 2008-07-21
Take a look at [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) for assistance.

---

### Post by Ronno6 on 2008-07-21
I've downloaded and installed winMD5SUM. I inserted the burned disk i the drive, started winMD5SUM, browsed the CD, as I could not "open" the entire contents.Problem is, when I insert the disk into the drive, windows gives me a message "Invalid Disk" There is a file on the CD called md5sum.txt  Opening this file fills in a string of numbers and letters into the MD5sum box. Retrieving the checksum from the Mythbuntu side gives another string that is radically different from the one on the CD. I guess this is the problem, or, am I doing something incorrectly? Where do I go from here?
Thanks for all your help so far.

OK. An update. Back to basics. I downloaded Mythbuntu , then burned the .iso to CD via Nero. THOSE are the discs which have the different MD5SUM. Those are the ones that give the SQUASH errors at installation.
 
I burned other disks using Windows XP copy " file to CD for the Mythbuntu files. THOSE discs, the checksum matches, but I cannot boot form them. I get a "disk read error" at attempted boot up. Now what?

---

### Post by avtolle on 2008-07-21
Not too sure what you are saying, but the burn needs to be an iso image, not a copy, or create a data CD, etc. , to CD. It appears that there was a problem burning via Nero, given the differing md5sum. At this point, I can only suggest burning as an image at a low speed (4x) to CD-R. That's what works for me.

The disk read error on the others is likely due to your copying, not burning as an image. Good luck.

---

### Post by Ronno6 on 2008-07-21
Well, I am learning. When I click on the "Direct Desktop md5sum Download" selection on the Mythbuntu download site, I have received differing results. Sometimes I get a white screen with a string of letters and numbers across the top. I believe this is the checksum? Other times I get a download dialog box, which downloads the checksum file to desktop. If I open that file using winMD5SUM, I get numbers that do not match anything I've downloaded or burned. 
I am downloading the installation   .iso file again from scratch for the 3rd time. I'll see if the checksum matches the one I've downloaded. 

This is all very confusing to me. Thanks again for your help. Any and all will be appreciated.

---

### Post by confused57 on 2008-07-21
> **Ronno6 said:**
> I have not verified the MD5SUM . There is a program that I need to download in order to do this ?
Deleted...need a cup of coffee, didn't see the 2nd page of this thread.

You're getting great advice by others in this thread, but you might want to try installing with the Alternate install cd, if you're unable to get the live cd to boot.

---

### Post by Ronno6 on 2008-07-21
I can't remember if I've tried that,yet. Guess I'll give it a shot.  I've been checking checksums till I'm blue in the face. Nothing seems to match. I can even get different checksums from the Downloads section of Mythbuntu. Sometimes I ger a download box. That checksum differs from that of the downloaded .iso file. Sometimes I just get a white screen with a string of letters and numbers texted at the top. That checksum (if that is what it is,) matches the checksum of the downloaded .iso file. BUT, I cannot get Nero to burn an .iso image that has the same checksum !! Plus, when I place the CD in the drive, Windows gives me an error message "Invalid CD Dectected". I have to scroll the files on the CD and i see a file labeled "md5sum". Opening that gives yet a DIFFERENT checksum. 
Mythbuntu supposedly has several providers to mirror the .iso image. I wonder if that is some of the problem with the differing checksums, even on the download site. 
I am not very skilled in this computer world, but these things just don't seem to make sense.

---

### Post by god0fgod on 2008-07-21
> **Rocket2DMn said:**
> The LiveCD is not likely to have support for many codecs, esp. proprietary ones.  The LiveCD isn't usually a "sign of things to come" - most problems people have with the LiveCD are fixed after installation.  For those that aren't, it is easy to troubleshoot them after the OS is already installed.

Are you saying I should attempt an install? I think it's too risky with ubuntu in this state. I'll simply wait until I have a MacBook and will try ubuntu again.

May seem pointless to install a Linux distrobution on OS X since OS X is fine and can run Linux programs anyway but Compiz Fusion is too cool not to have.

---

### Post by Rocket2DMn on 2008-07-21
You should do what you are comfortable with.  If you don't trust the LiveCD (and I wouldn't if it has errors), then don't use it - you may want to try the alternate install cd (as was mentioned a few posts ago).  That has a text installer without a live session, but it is easy to use.
If you don't want to install at all, then don't - it's all about what is best for you.  Ubuntu will be here when your new laptop arrives.

---

