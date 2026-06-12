---
title: "Upgraded Kubuntu to Edgy, now Amarok can't play MP3s"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by Baka Dasai on 2006-11-03
After upgrading my Kubuntu system to Edgy, when I run Amarok I get told: "Amarok currently cannot play MP3 files."  There is a button marked "Install MP3 support", but clicking it appears to do nothing.

I am running Amarok through xine, and I have libxine-extracodecs installed.  It all worked perfectly before the upgrade to Edgy.

This thread <http://ubuntuforums.org/showthread.php?t=231721> suggests the following solution:

```
sudo apt-get remove --purge amarok amarok-xine libxine-extracodecs
sudo apt-get install --reinstall amarok amarok-xine libxine-extracodecs
deleted ~/.kde/share/apps/amarok/ folder
deleted ~/.libxine/ folder
```

but when I go to do the the purge in the first command I'm told that kubuntu-desktop will also be removed, which is a bit alarming:

```
sudo apt-get remove --purge amarok-xine libxine-extracodecs
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xserver-xorg linux-headers-generic libxine-extracodecs hwdb-client-kde kde-icons-mono kubuntu-desktop kbstate
  python-qt4 amarok-xine amarok xorg linux-headers-2.6.17-10 python-elementtree kde-guidance-powermanager
  kmousetool kmag bluez-pin linux-headers-2.6.17-10-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  amarok* amarok-xine* kubuntu-desktop* libxine-extracodecs*
0 upgraded, 0 newly installed, 4 to remove and 31 not upgraded.
```

What should I do?

---

### Post by Baka Dasai on 2006-11-05
I tried the solution written above, and it didn't work.

The relevant version numbers:

Amarok: 1.4.3
Amarok-xine: 1.4.3
libxine-extracodecs: 1.1.2
libmad0: 0.15.1b

Also, MP3s and OGGs play OK in mplayer, but not in xine, kaffeine or amarok.  I assume that libxine-extracodecs isn't working for some reason, but what can I do?

---

### Post by chikebum on 2006-11-05
try install gstreamer plugins + Xmms :

gstreamer0.10-ffmpeg 
gstreamer0.10-gl 
gstreamer0.10-plugins-base 
gstreamer0.10-plugins-good 
gstreamer0.10-plugins-bad 
gstreamer0.10-plugins-bad-multiverse 
gstreamer0.10-plugins-ugly 
gstreamer0.10-plugins-ugly-multiverse


sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse xmms

---

### Post by Baka Dasai on 2006-11-06
I guess you're suggesting I use gstreamer instead of xine as the backend for amarok.  I might end up trying this, but I'd really like to get xine/amarok working properly as it's always worked well in the past, and I'd like to be able to play mp3-encoded movies in xine.

I'm a little frustrated at this problem as I can't see how to go about troubleshooting it, and nobody else seems to know either.

---

### Post by david.bal on 2006-11-09
Unfortunately i go the same exact problem. would be glad for a solution.

---

### Post by davidjh on 2006-11-16
So, when I upgraded from dapper to edgy I think my apt-sources got messed up.  In particular I believe that I had multiverse enabled and it became disabled.

Either that or I only had multiverse on backports for dapper, which *did* include libxine-extracodecs, but the same is not true for edgy-backports.


In any event, I had the same problem, here's how I resolved it.

1) rm -fr ~/.xine    # i don't think this actually matters, but it might have
2) rm -fr ~/.kde/share/apps/amarok
3) sudo vim /etc/apt/sources.list
  ensure that I have this line
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe multiverse
4) sudo apt-get --purge remove libxine-extracodecs
5) sudo apt-get install --reinstall libxine-extracodecs

I suspect that only steps 3 & 5 are actually necessary, but who knows.  Anyway, hope this helps someone.

---

### Post by eradan on 2006-11-18
it works! :KS 
Thank you!

---

### Post by Baka Dasai on 2006-12-09
Problem fixed for me - I renamed my .xine folder and all is well.

---

### Post by Etaoin on 2007-01-04
Just found this thread, while Googling for solutions to the same problem.  Worked perfectly.  Many thanks, davidjh.

---

### Post by Pobega on 2007-01-04
For future references, don't worry about *Ubuntu-Desktop packages. As far as I'm concerned they're *all* meta-packages, which means that they're only purpose is to give you quick downloads to their dependancies. Usually you won't lose much/anything by removing them.

---

### Post by goathunter on 2007-02-11
> **davidjh said:**
> So, when I upgraded from dapper to edgy I think my apt-sources got messed up.  In particular I believe that I had multiverse enabled and it became disabled.

Either that or I only had multiverse on backports for dapper, which *did* include libxine-extracodecs, but the same is not true for edgy-backports.


In any event, I had the same problem, here's how I resolved it.

1) rm -fr ~/.xine    # i don't think this actually matters, but it might have
2) rm -fr ~/.kde/share/apps/amarok
3) sudo vim /etc/apt/sources.list
  ensure that I have this line
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe multiverse
4) sudo apt-get --purge remove libxine-extracodecs
5) sudo apt-get install --reinstall libxine-extracodecs

I suspect that only steps 3 & 5 are actually necessary, but who knows.  Anyway, hope this helps someone.

I had the same problem as well. Solved it for me, thanks!

---

### Post by thobbs on 2007-02-13
Worked for me too - THANKS A LOT!!! I was about to give up until I saw this...

---

### Post by Tyler Oderkirk on 2007-04-01
> **davidjh said:**
> 
1) rm -fr ~/.xine    # i don't think this actually matters, but it might have


Thanks David, removing my ~/.xine folder (which only contained "catalog.cache") did the trick for me.

I had been getting messages like "amarok currently cannot play mp3 files" and "some media could not be loaded (not playable)"

For the curious, I attached the differences between the old, broken, catalog.cache and the working one that was created automatically after I deleted the old one. I'm guessing some other app I ran ruined my old version by removing the demuxers for cdda, wav, mp3, etc?

Now I can get back to the brand new 3/18/07 Groove Armada Essential Mix that I grabbed from [The Mixing Bowl]("http://themixingbowl.org/"). PM me for an invite if you like.

---

