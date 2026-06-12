---
title: "Sluggish Firefox on pages with flash content"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by crjackson on 2009-09-24
I've never really had any performance issues with Firefox on flash filled pages, but now it's painfully obvious.  Scrolling is slow and choppy.

Anyone else noticing increased sluggishness?

---

### Post by dummy910 on 2009-09-24
All my research on this subject, clearly indicates that the problem lies within Flash itself(a memory leaker), and not Firefox per se.

Check out the following site and follow the directions verbatim, and watch Firefox sail like the wind.
**[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)**

---

### Post by tuxxy on 2009-09-24
Are you running 64-bit ubuntu? if so did you install the 64-bit Flash plugin as what you describes sounds like the performance you get when using the 32-bit flashplugin-nonfree in the repos.

---

### Post by foremannz on 2009-09-24
I also found this, and did it to myself when I tried to get a facebook application working with flash - turned out I installed multiple flash players, and it wasn't running adobe as the default.
Fixed by removing all the flash players then visiting a flash based site and choosing adobe from the list of apps firefox wants to install (2nd in the list I think).  You can also install it by locating adobe non free or something to that affect.

---

### Post by cororok on 2009-09-24
Me too. because my laptop is a netbook.
scrolling on a webpage containing flashs is really terrible.


BUT
Try google chrome. it's really fast.

as I know firefox is not a simple browser but also contains large something which enables XUL rendering something so it is very slow.

anyway... try google chrome.

---

### Post by crjackson on 2009-09-25
> **tuxxy said:**
> Are you running 64-bit ubuntu? if so did you install the 64-bit Flash plugin as what you describes sounds like the performance you get when using the 32-bit flashplugin-nonfree in the repos.

32 bit

---

### Post by crjackson on 2009-09-25
> **foremannz said:**
> I also found this, and did it to myself when I tried to get a facebook application working with flash - turned out I installed multiple flash players, and it wasn't running adobe as the default.
Fixed by removing all the flash players then visiting a flash based site and choosing adobe from the list of apps firefox wants to install (2nd in the list I think).  You can also install it by locating adobe non free or something to that affect.

Looking into this now....

---

### Post by crjackson on 2009-09-25
> **foremannz said:**
> I also found this, and did it to myself when I tried to get a facebook application working with flash - turned out I installed multiple flash players, and it wasn't running adobe as the default.
Fixed by removing all the flash players then visiting a flash based site and choosing adobe from the list of apps firefox wants to install (2nd in the list I think).  You can also install it by locating adobe non free or something to that affect.

Using synaptic, I've located everything that shows up in the flash search.  I removed ubuntu-restricted-extras and Adobe Flash Plugin.

Nothing else shows.  I told it to remove the configuration files too.

Here's the funny part.  Nothing flash is showing as installed, but I can still watch flash videos and view flash content.

How do I get rid of it?

---

### Post by crjackson on 2009-09-25
Okay I'm getting frustrated with this.  Any other ideas.

---

### Post by kansasnoob on 2009-09-25
> **crjackson said:**
> Using synaptic, I've located everything that shows up in the flash search.  I removed ubuntu-restricted-extras and Adobe Flash Plugin.

Nothing else shows.  I told it to remove the configuration files too.

Here's the funny part.  Nothing flash is showing as installed, but I can still watch flash videos and view flash content.

How do I get rid of it?

Those two packages should be installed. Remember you must restart Firefox each time you change anything plug-in related.

I've had to install Flashblock to achieve an acceptable level of performance in Firefox:

[https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)

---

### Post by crjackson on 2009-09-25
> **kansasnoob said:**
> Those two packages should be installed. Remember you must restart Firefox each time you change anything plug-in related.

I've had to install Flashblock to achieve an acceptable level of performance in Firefox:

[https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)

Not only did I restart firefox, I restarted the system.  I'm watching flash videos with no flash software installed that I can detect.  How is that possible?

Also, I've never had to use flashblock before... that sucks.

