---
title: "Additional plugins are required to display all the media on this page - Firefox flash"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2010-03-20
Liveusb of beta1

So I go to a website that has flash advertisements or flash video, and I get this message in firefox "Additional plugins are required to display all the media on this page"

Ok this is normal since I don't have flash installed.

I click "install missing plugins..." button.
It searches for a couple seconds, and then "Press Next to install these plugins". There are none listed, so I click on next. "No suitable plugins were found". Click finish.

Shouldn't firefox know it is flash and ask to install adobe or gnash etc? It did this with previous ubuntu. This must be a new bug.

If I go to youtube, website points a link to adobe download.

Also first time I open firefox it is not maximized all the way down vertically (not touching bottom panel, can see wallpaper). This should be fixed.

Let me know if you have similar problems and whether bugreport is out.

---

### Post by mc4man on 2010-03-20
Probably related to this (or the dups
[https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/520166](https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/520166)

---

### Post by kansasnoob on 2010-03-20
I always just go to Software Sources and make sure that I have Main, Universe, Restricted, Multiverse, and Partner repos all checked, then click on Reload when prompted.

Next just install "ubuntu-restricted-extras", either from Synaptic or from terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

If you plan on running the Live CD off and on for some time you might be interested in "persistence":

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

I actually just create a 1GB partition on my hard drive for the "casper-rw" file system instead of using a USB stick.

---

### Post by andrewabc on 2010-03-20
> **kansasnoob said:**
> I always just go to Software Sources and make sure that I have Main, Universe, Restricted, Multiverse, and Partner repos all checked, then click on Reload when prompted.

Next just install "ubuntu-restricted-extras", either from Synaptic or from terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

If you plan on running the Live CD off and on for some time you might be interested in "persistence":

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

I actually just create a 1GB partition on my hard drive for the "casper-rw" file system instead of using a USB stick.

ubuntu resricted extras installs adobe flash?

I once installed ubuntu to liveusb which was a mistake as it screwed up grub.

I've done the startup disk creator "store in reserved extra space" option.
I'm just testing  for now to see what works and doesn't work on my hardware.

thanks mc4man for the link. I "affect me too" it.

---

### Post by andrewabc on 2010-04-27
This still hasn't been fixed yet for me even though bug report says fixed. Running liveusb 10.04 RC

Go to youtube, try to watch video, asks for plugin, no plugin found.
People are expected to go into synaptic or ubuntu software center to install flash?

It is fixed if I do what bug report discussion at end says to change 10.04 to 9.10. Why hasn't this been fixed yet? Are they waiting for release day to turn something on?
When it asks to enabled other repositories I say no (don't want to do that yet) and firefox then says flash installed successfully even though it never installed because I didn't enabled repository.

---

