---
title: "Kubuntu Karmic + Open Source Radeon Drivers = Fail"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by deathfrog on 2009-10-10
Where do I start? If I enable desktop effects one of four things will happen.

1) I get just a black screen and nothing else.
2) I get past the black screen but the window borders disappear.
3) I get a white screen and nothing else.
4) Everything goes fine, but then I get logged at out random. This only happens if desktop effects are activated.

Add this to all the other little problems like Konqueror suddenly stopping working with Flash, random hardlocks, KPackageKit being broken again, the desktop folder icons disappearing, the little visual artifacts that appear when you use desktop effects with the open source Radeon driver, the random screen dimming, and it appears that Kubuntu is heading for disaster yet again.

Ati and linux really are a match made in hell.

---

### Post by SeePU on 2009-10-10
> **deathfrog said:**
> Where do I start? If I enable desktop effects one of four things will happen.

1) I get just a black screen and nothing else.
2) I get past the black screen but the window borders disappear.
3) I get a white screen and nothing else.
4) Everything goes fine, but then I get logged at out random. This only happens if desktop effects are activated.

Add this to all the other little problems like Konqueror suddenly stopping working with Flash, random hardlocks, KPackageKit being broken again, the desktop folder icons disappearing, the little visual artifacts that appear when you use desktop effects with the open source Radeon driver, the random screen dimming, and it appears that Kubuntu is heading for disaster yet again.

Ati and linux really are a match made in hell.
Yes, I can confirm the ATI issue in Ubuntu (Live CD Karmic) and there has been a couple other posts reporting the issue.  Unfortunately, Ubuntu devs seem to be ignoring the issue or just taking ages to fix it.  Karmic is already at beta and the issue is still the same.  

Don't tell the fanboys, though.  They ignore the complaint since Ubuntu/Karmic is perfect. :rolleyes::(

---

### Post by The Recorder on 2009-10-10
> **deathfrog said:**
> Where do I start? If I enable desktop effects one of four things will happen.

1) I get just a black screen and nothing else.
2) I get past the black screen but the window borders disappear.
3) I get a white screen and nothing else.
4) Everything goes fine, but then I get logged at out random. This only happens if desktop effects are activated.

Add this to all the other little problems like Konqueror suddenly stopping working with Flash, random hardlocks, KPackageKit being broken again, the desktop folder icons disappearing, the little visual artifacts that appear when you use desktop effects with the open source Radeon driver, the random screen dimming, and it appears that Kubuntu is heading for disaster yet again.

Ati and linux really are a match made in hell.

Exactly the same here.  I have Gnome, Xfce, Enlightenment, LXDE, etc, on my machine - All the others work fine.  But, keep the faith - There's still a couple of weeks until final release.

---

### Post by clhsharky on 2009-10-10
HI

I have a ATI X1650 on Ubuntu Karmic 64 open source stack of course and its better than 8.10 with a 9.3 driver. Same machine different boots. Did you do fresh install. Sorry I cant help, do not know anything about Kubuntu, I would think its something fix-able. The only thing I haven't been able to get going is the KVM virtual machine yet.

---

### Post by 11hjpphty76lkjj on 2009-10-10
I'm having similar issues.  Even with the ATI Restricted driver and the ATI offical driver.  No go.  I'm glad I can still ssh into the box so I can reset the xorg.conf.

---

### Post by The Recorder on 2009-10-10
> **clhsharky said:**
> HI

I have a ATI X1650 on Ubuntu Karmic 64 open source stack of course and its better than 8.10 with a 9.3 driver. Same machine different boots. Did you do fresh install. Sorry I cant help, do not know anything about Kubuntu, I would think its something fix-able. The only thing I haven't been able to get going is the KVM virtual machine yet.

No, I did not do a fresh install, but, in this case I don't think this has anything to do with the problem.  Like I said, all of my other Karmic setups work fine with or without compositing.  Kubuntu seems to work ok without compositing, but switch on it's own compositing (Desktop Effects) or Compiz-Fusion and all goes downhill.  There is definitely some relationship problem between the new (free) ATI drivers (for "older" cards - mine is an X700) and Kubuntu.

---

### Post by clhsharky on 2009-10-10
HI again The Recorder

[QUOTE]No, I did not do a fresh install, but, in this case I don't think this has anything to do with the problem. Like I said, all of my other Karmic setups work fine with or without compositing. Kubuntu seems to work ok without compositing, but switch on it's own compositing (Desktop Effects) or Compiz-Fusion and all goes downhill. There is definitely some relationship problem between the new (free) ATI drivers (for "older" cards - mine is an X700) and Kubuntu./QUOTE]
 A lot of people do seem to have problems so maybe its hit or miss.
I did a fresh install at alfa 5 and updated sense. Compiz-Fusion works but I admit I'm not into spinning cubes,Tux Racer get 100+ fps, glxgears 13000+ I know that it doesn't mean anything other than it works. Google earth works and have had no lockups at all. I don't use open source stacks on any laptops, power-management not good  enough AFAIC. One other thing I'm using updated X.org stable Karmic drivers & libraries from the PPA's.
This may not help any one but I know some systems are fine at this time. 
Good Luck, It will get better just like Jaunty did.

---

### Post by The Recorder on 2009-10-11
The following bug report may have something to do with our problem.  It deals with the package "libdrm-radeon1", direct rendering, and various kernels over the past SEVERAL months, up to the present time, with mentions of Kubuntu and Karmic.


[https://bugs.launchpad.net/debian/+source/libdrm/+bug/348332](https://bugs.launchpad.net/debian/+source/libdrm/+bug/348332)

---

### Post by lucianct on 2009-10-11
i have a X1100 (200M) card and everything but desktop cube works. whenever i enable desktop cube i cannot switch the desktop. everything worked before with the proprietary drivers, but now they do not support my card.

---

### Post by Thehound on 2009-10-25
I can enable composite and it works well most of the time. However, it seems to conflict with Adobe Flash, as of Karmic. Flash makes everything slow and cpu intensive, unless you disable it while running flash. There is a neat plasmoid that lets you toggle desktop effects and it proves useful in this case. None of the issues previously described, though. Could it be because I'm using the open source drivers from the ppa? Maybe give that a shot guys and see if it helps.

---