---

### Post by crjackson on 2009-09-25
Man this sucks.  I'm tempted to reinstall but the release is just around the corner.  How can flash be working with no trace installed that I can find?

---

### Post by Longinus00 on 2009-09-25
> **crjackson said:**
> Man this sucks.  I'm tempted to reinstall but the release is just around the corner.  How can flash be working with no trace installed that I can find?

Obviously it is installed.

What's in .mozilla/plugins?

---

### Post by foremannz on 2009-09-26
Have a check for SWF in Synaptic - you might still have swfdec installed

---

### Post by LADmaticCA on 2009-09-26
You could try:

```
locate -i libflashplayer.so
```

That should give you an idea where the plug-in is hiding.

---

### Post by deathsshadow77 on 2009-09-26
check your /home/username/.mozilla/plugins folder
its probably in there

---

### Post by crjackson on 2009-09-27
> **LADmaticCA said:**
> You could try:

```
locate -i libflashplayer.so
```

That should give you an idea where the plug-in is hiding.
nothing found.

---

### Post by crjackson on 2009-09-27
> **deathsshadow77 said:**
> check your /home/username/.mozilla/plugins folder
its probably in there

not there

---

### Post by crjackson on 2009-09-27
> **foremannz said:**
> Have a check for SWF in Synaptic - you might still have swfdec installed

not that either.

---

### Post by crjackson on 2009-09-27
> **Longinus00 said:**
> Obviously it is installed.

What's in .mozilla/plugins?

There is no plugins sub-folder

---

### Post by psyke83 on 2009-09-27
Reinstall just to clear a browser plugin, are you kidding? This is a simple problem, but nobody has given concise enough instructions in one go.

Purge all packages relating to Flash:
```
$ sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree flashplugin-installer adobe-flashplugin
```

Check for any remaining Flash libraries:
```
$ sudo updatedb
$ locate libflashplayer | grep so
```

Delete all libraries that are listed from the above locate command.

Restart Firefox, and then verify that all Flash plugins are now removed by checking in Firefox:
```
about:plugins
```

If for some bizarre reason Flash is still showing in this list, make a note of its file name on the above page, and then do another locate of the name listed and delete it.

Once you have verified that Flash is gone, re-install the flashplugin-installer package, and in future, don't install plugins manually.

---

### Post by inportb on 2009-09-27
> **kansasnoob said:**
> [https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)

Oh hellz yeah, Flashblock is teh shiz.

---

### Post by crjackson on 2009-09-27
> **psyke83 said:**
> Reinstall just to clear a browser plugin, are you kidding? This is a simple problem, but nobody has given concise enough instructions in one go.

Purge all packages relating to Flash:
```
$ sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree flashplugin-installer adobe-flashplugin
```

Check for any remaining Flash libraries:
```
$ sudo updatedb
$ locate libflashplayer | grep so
```

Delete all libraries that are listed from the above locate command.

Restart Firefox, and then verify that all Flash plugins are now removed by checking in Firefox:
```
about:plugins
```

If for some bizarre reason Flash is still showing in this list, make a note of its file name on the above page, and then do another locate of the name listed and delete it.

Once you have verified that Flash is gone, re-install the flashplugin-installer package, and in future, don't install plugins manually.

Thanks psyke83.  That killed it. Now, what is the best method to PROPERLY install?

---

### Post by psyke83 on 2009-09-27
> **crjackson said:**
> Thanks psyke83.  That killed it. Now, what is the best method to PROPERLY install?

You said you're using the 32bit release, right?

As far as I know, installing the flashplugin-installer package is the recommended method. This will ensure that updates occur properly, and of course will make it easier to remove the plugin in future, if necessary.

Let us know if you're still experiencing sluggishness with the official Adobe plugin. I recall one of the developers replying to a recent thread about a conflict between the i915 and agpgart kernel module; if they are loaded in the incorrect order your graphics performance will be extremely sluggish. I think [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694") is the bug, or something similar.

