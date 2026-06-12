---
title: "Any way to install Gstreamer Plugins Bad?"
date: 2010-02-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by shafin on 2010-02-13
After my upgrade to lucid, I had to remove Gstreamer-plugins-bad package as it was holding my upgrades. But now I cannot find a way to install it. I thought the developers would fix it, but that hadn't been the case, maybe something is missing in my end. Currently, when I want to install gst-bad it gives the following error:
```
*gstreamer0*.*10*-*plugins*-*bad*: *Depends*:  *libdirac*-*encoder0 but it is not going to be installed*  
```If I try to force install libdirac-encoder0, it tries to remove gstreamer plugins ffmpeg and vlc among other things. I tried searching for a bug but [bug 509442]("https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/509442") is marked as solved.
Any help?

---

### Post by ankspo71 on 2010-02-13
Hi,
Synaptic says I have gstreamer0.10-plugins-bad-multiverse installed. I didn't install them directly, so they must have come with ubuntu-restricted-extras or another program that  needed them. This is a fresh Lucid install (not upgraded from karmic). libdirac-encoder0 is installed on my end too.
Are all of your repositories enabled? 
Hope this helps.

---

### Post by Starks on 2010-02-13
This problem was resolved weeks ago, what mirror are you using?

---

### Post by mc4man on 2010-02-13
I would just go ahead and remove libdirac0c2a and install the new dirac libs - libdirac-encoder0, libdirac-decoder0 - you'll have to at some point anyway.
(best done by searching dirac in synaptic, ect.

Anything that's removed can be re-installed, for the most part very little depends on them anyway.

I have my own vlc 1.0.5 package set but the lucid repo 1.0.4 doesn't depend on dirac libs.

If you have anything that does depend on libdirac0c2a then it probably isn't a lucid package and should be re-built off of the new lucid libdirac-dev (1.0.2-2

---

### Post by seeker5528 on 2010-02-13
If you have packages that are listed as locally installed/obsolete, I would get rid of some of those first.

Also check which libavcodec package is installed, mine is currently showing libavcodec-extra-52 when I use apt-rdepends with the following command line:

```
apt-rdepends -r --state-follow=Installed -s Depends,Recommends,PreDepends libdirac-encoder0
```

But in spite of that doing

```
dpkg -l *codec*
```

Shows libavcodec-extra-52 not installed, but libavcodec52 is. Now I have installed libavcodec-extra-52 as well.

If you don't have one of the restricted extras packages installed you might try that too, it may kick something loose something like.

```
sudo apt-get install --reinstall libavcodec-extra-52 libavcodec52 libdirac-encoder0 ubuntu-restricted-extras gstreamer0.10-ffmpeg
```

Might do it.

Later, Seeker

---

### Post by shafin on 2010-02-13
Thanks for the help. 
I was using the main mirror, but as I did not install libencoder0, the problem persisted for a long time.
Funny thing is, vlc had to be uninstalled along with libdirac0c2, but then it reinstalled just fine without it.

---

