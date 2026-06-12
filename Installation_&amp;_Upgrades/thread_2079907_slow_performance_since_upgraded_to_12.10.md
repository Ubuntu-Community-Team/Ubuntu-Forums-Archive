---
title: "slow performance since upgraded to 12.10"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by plh on 2012-11-02
hi folks,

I just upgraded yesterday to 12.10 on an asus g53s.
Everything worked fine, no problem... Until I discover that I can't even listen to a FLAC record without the music being interrupted once in a while, sometimes for a second or so! Not to mention vlc, in which I can see an interesting variety of pixel blobs !...

That happens wether I Choose xorg driver, NVIDIA recommenced or experimental driver. It even happens if I choose lightweight DM as lxde instead of unity, exactly same problem. killing compiz does not solve the pb either

I must mention that the problem arises after about 1 minute of use ; the first minute is ok... Of course I can't consider rebooting every two minutes ;)

IF someone has a hint, I'll be happy to share it ;)

Thanks in advance

---

### Post by nwalkey on 2012-11-03
Install went okay and nothing crazy looking in system manger? What are the specs of the computer and what did you upgrade from? Also is everything updated? 12.10 works beautifully on my laptop.(mind you I haven't used anything but windows 7 on it).

---

### Post by plh on 2012-11-03
hi nmalkey, thanks for answering.
My laptop is an asus G53S, i7 8-core, 6GB RAM, Nvidia 460M. Win7 was installed when I got it, so I'm in dual-boot. I had 12.04 just before and no performance penalty, though the Nvidia driver often triggered warning/error messages.
Everything was updated since I always reformat the system partition during install

---

### Post by nwalkey on 2012-11-03
That sucks. I'm on a similar gaming laptop and have had little problems. When I first installed 12.10 I was getting a ton of errors but those are gone and I got my graphics card working with optimus(bumbleebee). Hopefully you get it figured out.

---

### Post by Ghost_Mazal on 2012-11-03
I have the same performance issues.
12.04 ran like a warm ice cream.

But 12.10 is dreadfully slow and buggy.

---

### Post by plh on 2012-11-03
ok I'm sad for you Ghost but at least I have a good hint there really is a problem.
Hope next kernel version will solve it, or someone else has an idea ! :(

---

### Post by Ghost_Mazal on 2012-11-03
plh at least my Nvidia drivers works now ,

I did the solution in this thread , post nr 3 :

[http://ubuntuforums.org/showthread.php?t=2073060](http://ubuntuforums.org/showthread.php?t=2073060)

And it worked for me. But the system is still very slow.
And I have a few people on our mailing list also complaining that 12.10 is very
slow and sluggish.

---

### Post by plh on 2012-11-03
ok, good for yoy ;)
Mine instantly worked fine... Same result ith all 4 drivers I tried, wether Nvidia or Xorg. Works (in the Nvidia case, with +/- error messgaes popping up) but awfully slow.

---

### Post by pmerrill on 2012-11-17
My 12.10 is slow as well. Machine specs are:
Mainboard :	MICRO-STAR INTERNATIONAL CO.,LTD DKA790GX Platinum (MS-7550)
Chipset :	AMD 790GX
Processor :	AMD Phenom II X4 965e @ 3400 MHz
Physical Memory :	3072  MBDDR2-SDRAM
Video Card :	ATI Radeon HD 3300 Graphics
Hard Disk :	Seagate ST3320613AS ATA Device (320GB)

I notice on my Win 7 if I click on Chrome it will take about 1 sec to open. If I click on Chromium on Ubuntu it takes about 5-7 seconds to open. Firefox on Win 7 takes about 7 secs, on 12.10 it's like 15 or so seconds. 

Any ideas?

---

### Post by plh on 2012-11-24
Incredible: I didn't find ANYTHING on this issue anywhere! You prove that I'm not the only asus user with such problems, so what ?

---

### Post by Mark Phelps on 2012-11-25
> **pmerrill said:**
> Any ideas?

Yeah -- you're using the default open-source Radeon drivers on 12.10 because AMD dropped support for Restricted drivers for the HD 2x/3x/4x series cards this summer.  Now, you're relegated to using the default drivers -- which don't have the same runtime performance as the restricted drivers.

I'm in the same boat (since I have an HD 42xx card) and have noticed that 12.10 runs noticeably slower than 12.04 -- on the same hardware.

---

### Post by plh on 2012-12-01
Hi Mark,
I'm not so sure: I have a Nvidia GTX460M, not a radeon...

---

