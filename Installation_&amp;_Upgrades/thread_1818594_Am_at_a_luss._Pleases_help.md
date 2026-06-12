---
title: "Am at a luss. Pleases help"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by bradlees on 2011-08-04
I am having extreme difficulty installing Ubuntu on my pc. I am fairly certain I had it on this machine before so I don't think that's the issue, but it could be a possibility. I have an older pc, purchased new 5 or 6 years ago, 2.93 ghz emachines with an intel processor, and an 80gb hdd I am attempting to install Ubuntu on as the sole OS. My other hdd runs xp, but is not connected as I attempt install.

I have tried installing: Ubuntu 11.04, 10.04, 10.04.03 all of the live iso's and the alternate versions, Mint, Lubuntu, and Xbuntu. I have tried on different hdd's, different cds, different dvds, from ubuntu's downloads, from torrents, via usb from ubuntu's home page. I have tried burning and creating the discs and usbs on 3 different pc's. I have checked the md5 sums on some of the cds and it has matched. I have tried running the wubi off of the ubuntu site when the hdd had xp on it. I have tried loading the wubi onto the drive when I had xp running on the other hdd and this one set as a slave. All have failed. Either a number or error messages or freezing. They usually freeze as the ubuntu logo comes up and the dots below it appear. I left the pc on for hours too, just to make sure. The furthest I have gotten is with the alternate version disc. This claimed it successfully installed then when I rebooted, I got this message: "the disk drive for/dev/mapper/cryptswap1 is not ready yet or present." Upon reinstalling, it froze.

I am not computer illiterate, but some things are certainly out of my wheelhouse. I had fedora running on an older pc before and ubuntu on my current laptop and a prior pc. I can give my exact system info if someone tells me exactly what they need from me to help.

I know this is long and demanding, but I would like to become a part of this community. Hopefully my troubles will help me provide advice to other noobs. However, I am becoming quite discouraged, this has taken me weeks with no success to do something I thought would be quick.

Any guidance would be greatly, greatly appreciated

---

### Post by wildmanne39 on 2011-08-05
Hi, I suggest using the 10.04 since your system is older and you most like will need to set nomodeset parameters to be able to boot, here is a guide to do that.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by bradlees on 2011-08-05
Thx,

I'm trying this as we speak. The reboot seems to have stalled though. ALmost have a 10.04 alt version downloaded to install.

Will update.

---

### Post by bradlees on 2011-08-05
I have posted a few times regarding my failed attempts to install:

'I am having extreme difficulty installing Ubuntu on my pc. I am fairly  certain I had it on this machine before so I don't think that's the  issue, but it could be a possibility. I have an older pc, purchased new 5  or 6 years ago, 2.93 ghz emachines with an intel processor, and an 80gb  hdd I am attempting to install Ubuntu on as the sole OS. My other hdd  runs xp, but is not connected as I attempt install.

I have tried installing: Ubuntu 11.04, 10.04, 10.04.03 all of the live  iso's and the alternate versions, Mint, Lubuntu, and Xbuntu. I have  tried on different hdd's, different cds, different dvds, from ubuntu's  downloads, from torrents, via usb from ubuntu's home page. I have tried  burning and creating the discs and usbs on 3 different pc's. I have  checked the md5 sums on some of the cds and it has matched. I have tried  running the wubi off of the ubuntu site when the hdd had xp on it. I  have tried loading the wubi onto the drive when I had xp running on the  other hdd and this one set as a slave. All have failed. Either a number  or error messages or freezing. They usually freeze as the ubuntu logo  comes up and the dots below it appear. I left the pc on for hours too,  just to make sure. The furthest I have gotten is with the alternate  version disc. This claimed it successfully installed then when I  rebooted, I got this message: "the disk drive for/dev/mapper/cryptswap1  is not ready yet or present." Upon reinstalling, it froze.

I am not computer illiterate, but some things are certainly out of my  wheelhouse. I had fedora running on an older pc before and ubuntu on my  current laptop and a prior pc. I can give my exact system info if  someone tells me exactly what they need from me to help.

I know this is long and demanding, but I would like to become a part of  this community. Hopefully my troubles will help me provide advice to  other noobs. However, I am becoming quite discouraged, this has taken me  weeks with no success to do something I thought would be quick.' previous post

Now I tried an older version of ubuntu 10.04 alternate version. Ran the whole install through to reboot with nomodeset as suggested by another user. Gets to grub menu and any option I select goes to a screen with a small dot in the upper left corner and is unresponsive.  WTF??????!!!!!!!!!!!!!!!!!! 

Any guidance would be greatly, greatly appreciated

---

### Post by mikewhatever on 2011-08-05
I suspect this is a graphics problem, can you check what graphics adapter is there.

---

### Post by nativehound on 2011-08-05
Did you create a /swap partition during the install?
To check boot up a live cd and run 
```
cat /proc/swaps
```

---

### Post by Toz on 2011-08-05
Sounds like a blank screen problem. Here is a link to a troubleshooting thread that might be of help: [http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")

---

### Post by Iowan on 2011-08-05
Threads merged.
From Code of Conduct:
> Do not cross post, or post the same thing in multiple locations.
A more descriptive title might yield better results... :)

---

