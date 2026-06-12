---
title: "Trouble installing ubuntu on my Laptop"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by darkdemon on 2008-03-01
I recently bought a brand new Acer, windows vista Laptop. Ever since I've got I've had constant trouble with it, Vista broke, so I installed XP, then that broke, it just seems to be "one of those systems"

So anyway, I figured I'll just wipe the lot and start fresh with linux.
I didn't know anything about it so I followed the guide's etc. and got a copy of Ubuntu X64. (I've also tried this with another ubuntu).

After running Live, which worked fine, I tried to install it, it didn't work for an unknown reason on the other version of ubuntu but when I tried with the X64 package it appeared to work completely.

however when I start it up it hangs at the boot screen for a minute and then drops into the shell.
I've run the recovery mode and it gave me this message:

"Alert! /dev/disk/by-uuid/e4927621-fa02-4275-8471-184bbda8c9cc does not exist. Dropping to a shell!"

and goes back to where I started.

I'm not sure what the hell I'm meant to do and what this means, can you help me out?

I'm using an Acer Aspire laptop, 7520-6A1G-08Mi

---

### Post by Pumalite on 2008-03-01
Get Gparted Live CD. Burn to disk and boot from it.  Delete everything in your hard drive. Make new large partition of your whole hard drive, format ext3. Install Ubuntu.

---

### Post by darkdemon on 2008-03-02
I tried this to no avail, It gave me the exact same message.

Any other suggestions?
(p.s. the code at the end of the error is now different.)

---

### Post by templa edhel on 2008-03-02
just a guess but maybe the cd is messed up. try re downloading and check the m5d sum or w/e. then reinstall.

---

### Post by Pumalite on 2008-03-02
[http://ubuntuforums.org/showthread.php?t=595979](http://ubuntuforums.org/showthread.php?t=595979)
[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)
Burn a new CD. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on your iso, burn at 4x or less in good quality CD-R media, as image, check CD integrity before install.
Maybe you should DBan your drive before using Gparted: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by darkdemon on 2008-03-02
"The CD-ROM integrity test was successful. The CD-ROM is Valid."

But I'll try your way anywho.

That's for the lightning response time.

---

### Post by darkdemon on 2008-03-02
Nope this hasn't worked either, no matter what I do I always get back to the same dropped shell.

(I haven't yet tried DBAN, I'm unsure, will it harm the bios in any way?)

---

### Post by Pumalite on 2008-03-02
DBan will not touch your BIOS. It's to clean the garbage left by other installations in your hard drive, especially Windows.

---

### Post by darkdemon on 2008-06-22
I never did get linux installed on that Laptop, it's got windows on it again now, works fine...

---

