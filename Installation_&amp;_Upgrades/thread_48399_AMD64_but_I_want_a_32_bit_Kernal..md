---
title: "AMD64 but I want a 32 bit Kernal."
date: 2005-07-12
forum: Installation &amp; Upgrades
---

### Post by radeon4 on 2005-07-12
I have an Athlon4 3200+ but the support for apps is not where I would like it to be.  So I decided to install the 32 Kernal but I am not sure which I should use?  I did an install with the Generic kernal but it does not support my total RAM, I have 2 gig.  So I was wondering if I should do a fresh install and if so what Kernal should I use or is there one avaliable for what I am trying to accomplish?

Any help would be greatly appreciated, and these forums are really great thanks all for your hard work.

---

### Post by JamesRock on 2005-07-12
I know the Kernel with the -k7 extension is suited to AMD64 chips in 32-bit mode. I don't know why your system would have trouble addressing 2gb of memory? I thought the limit was 4gb, if any?

I use an AMD64 on the default Ubuntu install and it works fine, however I only have 1gb of RAM

Maybe just post one of your 1gb chips to me and it will solve your problem?

---

### Post by trivialpackets on 2005-07-12
[QUOTE=radeon4]I have an Athlon4 3200+ but the support for apps is not where I would like it to be.  So I decided to install the 32 Kernal but I am not sure which I should use?  I did an install with the Generic kernal but it does not support my total RAM, I have 2 gig.  So I was wondering if I should do a fresh install and if so what Kernal should I use or is there one avaliable for what I am trying to accomplish?

Any help would be greatly appreciated, and these forums are really great thanks all for your hard work.[/QUOTE]
 With the Athlon, I would typically, as I did do apt-get linux-k7, which is optimized for the athlon processors.  Not positive as to the amount of ram that it supports, and I'm not at my system, so I'd advise looking into the actual kernel version that is available through synaptic and possibly reading up on the web, kernel.org I think.  May need to have a recompiled kernel, which is fun.  Good luck, and check out the linux-k7.  Hopefully this will help.

---

### Post by radeon4 on 2005-07-12
Thanks guys I apprecate the information.  I just wish the apps for 64bit were better supported.

---

### Post by braveerudite on 2005-07-12
As far as my understanding goes 32bit CPU's are the one limited to 4Gigs of RAM and AMD 64 way beyond.

---

