---
title: "opera &amp; Flash !#$$"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by USNSubguy on 2007-12-08
Hello I'm on my 3rd day using Ubuntu,  been using windows  sence 3.11,   i'm very impressed  but i didn't like firefox, it was not very compatible with alot of my normal sites,  i switched to opera but i cant get flash to install,  any ideas?:confused:

---

### Post by PmDematagoda on 2007-12-08
Maybe [this]("http://www.opera.com/linux/docs/plugins/install/") page could help you.

---

### Post by USNSubguy on 2007-12-08
Thanks for the reply,  that aloud me to install using the term program and it said it installed just fine,  i can now go into opera's plugins and see it, its click to be active but its still not working? any thoughts?   although i'm new to ubuntu i'm not afraid to try new things so throw it at me.  if you know a web browser that works or how to optimize FireFox so that it works (frames in the right spot, buttons click like there supost to) , basicly i'm up for any sugestions.

---

### Post by monte48lowes on 2007-12-08
I use opera almost exclusively. What are the paths you have for plugins?

Mike

---

### Post by USNSubguy on 2007-12-08
It shows   

/usr/lib/opera/plugins:/usr/lib/flashplugin-nonfree:/usr/lib/mozilla

for my flash.

---

### Post by ericartman on 2007-12-08
Never used opera but for firefox I always just go to synaptic and install flash non free and it works.

or try uBackup! a script that installs codecs and fixes flash and does backups. Just do a forum search for that. not sure if it works on Opera though.

Cart

---

### Post by monte48lowes on 2007-12-08
add /usr/lib/firefox/plugins

For some reason mine shows 'plugins' and the end of both the firefox directories and mozilla. Try adding the one above, and see if that works.

Mike

---

### Post by USNSubguy on 2007-12-08
nope still not working,   is there anyway to "uninstall all my web brousers and plugins then reinstall"

---

### Post by daradib on 2007-12-08
FYI:

There is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This affects anything using the flashplugin-nonfree package including Firefox and presumably Opera.

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree. For more information on how to do this, see the Ubuntu documentation here: [https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic](https://help.ubuntu.com/7.10/add-applications/C/advanced.html#synaptic)

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by Dynaflow on 2007-12-08
I'm an Opera user, and I can confirm that the above solution isn't working for that browser (thank goodness I was installing Ubuntu on a *secondary*, work-related machine when this thing hit -- my main, personal Ubuntu computer will, in theory, continue to display Flash in Opera as long as I don't do anything stupid like update it to the latest, greatest version of Flash).  The Flash-nonfree plugin never worked well in the Linux version of my Norweigan browser of choice, but at least the previous editon could usually play things right if you didn't confuse it by switching tabs or anything crazy like that.  Now it doesn't work at all.  

Due to the proprietary version of Flash's ubiquity on the web (Thanks, Macromedia/Adobe Marketing!), I'm moving "back" to Firefox on this newly-Ubuntu'ized laptop until Adobe's Linux <s>department</s> guy gets the compatibility issues straight.  At least I got the load-cycle-count thing sorted out... [grumble]

---

### Post by daradib on 2007-12-08
Oh, well that's a pity. I am not very happy with Adobe Flash. I really hope Gnash improves to a fully usable state where it can compete with Adobe Flash player/plugin.

---

### Post by Colonel Kilkenny on 2007-12-08
I haven't actually tried Flash with Opera 9.24 but when Adobe said that newest flash works with Opera as well they meant that it works with Opera 9.50. 

Not sure what the situation is with stable Opera release (9.24). The older flashplugins were working OK though.

---

### Post by Dynaflow on 2007-12-08
> **Colonel Kilkenny said:**
> I haven't actually tried Flash with Opera 9.24 but when Adobe said that newest flash works with Opera as well they meant that it works with Opera 9.50. 

Not sure what the situation is with stable Opera release (9.24). The older flashplugins were working OK though.

Oh, goody.  So what Adobe meant was that it *will* work with Opera one day, once Kestrel is final.  According to [the Opera Desktop Team Blog]("http://http://my.opera.com/desktopteam/blog/"), they got the release candidate of the Flash plugin to work on the latest daily build of their not-yet-released new version by essentially tricking Flash into thinking it was Firefox.  That may be the source Adobe's "works in Opera" claim.  The Opera folks offer the caveats that the browser crashes when Java is initialized, and it also "might crash if you close a tab while flash is being initialized."

If anyone feels like climbing onto that bucking horse to see if it might be amenable to taming, you can find links to the latest release candidates at [http://my.opera.com/desktopteam/blog/]("http://my.opera.com/desktopteam/blog/").  You would be strongly advised to install this separately from your current, stable installation of Opera 9.24 from the repositories, unflashworthy though it may be.

---

### Post by Dynaflow on 2007-12-08
False alarm.  I tried it and got nothing.  I guess we'll just have to wait for the next beta release.

---

### Post by meborc on 2007-12-09
> **Dynaflow said:**
> False alarm.  I tried it and got nothing.  I guess we'll just have to wait for the next beta release.

i am as frustrated as you are... a long time opera user... did a stupid thing :) tried to update flash... it kept not working from time to time (like in youtube, i needed to refres sometimes to get it to load the videa properly)... well... no flash anymore... and firefox is freezing... i get like 1-2 FPS with youtube, that sucks...

i'll look into kazehakase again :)

---

### Post by daradib on 2007-12-10
See [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669) for more information. I am not sure, but Opera may be related to the same problem as Konqueror has.

---

### Post by psycho_NIX on 2007-12-11
if you install preupdated version (v 9.0) of libflashplayer.so flash willwork again.

---

### Post by daradib on 2007-12-11
> **Dynaflow said:**
> Oh, goody.  So what Adobe meant was that it *will* work with Opera one day, once Kestrel is final.  According to [the Opera Desktop Team Blog]("http://http://my.opera.com/desktopteam/blog/"), they got the release candidate of the Flash plugin to work on the latest daily build of their not-yet-released new version by essentially tricking Flash into thinking it was Firefox.  That may be the source Adobe's "works in Opera" claim.  The Opera folks offer the caveats that the browser crashes when Java is initialized, and it also "might crash if you close a tab while flash is being initialized."

If anyone feels like climbing onto that bucking horse to see if it might be amenable to taming, you can find links to the latest release candidates at [http://my.opera.com/desktopteam/blog/]("http://my.opera.com/desktopteam/blog/").  You would be strongly advised to install this separately from your current, stable installation of Opera 9.24 from the repositories, unflashworthy though it may be.

See this [bug comment]("https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890/comments/32"):
> 
btw. updating to version 9.0.115 of flash will also affect the package opera. The 9.50 Beta 2 of Opera can handle this.

---

### Post by daradib on 2007-12-11
> **psycho_NIX said:**
> if you install preupdated version (v 9.0) of libflashplayer.so flash willwork again.

Well in that case, here is an [archive of Flash 9 releases]("http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip") (over 65 MB in size), including installers for all supported platforms.

---

