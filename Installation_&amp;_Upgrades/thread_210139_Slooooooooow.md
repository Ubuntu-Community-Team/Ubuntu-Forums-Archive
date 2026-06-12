---
title: "Slooooooooow"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by Pheusion on 2006-07-06
Ok, I loved the LiveCD when I tested it, and I got a new laptop yesterday. So I figured hey, I'll try Ubuntu. The laptop only came with 192 ram so doing the LiveCD install was a no go. search the forums and I eventually get the Alt image and burn that, under K3b in Auditor Nix. 

Came into work this am, slap the disk in, and 30 minutes later I am at the SPLASH screen for the install. Unnacceptable.

Thinking I have a corrupt disk (Although MD5's all sound) and verified the disc as well. I redoanloaded and re-burnt the image. 

Same thing. I am 40 NEW minutes into this now and still no install....

Being inpatient, I slap my good ol TRUSTY auditor disc in, bam. 5 min FULL install including the WM.

I begin the Ubuntu process again, which is where I am now. 23 minutes and I am YET to see the install options (IE Text Mode, OEM Mode etc)

I searched the forums and I see no answer to resolve this, I REALLY want ubuntu on this laptop.

In 10 years of working with *nix professionally, this is the slowest binary install I have seen  (Lunar Nix, source based, all night install) 

Anything I can do to speed this up?

---

### Post by Derek Djons on 2006-07-06
I think there's a combination bug working here. With past Ubuntu editions I also had some problems with one specific computer. After some time the installation screen came up but it was all corrupted. Also I had problems after choosing a installation mode that the installation just froze and etc.

I think it's a combination of specific hardware and perhaps a bug. But sorry, I do not know what's actually going. In my case with future releases the problems dissapeared as if they never excisted.

---

### Post by Pheusion on 2006-07-06
2nd new cd, unable to read CDROM. Dammit. right after initrd initialization...

Thx for the response, I will keep trying, if all fails I'll wait until a newer version comes out, hopefully it will be ironed out...

It's been a long time since an OS made me excited, (OSX was the last one) and the LiveCD did just that, so Ill cross my fingers and keep hoping!!

---

### Post by Grim_n_Evil on 2006-07-06
I installed Ubuntu from the LiveCD on a 192 RAM laptop without any trouble

---

### Post by Pheusion on 2006-07-06
The LiveCD works good, as I have tested and isntalled from that media on several desktop PC's...

On my laptop though, I freeze while waiting for the installer to run...

I downloaded the torrent file version of alt and it is running MUCH faster, I actually got past the basic install options and it is now scanning /cdrom/pool/main

So hopefully this will be it and it will isntall from this point... Ill update afer I find out...

Thansk all

---

### Post by Pheusion on 2006-07-06
Dammit Dammit.

Got furthur than last time, but same problem in the end, 
Error during install, cannot copy files from CD (3rd DIFF disc as well as diff source)

For some reason it goes through reading the CD fine, verifies, mounts ok. Then gets to the part of installing and it wont see teh CD anymore....

ug

Gonna try teh LiveCD one more time

---

### Post by Pheusion on 2006-07-06
ARG!

The LiveCD is upto qparted, but fails with "Error While creating /dev/hda*"

It wont format or create any parts, also fails when I try to let it do it itself with "Erase entire disk"

Gonna search on this now...

I know it works as I can slap Auditor on it with no issues

---

### Post by cookfromfrozen on 2006-07-06
I had this same problem.

I downloaded the desktop version of Dapper (with the LiveCD installer) and burnt it to a CD-RW because I didn't have any CD-Rs.  When I clicked on the "Install" shortcut on the desktop,  the installer would hang.

I erased the CD-RW and burned the alternate version onto it.  The menu would come up (install, OEM mode etc) but the CD would spin down very slow at the "Loading Linux Kernel" stage and eventually fail with some error message.

The next day I bought some CD-Rs and burnt the same ISO to those CDs.  It worked perfectly.

Only thing I can suggest is try a different brand of CD-R.  If that still doesn't work then Ubuntu must be picky about certain CD drives.  Perhaps you could pick another one up cheaply somewhere?

Hope you'll be able to install Ubuntu soon, I know how frustrating this problem was for me.

---

### Post by frodon on 2006-07-06
According to [this page]("http://releases.ubuntu.com/6.06/") 192Mo of RAM is the minimum setting to run the liveCD so i would say that it's normal to get speed problems with 192Mo of RAM.
If you wish to install ubuntu i strongly advice you the alternate CD which use a text based installer which is really faster than the liveCD.

---

### Post by Pheusion on 2006-07-06
Ive tried the Alt CD, (read above) Fails...

The LiveCD is the closest it will come, but it gets to Espresso and fails still with various errors (#1 Cannot create filesystem, #2 Installer crashed, #3Stops reading disc (Both LiveCD and Alt)

These are 3 seperate images dowloaded from 3 seperate mirrors

Last thing I am trying is to do the LiveCD isntall via safe Mood gfx as suggested on another site.  Seems the HP pavilion laptops have issues with ubuntu, as several reports of teh same issue can be found via google...

If teh safe mode does not work, Im moving bak to Auditor for now...

---

### Post by Pheusion on 2006-07-06
Thx for the info cookfromfrozen, 

This is on 2 diff CD-R media brands, one memorex, other generic.

I jsut got this Laptop yesterday (Traded a PSP) so Im not going to rush out and buy periphs for it when it is 100% functional, other *Nix OSs work great with it (Auditor is a 5 min full install w wlan and ethernet) 

Most likley, I will have to wait until the next release when hopefully it will be resolved...

---

### Post by Pheusion on 2006-07-06
So far so good!!

Choosing "Safe Mode" allowed me to boot into the LiveCD, and from there the isntall process worked fine.

No other changes was done so I am unsure why the "Unable to create filesystem"  error exists during normal isntall and not for "Safe Mode"

But at this point I dont care, as it is up and RUNNING and looking beautiful...

For reference, this is the site I used to get info:
[http://justinsomnia.org/2006/06/ubuntu-up-and-running/](http://justinsomnia.org/2006/06/ubuntu-up-and-running/)

I followed that and lo and behold, I have Ubuntu

=)

Thanks to all who helped me out with this

---

