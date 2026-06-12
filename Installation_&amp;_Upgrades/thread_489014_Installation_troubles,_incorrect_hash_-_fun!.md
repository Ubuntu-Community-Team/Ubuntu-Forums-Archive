---
title: "Installation troubles, incorrect hash - fun!"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by chemicalduck on 2007-06-30
Hello.

Just an FYI, I've checked through most of the FAQ and "READ BEFORE POSTING" threads, however I'm still stuck and would like some feedback if possible. If I happened to miss a page, and/or this is a simple solution, I apologize. Just trying to get this all working.

OK, so my issue is this:

I downloaded Ubuntu 7.04 - Supported to 2008, Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM). I'm looking to install this OS on my Dual Core 6300 @ 1.86 GHz. 1.00 GB RAM.

After downloading I burned the image using PowerISO to a DvD. After burning I double clicked and it popped up saying "Start Brower". After that nothing happened, so I clicked it (the icon) again and it said the same thing but nothing came up. I figured it was related to Windows or something so I took out the DvD and put it into the computer I want to install it on. I booted the comp, selected boot from CDROM and so far everything went fine. I ended up getting to the install menu, and I selected install Ubuntu and thats as far as she goes. On the top of the screen shows the word "Loading" in green, but thats it. The CDROM drive isn't working (no flashing light or sound) and after letting it site for awhile it just doesn't advance or load or anything. I restarted and tried acouple other things, like installing in graphic safe mode, no effect. It too seems to get stuck at the loading. The help menu and testing work on the DvD, however nothing else does. Not even the test CD option works.

I burned the image file onto a CDROM figuring that perhaps it being on a DvD is the issue. Same effect. It gets stuck (or doesn't pass) the loading part.

I checked all the FAQ posts on the forums and it led me to the Hash bit with "MD5SUM on Windows". I downloaded the program and tested it out. winMD5sum tells me that the downloaded image file is using Hash number bbab61a83c00dd5f7c70a5282e6d3995, and when I check the Hash list ([https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)) that number is no where to be found. I should have e296e3468358789904097fc8df29609a, correct? OK, so I'm assuming this means it was a corrupted download?

I'm now re-downloading and I decided to try the 6.06 version. 

Anyway I just want to know if someone can confirm or acknowledge that I've taken the right steps and this does indeed seem to be a corruption error.

Thanks. :)

---

### Post by Pumalite on 2007-06-30
Correct. Downloads are better if torrent. Do checksum. Confirm. Burn as an image at 1x if necessary.

---

### Post by chemicalduck on 2007-07-01
> **Pumalite said:**
> Correct. Downloads are better if torrent. Do checksum. Confirm. Burn as an image at 1x if necessary.

I took your advice and downloaded the file from TPB. I did the checksum, confirmed it, burned it and installed it just fine this time. Sweet. :)

There is now just one tiny problem that I'm curious about. I installed it on my dual core system and everything went fine. I was using my 19 inch monitor at the time. I then decided to plug in my 32 inch LCD TV/Monitor to check it out on the big screen, which I normally use, and it didn't work. After loading in, instead of showing the desktop, it just shows a black screen. I plugged in my 19 inch again and it works fine. I'm curious why it isn't working on my 32 inch. Could it be related to a DVI-HDMI connection? The DVI is connected to my video card, and on the other end is an HDMI that connects to my 32 inch LCD. It worked before with Vista and it works right now (as I type this) with XP.

I'm going to search around and see if I can find some info.

---

### Post by Pumalite on 2007-07-01
Your xorg file was configured for your monitor. For your TV you would have to reconfigure your xorg file. You have to first find out the specs for your TV. I cannot advice you there.

---

