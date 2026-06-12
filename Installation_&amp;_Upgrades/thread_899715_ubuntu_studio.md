---
title: "ubuntu studio"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by pgabhart on 2008-08-24
I used RedHat 7.0 a few years ago so I have some experience with Linux.  I installed Ubuntu on an older machine a year ago without a problem.  But what I really want to do is install Ubuntustudio on that computer.  I have attempted this several times over the last 1.5 years and spent a lot of time getting nowhere.  I had no experience with ISO files, and the instructions I have found on the internet seem to leave things out.  I downloaded the Ubuntustudio 7.1 and then 8.04.  I have tried at least 3 different programs to try to burn a bootable DVD disk.  I finally extracted the files today using ISObuster and got at the actual files as opposed to an ISO image.  

But I was surprised to see that there are subfolders in that image which I did not expect.  One is marked ISO, another one I believe is RVR, then one is marked Bootable disk, and there are about 4 individual files, not in a separate folder.  The site I downloaded the ISO from doesn't mention any of this nor does the Ubuntu Studio site.  Is just part of it, e.g. the ISO folder, supposed to be burned to the DVD to create a bootable disk, or should some of the other files go on there?

I burned the ISO folder plus the folder labeled bootable disk, but that disk will not boot in my computer, and the DVD light is coming on during the boot process

Another thing I don't know is how linking the DVD player as a slave to the CD-Rom drive affects the booting ability.  The boot-up options on the Ubuntu computer show the CD-Rom, but it does not show the DVD drive.  I added the DVD drive to the Ubuntu computer since the ISO image is too large to fit on a CD.

I also tried the disk in a laptop with XP on it, and it won't boot there either so I assume the disk is not bootable, but I have no idea why.

A typical installation instruction on the web says: 

"The installation of the base system is easy as 1-2-3 because the Ubuntu Studio installer doesn't offer a lot of options to choose from, so you cannot go wrong.

Download the Ubuntu Studio 7.04 DVD from [http://www.ubuntustudio.org](http://www.ubuntustudio.org), burn it onto a DVD, and boot your computer from it. At the boot prompt, select Install Ubuntu Studio:"

This sounds so easy, but based on my experience this is not how this works.  This writer for instance, seems to assume his reader will know how to convert an ISO image to a bootable disk.  I have sent hours trying to get this to work and still haven't succeeded so his claim it is as easy as 1-2-3 sure rings hollow.

Can anybody give me a clue what to do?  I sure would appreciate it.

---

### Post by Sef on 2008-08-24
Read [How to Write ISO files to CD]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm") and download [ISORecorder]("http://isorecorder.alexfeinman.com/isorecorder.htm").

---

### Post by Thelasko on 2008-08-25
In my opinion, the easiest way to install UbuntuStudio is to install regular Ubuntu on your machine and get everything working.

Once you do that, and assuming your machine has access to the internet, open the terminal and enter:
```
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```
That will upgrade your Ubuntu system to Ubuntu Studio (assuming you are using 8.04 Hardy Heron)

For other versions [look here.]("https://help.ubuntu.com/community/UbuntuStudio/Installation")

---

### Post by pgabhart on 2008-09-01
[QUOTE=Thelasko;5662897]In my opinion, the easiest way to install UbuntuStudio is to install regular Ubuntu on your machine and get everything working.

This is probably the best way for me to go at this point.  Since I installed Ubuntu, I have not used that computer much.  The os seems to be working fine in general, however, I have had trouble getting access to the internet through it so I need to straighten out that problem first.

Thanks for your advice.

---

