---
title: "Complete install even with corrupt files on disk"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by superdav42 on 2009-11-20
Greetings,
I was installing 9.10 using the alternate install so I could setup RAID. The installing when fine but kept failing at "Select and Install Software" Looking at the error messages in the other console I noticed it was because it was getting I/O errors trying to read the CD. So I burnt another cd and tried again. It did the same thing. 

Not sure if the CDROM in this computer is broken or what but I was able to complete the install by unmounting the cd and then running the "configure apt" step. Then I was able to "Select and Install Software" Without error because it downloaded all the packages from the internet. 

So now my question is why didn't it do this automatically? Why don't we configure apt to try to download packages from the internet if they fail to download from the CD?

Anybody know?

---

### Post by Axos on 2009-11-20
For some bizarre reason I was having the same problem with the 64-bit desktop CD today. I burned 3 CDs with 2 different computers and got the same results. The 32-bit desktop CD I created a few days ago booted quickly and cleanly. The 64-bit desktop CD booted extremely slowly (drive spinning very slowly) and tons of read errors appeared when it gave me a look at the console screen. ???

So I went out and bought a USB flash drive, wrote the 64-bit desktop ISO to it, and installed from it instead. I'm typing this on the installed system.

Don't mean to hijack your thread but just thought I'd mention that I was getting mysterious read errors too.

---

### Post by superdav42 on 2009-11-20
CD and burners are just error prone technologies. All the more reason to make the installer more resilient to such problems. Is there are good place to put ideas like this, like a wiki or something?

---

### Post by Axos on 2009-11-20
There's this:

[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

