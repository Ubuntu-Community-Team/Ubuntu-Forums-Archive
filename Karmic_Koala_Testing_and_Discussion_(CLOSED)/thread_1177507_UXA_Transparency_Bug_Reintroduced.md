---
title: "UXA Transparency Bug Reintroduced?"
date: 2009-06-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by marijus on 2009-06-03
hello,

just want to ask if anybody else is seeing the UXA transparency bug introduced again since updates from june 2nd?

for those who dont know what this bug is/was about:
you can see odd white color on some windows or parts of the windows when making them transparent...

regards marijus

---

### Post by TrueTom on 2009-06-03
Yes

---

### Post by ghindo on 2009-06-03
Have you filed a bug report?

---

### Post by RD1 on 2009-06-03
I don't know about that but, I can no longer run anything (video, screensaver etc.) in fullscreen with compiz enabled. The xserver crashes and I end up back at log on screen.

---

### Post by Vanishing on 2009-06-03
mines just freeze..had to rseiub..
now playing arround with xorg.conf trying to figure something out.. 
hope there's a fix soon..

---

### Post by eldragon on 2009-06-03
i dont think it was ever gone. but im under a different distro...

---

### Post by marijus on 2009-06-03
> **ghindo said:**
> Have you filed a bug report?

not yet... wanted to ask before...


> **eldragon said:**
> i dont think it was ever gone. but im under a different distro...

it was fixed in the late jaunty dev cycle...

---

### Post by nyarnon on 2009-06-03
Sounds like the bug I was posting about, I will try to fall back from compiz and try the intel driver again.

---

### Post by Vanishing on 2009-06-03
it seems in xorg.conf:
driver "intel" nolonger works
exa seems to be gone...
anyone have any fix?

---

### Post by Amaranth on 2009-06-03
Not sure what is happening with the "intel" driver line not working (would need more information) but EXA has indeed been removed from the driver. The only supported configuration now is UXA, DRI2, and KMS. I suspect they'll remove the DRI and userspace mode setting code some time in the near future too.

---

### Post by Vanishing on 2009-06-03
Yea. I've noticed Exa been removed..which leads to freezes when compiz is enabled on(Intel Corporation Mobile GM965/GL960 Integrat
ed Graphics Controller), now I have to disable compiz to work on ubuntu .T.T

---

### Post by Vanishing on 2009-06-03
What i meant about the intel driver line is no matter if I put (driver "intel") in xorg.conf or not, vesa driver is still used..

---

### Post by Amaranth on 2009-06-03
As far as freezes with UXA go, file a bug by running 'ubuntu-bug xserver-xorg-video-intel'.

For the problem loading the driver, please attach your Xorg.0.log file.

---

### Post by marijus on 2009-06-04
the transparency issue seems to have resolved again...
maybe with the compiz update... not sure...

---

### Post by nyarnon on 2009-06-04
I can confirm that and after the gnome power manager update screen blackouts are gone too.

---

### Post by RD1 on 2009-06-04
Confirmed here also. After last night's updates, problem seems to have been resolved.

---

### Post by Vanishing on 2009-06-04
I went back to the previous xserver intel driver, and everything works now..

---

### Post by deusdiabolus on 2009-10-18
I just installed the beta of Karmic this morning (10/17) and I am experiencing the same issue with transparency (desktop widgets and OSD popups all have black backgrounds).  I haven't tried rolling back the xserver driver yet.

---

