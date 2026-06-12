---
title: "Ubuntu 10.10 on PS3 no boot, install CD doesn't load"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by EricM80 on 2010-10-14
Hello,
has anybody tried 10.10 on their PS3 (FW 3.15)? I first ran an update from 10.04 (which was working fine, including ext4 FS), and upon rebooting after the update, all I had was a black screen after PetitBoot. I then tried to do a clean install with the 10.10 PPC+PS3 Alternate CD, but same black screen after selecting any type of install from CD in PetitBoot. I then installed the OtherOS that's on the 10.10 CD (KBoot); same black screen. Went back to PetitBoot and tried the PS3 desktop 10.10 CD; same problem.
I was almost ready to give up and reinstall 10.04 when I thought of using the "linux-old" option in PetitBoot. This loaded the newly upgraded Ubuntu 10.10 on my HD, with the difference that it's using kernel 2.6.32 instead of 2.6.35. This works fine.
So here's my question (at last :) ): was the PS3 port of 10.10 tested by anyone before being pushed as a release on cdimage.ubuntu.com, or is there an incompatibility with kernel 2.6.35 that was never noticed, except for here where it didn't seem to go anywhere: [http://ubuntuforums.org/showthread.php?p=9849524](http://ubuntuforums.org/showthread.php?p=9849524)
? If I'm the only one left on earth with firmware 3.15 and interested in Ubuntu on PS3 at this point, please feel free to close the thread :P

---

### Post by AaronSells on 2010-10-17
No, you are not the last one on Earth, good sir!  I, too, am a proud owner of a firmware 3.15 Playstation3 and wish to run the latest Ubuntu distros.  I am experiencing the same 2.6.35 kernel woes as you.  I submitted a bug report here:

[https://bugs.launchpad.net/ubuntu-ps3-port/+bug/662457](https://bugs.launchpad.net/ubuntu-ps3-port/+bug/662457)

---

### Post by EricM80 on 2010-10-18
And then there were two :)
Thank you for submitting the bug, and confirming the problem. In the meantime I switched to yellow dog 6.2, quite a bit snappier than 10.04 I would say. But I'm willing to try any fix that's offered for Ubuntu 10.10!

---

### Post by feilipu on 2010-10-28
I tried installing the backport 2.6.35 kernel (compiled using the standard .config) on my 10.04 installation. Same issue, doesn't work.

Unfortunately, I'd gotten lazy with keeping oldlinux up to date, so I'll have to go and reinstall 10.04 or try 10.10.

Would be very nice to have a 2.6.35 kernel working though, as it adds support for SSD TRIM, and the 32GB SSD I installed in my PS3 makes it very snappy. Worth doing.

---

### Post by monoschwarz on 2010-12-08
hi boys 

downgrade works 

you are not the last boy 
" and downgrade ist perfect "

---

### Post by darckhart on 2010-12-13
well after some google fu i can find this thread!

i also have FW v3.15 and cannot install 10.10 on my ps3. however, i'm getting stuck at a different point. it deals with ps3 ehci usb error. maybe you guys have some ideas? i opened a thread here: [http://ubuntuforums.org/showthread.php?t=1644073](http://ubuntuforums.org/showthread.php?t=1644073) 

but i'll dl 10.04 and give that a try tonight since you guys seem to have gotten it to work with that build.

TIA!

---

