---
title: "flash stopped working after updating using update manager"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by pieman711 on 2009-12-10
I'm running ubuntu 8.10 and after installing the latest update in the update manager (for flash) the videos on the BBC website no longer run. 
I still get the picture loading up correctly in the box but instead of a play toolbar it just has the message "cannot play media. you do not have the correct version of Flash player"

---

### Post by vificunero on 2009-12-10
I had problems with bbc video too. I just restarted firefox. Now it works.

---

### Post by Yvan300 on 2009-12-10
You could try reinstalling the flash player, may or may not work.

---

### Post by doas777 on 2009-12-10
my kids were complaining that the faceboot games stopped working last night. haven't gotten a chance to dig into it, but my first guess is a flash update.

---

### Post by networkspeedy on 2009-12-10
Yes, after the latest update from update manager this morning (which included an update to adobe flash) I am unable to see any flash movies whatsoever.  No flash for me either.  I don't know how to rectify it.  I'm going to try using a different plugin to play swf movies, but barring that, all I have to say is that I'm glad I rsync backup my entire system nightly...

I'd love to see a solution for this though, if anyone knows how/what to do for a fix.

---

### Post by suniyo on 2009-12-10
> **networkspeedy said:**
> Yes, after the latest update from update manager this morning (which included an update to adobe flash) I am unable to see any flash movies whatsoever.  No flash for me either.  I don't know how to rectify it.  I'm going to try using a different plugin to play swf movies, but barring that, all I have to say is that I'm glad I rsync backup my entire system nightly...

I'd love to see a solution for this though, if anyone knows how/what to do for a fix.


It happened to me too, problem is may be with this file that update manager needed to download for upgrade and which is not available: [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.42.34.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.42.34.orig.tar.gz)

Need to inform some moderator about this as dpkg hangs and crashes due to the problem that the file can not be downloaded.

---

### Post by Jordao on 2009-12-10
It happened to me too.

I just downgrade to the previous version in Synaptic.

It works fine now.

---

### Post by Janeleaper on 2009-12-10
I had this problem a few months ago.  In my case it was because I had two versions of Flash installed (nos 5 and 6 as I recall). Check using Synaptic Manager and uninstall the earlier version if necessary.

---

### Post by markbuntu on 2009-12-10
I had that problem with my hardy install when I got the last flash update. I fixed it with

sudo apt-get install libflashsupport

Took a little while to figure that out. 

Shockwave Flash 9.0 r246

---

### Post by noondaysun on 2009-12-10
Same here.

It was working.  Updated.  Now its not. <sigh>

---

### Post by safarj on 2009-12-11
hello, flashplayer fixed in ubuntu 9.10 via running:
[FONT="Courier New"]sudo aptitude reinstall flashplugin-installer[/FONT]

---

### Post by Orbegoso on 2009-12-11
> **safarj said:**
> hello, flashplayer fixed in ubuntu 9.10 via running:
[FONT=Courier New]sudo aptitude reinstall flashplugin-installer[/FONT]

That worked for me.

---

### Post by pieman711 on 2010-01-06
If anyone is still having a problem with this I fixed it in 8.10 just by going on the add/remove programs and installing it. Apparently the update somehow deleted it from my computer.

---

