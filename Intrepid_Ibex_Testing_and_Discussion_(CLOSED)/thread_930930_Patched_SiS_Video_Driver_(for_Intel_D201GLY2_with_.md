---
title: "Patched SiS Video Driver (for Intel D201GLY2 with SiS662 - Mirage*1, and others)"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Master One on 2008-09-26
Up to Hardy it was possible, to compile the patched SiS video driver (formerly developed by [**Winischhofer**](http://www.winischhofer.net/), known as the Winischhofer SiS Premium Driver), that does not have distortions on higher resolutions and offers at least 2D acceleration, the appropriate thread with links to the driver archive and the patches is in the forum archive [**here**](http://ubuntuforums.org/showthread.php?t=463077).

Unfortunately it does not compile any more with the latest xorg on Intrepid Ibex. I just tried, but "make" stops with the following errors:```

       In file included from init301.h:60,
                 from init301.c:76:
sis.h:63:24: error: xf86_ansic.h: No such file or directory
In file included from init301.h:60,
                 from init301.c:76:
sis.h:970: error: expected specifier-qualifier-list before 'pciVideoPtr'
make[2]: *** [init301.lo] Fehler 1
make[2]: Verlasse Verzeichnis '/home/master/src/sisp/2d-driver/src'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/master/src/sisp/2d-driver'
make: *** [all] Fehler 2
```
Can someone please have a look, and update the patch, so that this driver can be used on Intrepid Ibex?

Any computer with a crappy SiS graphics onboard (and that's not only about the budget Mini-ITX mainboards D201GLY & D201GLY2, but also a lot of laptops) is totally unusable without that driver, since the patched Premium version still did not make it into xorg.

More info: [**here**](http://ubuntuforums.org/showpost.php?p=3504906&postcount=21)
Driver & Patches: [**here**](http://cs.haifa.ac.il/~skiselev/)
iMedia Driver & Patches : [**here**](http://www.linuxconsulting.ro/xorg-drivers/) (unfortunately also not updated since January)
Some more info on the iMedia Driver on Ubuntu: [**here**](http://ubuntuforums.org/showpost.php?p=5140451&postcount=129)

---

### Post by uPiaga on 2008-10-03
I have the exact same problem!
I would be grateful if someone could help us with this one.

---

### Post by Master One on 2008-10-03
It's pretty bad, because nobody seems to care.

What shall we do?

We can not even file a bugreport, because it is not really something the Ubuntu devs can fix, unless the patched SiS driver goes upstream to Xorg, and gets to replace the official SiS Xorg driver (which finally would resolve that issue for all distributions and Unix-like operating systems).

Besides the driver, up to Ubuntu 8.04.1 an additional kernel-patch is needed for adding the SIS 671 PCI ID (0x0671) and a new entry in sis-agp.c to detect the chipset, because otherwise AGP stays disabled (as I just confirmed in my actual Xorg.0.log: "(EE) SIS(0): [drm] Failed to acquire AGP, AGP disabled"). I did not find that error message on my Intrepid Ibex installation (with the faulty stock xserver-xorg-video-sis driver), so I guess that issue has already been fixed in recent kernels upstream.

I really don't understand, that this SiS graphics driver issue get so few feedback, because there are a lot of mainboards and Laptops out there with SiS graphics chipssets, and they all are affected.

---

### Post by bahamot on 2008-10-03
I've managed to patch the driver under FC9, which uses pcirework Xorg-server. So I think this might helped. But, sadly the result is not without bugs. Quite contrary, it has bugs that I just switch to vesa driver. I would have fixed the bugs if I've the expertise on Xorg module/driver development, sadly, I don't. So please, someone with the right skill, help us SiS672 users. 

[http://forums.fedoraforum.org/showthread.php?t=195483](http://forums.fedoraforum.org/showthread.php?t=195483)


Thanks.

---

### Post by Master One on 2008-10-03
Can you please post the patch, that you used?

I've not heard of "pcirework Xorg-server" before, but I guess, that's not the same as used by Ubuntu 8.10, right?

Also I only have used the patched Winischhofer driver up till Ubuntu 8.04.1, and AFAIK there are some differences to the iMedia driver.

It seems to be very strange, that you had to use "EXA" instead of "XAA", because "EXA" is way too unstable, and should not really be useable with that driver. MPlayer crashings can have a lot of reasons, maybe it was just a wrongly chosen Xv device.

Looks like we are just fiddling around in the dark, instead of someone with the proper knowledge able to just fix the issue.

---

### Post by bahamot on 2008-10-03
[http://rapidshare.com/files/149896152/xf86-video-sis-imedia-fc9.tar.bz2.html](http://rapidshare.com/files/149896152/xf86-video-sis-imedia-fc9.tar.bz2.html)

I didn't make diff patch, so I uploaded the whole modified source code.

Also worth to mention that if I'm using openchrome on Fedora9 (on different laptop), it also have the same issue. That is, I can't use XAA, only EXA with greedy migration heuristic turned on. So, maybe the bug I mentioned only occurred on Fedora9. But I'm not too sure.

---

### Post by Master One on 2008-10-10
Too much of a hassle, didn't want to fiddle around with the iMedia driver at all, since I had the patched Winischhofer driver kind of working on Hardy (unless the iMedia driver has any advantage).

Nobody else willing to take a closer look?

I guess adapting the SiS driver patch from Xorg 7.3 to 7.4 only requires some minor work, but I don't have the necessary knowledge, nor the time.

---

### Post by shanka_mns on 2008-10-18
Damn! I got this SiS driver working on hardy, and was so happy that it worked finally! Initially I had got some patch for 64bit mandriva, which had issues with running GTK apps (it would just hang) and after sometime at [http://ubuntuforums.org/showthread.php?t=615094](http://ubuntuforums.org/showthread.php?t=615094) thread helped be get 2d drivers for 8.04.

But just a few days back I upgraded to 8.10 and it just doesn't work anymore. I'm getting the same error as "Master One"

I tried bahamot's driver too.. I don't think it works (I didn't know the excat procedure though)

Anybody with some sort of solution in sight?

I'm seriously considering buying a cheap graphics card instead.

---

### Post by dc740 on 2008-10-20
I have the same problems trying to use the driver on my notebook (sis mirage 3+ M672)

I'm trying to fix the driver myself, but I'm not going anywhere :(

---

### Post by Master One on 2008-10-21
Someone needs to know the changes from Xorg 7.3 to 7.4, to be able to adapt the driver patch accordingly. So unless someone with the proper knowledge is finally taking a look, we SiS victims are not going anywhere after *Ubuntu 8.04.1. :(

---

### Post by dc740 on 2008-10-21
exactly... we are all in the same problem. I have no idea about xorg, so I'm coding pretty much blind here. I'm trying to search on the changelogs to change some old funcionts with newones. this page has been really useful

[http://www.x.org/wiki/PciReworkHowto](http://www.x.org/wiki/PciReworkHowto)

I changed SOME things, but I cannot even compile the driver yet. It has a lot of dependencies and is not easy to solve. I was close to compile it a few minutes ago. I had only two dependencies missing: iobase on the pciVideoPtr struct, and I didn't know how to solve it. I had another problem finding some definitions...

I don't know, I don't want to give up, but it's really hard to fix something without knowing how it works. I need to understand the how xorg works. then find out how the sis driver is written and then, understand the changes from the 7.3 to 7.4... and that's not something that can be done in two days. It takes time, but I don't have it.

good bye.

---

### Post by bahamot on 2008-10-26
I managed to get it compile with all pcirework changes, but with bugs as I said earlier. That's the problem as debugging X's modules is not easy.

---

