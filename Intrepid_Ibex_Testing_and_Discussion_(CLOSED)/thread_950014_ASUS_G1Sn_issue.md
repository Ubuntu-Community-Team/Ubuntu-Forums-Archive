---
title: "ASUS G1Sn issue"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Hideaki on 2008-10-16
I don't know if the G1Sn is the only laptop affected by this, but this problem has been going on for quite a while now from what I've seen around the internet.

The problem is that if you have a GeForce 9500m GS, and 3GB of RAM or more, then the nVidia drivers will not work with your video card. Ubuntu detects that you have an nVidia card, tells you to install the drivers, you restart, and your X server crashes telling you it could not load the nVidia modules.

A fix for the issue is found [here](http://ubuntuforums.org/showthread.php?t=849395&page=2) but it involves recompiling the kernel, which is not a very nice work around since you have to recompile every time a new version is released.

The problem is still happening with 2.6.27-10.7, and I see no hint of it getting fixed. Does anyone know anything about this, or know of someone trying to get this issue fixed at an official level without the need for kernel recompilation?

---

### Post by jadedoto on 2008-10-19
Yes. This really needs to get fixed. It doesn't look like ASUS will be patching their BIOS anytime soon and this has been an issue for nearly a year now. Drives me INSANE.

---

### Post by Hideaki on 2008-10-22
Having searched around the net for more relating to this issue, it seems that there are other laptops besides the G1Sn that are affected by this, and this problem has been going on since at least December 2007.

The easies fix would be a BIOS update from the OEM, but it seems like ASUS has no plans of releasing one for the G1Sn =/

---

### Post by jadedoto on 2008-10-25
There is actually a patch for this that has been on the NV forums for at least half a year. Lord knows why it isn't patched into the kernel by now. You just have to remap the BIOS table so that the nvidia installer can recognize the card. 

It does involve rebuilding the kernel, but that's easy enough with kpkg. However, it is annoying and by doing so your kernel will not be "supported by the Ubuntu community".

You just patch the i386 file in the arch/pci branch... here is a link to the post containing the patch: [http://www.nvnews.net/vbulletin/showpost.php?p=1671681&postcount=24](http://www.nvnews.net/vbulletin/showpost.php?p=1671681&postcount=24)

Depending on if you have a 256MB card or a 512MB card, you use one or the other patch that the poster has on that post...

Someone on that forum actually built a 2.6.24-19-rt kernel using that patch and it can be found in this post: [http://www.nvnews.net/vbulletin/showpost.php?p=1713165&postcount=37](http://www.nvnews.net/vbulletin/showpost.php?p=1713165&postcount=37)

I used that precompiled kernel for a few months without any issues.

However, last night I compiled the Intrepid development branch of the 2.6.27-2 kernel, and packaged it. If you'd like to install that kernel (which is the most recent release for Intrepid), I have it on my website here: [http://jadedoto.net/node/135](http://jadedoto.net/node/135)

But if you'd rather be nicer to my bandwidth allocations, I posted it on Megaupload here: 

headers: [http://www.megaupload.com/?d=JEDJ1K3P](http://www.megaupload.com/?d=JEDJ1K3P)
image: [http://www.megaupload.com/?d=ZGNYDSE0](http://www.megaupload.com/?d=ZGNYDSE0)

You'll need to install both .deb's and then when you boot that kernel, you should be able to install the nvidia drivers (I'm currently running the 177x release from nvidia).

Cheers!

---

