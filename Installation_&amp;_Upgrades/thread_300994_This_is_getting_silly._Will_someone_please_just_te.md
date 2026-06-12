---
title: "This is getting silly. Will someone please just tell me how to boot the system?"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by InsomniacUK on 2006-11-16
I have been using Ubuntu since Hoary Hedgehog, and I think it's  brilliant. So, I thought i'd try and install the new Ubuntu (Edgy Eft) on my new PC.

I couldn't even get the Live CD to boot, due to graphical glitching. Safe graphics mode did nothing to help. Having Googled the problem, it seems that it's a major bug, affecting many people, but apparently being ignored.

I downloaded the alternative install CD, installed, and guess what? X won't start. Or rather, it starts, but my monitor says that it cannot the display the image.

It's really silly. What I always like about Ubuntu was the way it just worked. This is no longer the case, and nobody seems to be sure what's happening?

My graphics card is an NVIDIA GeForce 6800XT.

Is there a workaround to get the system working? Or are we going to have to wait 6 months (or more) for the next version and just hope the bug has been fixed?

I'm not trying to moan, i'm really not, but it's quite a serious bug.

---

### Post by ciscosurfer on 2006-11-16
I heard some complaints to this effect...can you describe the bug?  What's your hardware setup?  There are kernel options you can pass at boot time to get around this issue I believe.  I'll look into this a bit further and post back.

---

### Post by bulldog on 2006-11-16
Just install your graphics driver and reconfigure xserver.

I have a nVidia 6800 Ultra and no probs what so ever.

If you want a stable Ubuntu,just download and install Dapper Drake [6.0.6.1]

---

### Post by InsomniacUK on 2006-11-16
I fixed it by booting into recovery mode, running Nano to edit xorg.conf and then changing the graphics driver from nv to vesa, and then booting into a very slow desktop and running Automatix2 to install the official nVidia drivers.

Great solution if you're comfortable messing around in a CLI, but you shouldn't have to at all in a stable release, especially not for a distro that prides itself on it's ease of use. "Linux for human beings".

> Just install your graphics driver and reconfigure xserver.

That's great if you know what you are doing. If you are taking your first steps into Linux, then it's utterly useless. Most newcomers to Linux don't even know what an X server is, let alone how to reconfigure it.

> I heard some complaints to this effect...can you describe the bug? What's your hardware setup? There are kernel options you can pass at boot time to get around this issue I believe. I'll look into this a bit further and post back.

The bug seems to be with the default nVidia driver that Ubuntu uses. The system seemed to boot fine, it just refused to display anything, and on the rare occasions when it did display something, it would just be glitchy garbage, nothing workable.

Booting into Safe Graphics mode had the same effect.

As I said, after some Googling and searching here, I managed to get the system working by installing from the alternative CD in text mode, booting into recovery mode, and then editing xorg.conf using nano to use VESA instead of "nv". Then, once X started, I installed the nVidia drivers using Automatix.

Just for reference, my system specs are:
Pentium 4 HT 3.4Ghz
2Gb DDR2 RAM
80Gb SATA HDD (40gb Ubutnu/40Gb Windows)
nVidia GeForce 6800XT
19" 1280x1024 flat panel monitor.

I apologise if the tone of my post seemed impolite, it was simple frustration. Although I managed to get the system working, I do think it's a problem that needs to be addressed.

It's the kind of bug that would put new users off, and make them just stick with Windows.

---

### Post by ciscosurfer on 2006-11-16
Glad you got everything working!

---

### Post by Dual Cortex on 2006-11-16
> **InsomniacUK said:**
> I fixed it by booting into recovery mode, running Nano to edit xorg.conf and then changing the graphics driver from nv to vesa, and then booting into a very slow desktop and running Automatix2 to install the official nVidia drivers.

Great solution if you're comfortable messing around in a CLI, but you shouldn't have to at all in a stable release, especially not for a distro that prides itself on it's ease of use. "Linux for human beings".



That's great if you know what you are doing. If you are taking your first steps into Linux, then it's utterly useless. Most newcomers to Linux don't even know what an X server is, let alone how to reconfigure it.



The bug seems to be with the default nVidia driver that Ubuntu uses. The system seemed to boot fine, it just refused to display anything, and on the rare occasions when it did display something, it would just be glitchy garbage, nothing workable.

Booting into Safe Graphics mode had the same effect.

As I said, after some Googling and searching here, I managed to get the system working by installing from the alternative CD in text mode, booting into recovery mode, and then editing xorg.conf using nano to use VESA instead of "nv". Then, once X started, I installed the nVidia drivers using Automatix.

Just for reference, my system specs are:
Pentium 4 HT 3.4Ghz
2Gb DDR2 RAM
80Gb SATA HDD (40gb Ubutnu/40Gb Windows)
nVidia GeForce 6800XT
19" 1280x1024 flat panel monitor.

I apologise if the tone of my post seemed impolite, it was simple frustration. Although I managed to get the system working, I do think it's a problem that needs to be addressed.

It's the kind of bug that would put new users off, and make them just stick with Windows.


Exact same thing happened to me! I was quite annoyed!

---

