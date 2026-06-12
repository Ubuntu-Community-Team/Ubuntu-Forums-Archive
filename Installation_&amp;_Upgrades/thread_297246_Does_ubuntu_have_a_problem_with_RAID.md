---
title: "Does ubuntu have a problem with RAID?"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by boostedtsi on 2006-11-10
I do not know what is going on here but something is funky.
First I install ubuntu on my spare box, runs fine I like it. I even go as far as install it as a dual boot on my main machine.

Now, I finally get the stuff I was waiting for (hard drive coolers) for my spare box so I decide to install a second drive and go raid, simple config just mirror.

No more boot. Says boot disk error. I have my bios set up to go to CD first, then HD, HD, HD. I even set boot other device to active. Still no dice.

So giving up on that idea I decide to go back to single hard drive. Yes I deleted the array, and even unplugged second drive. It loads off CD, sees the HD and installs. Go to boot without cd after install, no dice.

What gives?

---

### Post by skwillz on 2006-11-10
What type of raid controller do you have? Software? Hardware?

In the typical case, I believe linux has fair support for hardware raid controllers (actual devices). Unfortunately, there seems to be a growing number of BIOS style software raid controllers popping up on new machines, and of course these have dismal linux compatibility so far.

You may want to refer to the following page to see if it is relevant to you.

[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

Hope that helps.

---

### Post by boostedtsi on 2006-11-10
This is a newer, but not new by any means Biostar T series board. It is SATA2, and the raid is a hardware board function.

So I dunno. I did pull the drive and found them set to different speeds, one 1.5GBs the other was 3.0GBs. So that may have been the issue... retrying to find out...

Just one of the many good things about having multiple comps... have an issue with one, you can hop on other to find help!

---

### Post by boostedtsi on 2006-11-10
well and of course when I am getting out the win2K server disk it decides to work...

dunno what the deal was, but it at least installed and will boot into it now. Now I just need to make sure the raid is working...

---