---

### Post by crjackson on 2009-09-27
> **psyke83 said:**
> You said you're using the 32bit release, right?

As far as I know, installing the flashplugin-installer package is the recommended method. This will ensure that updates occur properly, and of course will make it easier to remove the plugin in future, if necessary.

Let us know if you're still experiencing sluggishness with the official Adobe plugin. I recall one of the developers replying to a recent thread about a conflict between the i915 and agpgart kernel module; if they are loaded in the incorrect order your graphics performance will be extremely sluggish. I think [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/430694") is the bug, or something similar.

Funny thing is that synaptic shows that flash isn't installed, but flash plays with JUST the plugin-installer installed.

It's very sluggish like this still...

This on on a laptop with a ATI 9600 installed. Video performance has been great except when using a flash enabled page.

---

### Post by ormandj on 2009-09-27
Hi,

I started having an issue with Flash (Hulu, for instance) being very choppy/slow since an update that I did about half a week ago. I hadn't updated in a week or two prior, so something changed in that period. I use 64-bit flash, so that isn't my issue. I do have Intel video (this occurred on two machines, both my desktop which is an X4500HD and my laptop which is an X4500MHD) so this may be my issue, I just wanted to mention it in case it was related.

---

### Post by crjackson on 2009-09-27
> **ormandj said:**
> Hi,

I started having an issue with Flash (Hulu, for instance) being very choppy/slow since an update that I did about half a week ago. I hadn't updated in a week or two prior, so something changed in that period. I use 64-bit flash, so that isn't my issue. I do have Intel video (this occurred on two machines, both my desktop which is an X4500HD and my laptop which is an X4500MHD) so this may be my issue, I just wanted to mention it in case it was related.

Well that's kind of the same thing that happened here but I'm not using an intel card.

Good to see someone else for SATX here.  I moved to NC in 2003 after retiring from SAPD.

Back on topic.  Let me know if you find a solution.

---

### Post by crjackson on 2009-09-28
Does anyone think this MIGHT get fixed before the release date?

---

### Post by ormandj on 2009-09-29
> **crjackson said:**
> Does anyone think this MIGHT get fixed before the release date?

No idea, even with flashblock I still get terrible performance. I'm giving gnash a try now, as all I really care about are basic navigation on sites that are flash only (uhg) and Hulu/youtube. Gnash seems ok with most youtube content, although some seems to not work. Hulu I haven't had a chance to try yet, but I will soon as my HTPC looks like it's playing the content at 10fps.

---

### Post by ormandj on 2009-09-29
Unfortunately, I found the only solution to workable flash playback for sites such as Hulu which don't work with Gnash or swfdec.

1) Remove all swfdec/gnash plugins
2) If you're running 64-bit Ubuntu Karmic, you need to setup this repo: [https://launchpad.net/~dinxter/+archive/test](https://launchpad.net/~dinxter/+archive/test)
3) Install the Adobe flash plugin :(
4) Goto the menu, System->Preferences->Appearance->Visual Effects. Select 'None'
5) Exit Firefox if you're using it. This may not be necessary, but doesn't hurt, either
6) Flash works properly, without the slide-show mode. No visual effects, though

Yes, it sucks. Yes, it works. I hope the new standards catch on with Youtube/Hulu, so we can get rid of this flash requirement on these two sites. Once these are available sans-flash, life in the alt-OS world will become much more enjoyable.

David

---

### Post by jeffus_il on 2009-09-29
I second this!

> **cororok said:**
> Me too. because my laptop is a netbook.
scrolling on a webpage containing flashs is really terrible.


BUT
Try google chrome. it's really fast.

as I know firefox is not a simple browser but also contains large something which enables XUL rendering something so it is very slow.

anyway... try google chrome.

---

### Post by crjackson on 2009-10-11
Well, the problem with the open-source ATI driver performance.  I tweaked it up and now everything runs fine.

---

