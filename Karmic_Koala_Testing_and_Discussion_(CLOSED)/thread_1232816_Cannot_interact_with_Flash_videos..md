---
title: "Cannot interact with Flash videos."
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Aries K on 2009-08-05
When I'm watching a video in Flash I cannot interact with it in anyway whatsoever. Is anyone else have this problem? Thanks in advance.

---

### Post by Sub101 on 2009-08-06
I am having the same issue. I can sometimes tab through the selection options but can not normally with the mouse.

Are you 64 bit?

---

### Post by Leighman on 2009-08-06
Having the same problem here, using Opera, if that's a common denominator

---

### Post by Aries K on 2009-08-06
Yep I am 64bit.

---

### Post by Davikar on 2009-08-06
I think I might have a related problem, some flash applications on facebook are behaving very oddly. Like the aim is very off. Like a click in the middle ends upp in the left upper corner of the window.
I'm also on 64bit, same problem with both Opera and Firefox 3.0 and 3.5.

---

### Post by taavikko on 2009-08-06
You guys, might help if you'd tell what version of flash you're using ;)

---

### Post by Sub101 on 2009-08-06
The adobe website identifies as: 10,0,22,87

Which is the version marked in synaptic.

---

### Post by Davikar on 2009-08-06
Well, the latest available from the repository (10.0.22.87). But the newest on the flash website isn't available there yet (and they don't serve 64bit versions from the flash site).

---

### Post by taavikko on 2009-08-06
Do someone has any site at hand that doesn't require registration to view, where this "interaction" fails?

Does this tag-cloud work?
example: [http://www.roytanck.com/2008/03/06/wordpress-plugin-wp-cumulus-flash-based-tag-cloud/](http://www.roytanck.com/2008/03/06/wordpress-plugin-wp-cumulus-flash-based-tag-cloud/)

---

### Post by jfernyhough on 2009-08-06
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

64-bit native Flash plugin. Works perfectly.

---

### Post by Davikar on 2009-08-06
Well, just tried the plugin you linked to. Still doesn't work right when playing flash based games on Facebook, like FarmVille and Restaurant City. That tag cloud works fine though.

---

### Post by scradock on 2009-08-06
> **taavikko said:**
> Do someone has any site at hand that doesn't require registration to view, where this "interaction" fails?

Does this tag-cloud work?
example: [http://www.roytanck.com/2008/03/06/wordpress-plugin-wp-cumulus-flash-based-tag-cloud/](http://www.roytanck.com/2008/03/06/wordpress-plugin-wp-cumulus-flash-based-tag-cloud/)
I'm getting a new (karmic only, after recent updates) failure at [www.latimes.com/sudoku](www.latimes.com/sudoku)

The flash sudoku screen loads, but no interactions are acted on.....

No registration needed..

---

### Post by Sub101 on 2009-08-06
After some investigation Ive found that it works on some sites, and not others. So could this be a problem with the sites not being coded properly for Flash 10?

---

### Post by Davikar on 2009-08-06
Well, the sites that don't work well for me works perfectly when I'm on Windows with both Opera 10, FF and the latest flash...

---

### Post by caeroe on 2009-08-06
> **Aries K said:**
> When I'm watching a video in Flash I cannot interact with it in anyway whatsoever. Is anyone else have this problem? Thanks in advance.

I had that issue, but when I disabled visual effects I could once again interact.  I'm using Jaunty and Karmic x64 myself now, with the Flash version supplied through Synaptic.

(Oddly sometimes I could get functions to work, with Youtube but not Hulu.)

The x64 plugin from Adobe didn't have any such issue with any visual effects enabled.  However the the plugin's performance was horrid.  Fullscreen was extremely choppy.

This was in Firefox 3.0.12 and 3.5.2.  In Opera I have never had Flash working properly.  I have audio, but where the video is just an empty space.

Edit:  Fixed Opera's flash, somewhat.  I'm having Opera use the Adobe Flash x64 plugin directly copied to the /usr/lib/opera/plugins directory.  Where as Firefox is using Flash through Synaptic.  However the x64 plug-in is still horrible in fullscreen, so I'm still using Firefox for any flash video.  In short, nothing changed in regards to what browser I have to use.

---

### Post by Aries K on 2009-08-07
Whoops sorry for the late response my instant email notification didn't inform me of the extra replies to the thread. I am using the latest (10.0.22.87) Flash from the repos. The tag cloud thing works for me but YouTube and most random sites that used Flash-based players I cannot interact with. IE: Hitting the pause/play button etc.

---

### Post by tghe-retford on 2009-08-08
I am noticing intermittent problems with numerous video websites, including YouTube, where none of the buttons or interactive elements will work. I have to restart Firefox to gain control.

More importantly, I am not using Flash from the repos, I am using the 64-bit native Flash plugin direct from Adobe which jfernyhough posted a link to.

---

### Post by taavikko on 2009-08-08
I'm using the adobes alpha 64-bit plugin, and have no problems interacting with flash.
though not using firefox, arora took the prize. though firefox seems to work without a glitch also...

Wonder if this is a issue with nspluginwrapper and firefox?
since most of the replies seems to be from users of 64-bit systems.

---

### Post by psyke83 on 2009-08-08
Folks,

If this is only affecting 64-bit users, it seems likely to be a problem with nspluginwrapper.

---

### Post by tghe-retford on 2009-08-08
> **taavikko said:**
> Wonder if this is a issue with nspluginwrapper and firefox?
since most of the replies seems to be from users of 64-bit systems.
Can't deny it appears to be a 64-bit issue, but it doesn't solve why I am having the same problem without nspluginwrapper or flashplugin-installer installed, but rather with the native 64-bit Flash plugin from Adobe:
```
sonic@TGHE:~$ dpkg-query -W "flashplugin-installer"
No packages found matching flashplugin-installer.
sonic@TGHE:~$ dpkg-query -W "nspluginwrapper"
No packages found matching nspluginwrapper.
sonic@TGHE:~$ dpkg-query -W "firefox-3.5"
firefox-3.5     3.5.2+nobinonly-0ubuntu1

```

---

### Post by Arup on 2009-08-08
Alpha x64 plugin doesn't need or use nsplugin, the interactivity features like mic and video support were left out by Adobe according to their initial release notes, they might have added these features later.

---

### Post by taavikko on 2009-08-08
> **Arup said:**
> Alpha x64 plugin doesn't need or use nsplugin, the interactivity features like mic and video support were left out by Adobe according to their initial release notes, they might have added these features later.

True. but someone who install the flashplugin-installer via repos on x86_64 system, it pulls nspluginwrapper right beside the 32-bit flash, cause it wont work in normal 64-bit system, and the native 64-bit flash isn't available through the repos.

folks are experiencing problems with play/pause and such on flashplayer, not solely meaning the right-click options menu.

EDIT//lousy explanation, but hopefully somebody got the point :)

---

### Post by scradock on 2009-08-08
> **taavikko said:**
> True. but someone who install the flashplugin-installer via repos on x86_64 system, it pulls nspluginwrapper right beside the 32-bit flash, cause it wont work in normal 64-bit system, and the native 64-bit flash isn't available through the repos.

folks are experiencing problems with play/pause and such on flashplayer, not solely meaning the right-click options menu.

EDIT//lousy explanation, but hopefully somebody got the point :)
I've tried the 64-bit version from the repos, which brings in nspluginwrapper if it isn't already installed, and also the "latest" Adobe 64-bit libflashplugin.so; both show the same problem (SOME Flash pages don't react to button clicks, etc). This "happened" a few days ago; it doesn't affect Jaunty or Karmic32 installs on the same machine, and has survived at least one Firefox upgrade, as well as removal and reinstallation of the Flash plugin (Two or three times).

Other Flash pages (msnbc news videos, for instance) work fine, including stop/start buttons.

---

### Post by -=hazard=- on 2009-08-08
I got the problem of flash too but only for Opera. No video/No audio. Googling so much and cant resolve the problem, but on firefox 3.x flash works fine.

32 bit version.

---

### Post by miegiel on 2009-08-10
> **scradock said:**
> I've tried the 64-bit version from the repos, which brings in nspluginwrapper if it isn't already installed, and also the "latest" Adobe 64-bit libflashplugin.so; both show the same problem (SOME Flash pages don't react to button clicks, etc). This "happened" a few days ago; it doesn't affect Jaunty or Karmic32 installs on the same machine, and has survived at least one Firefox upgrade, as well as removal and reinstallation of the Flash plugin (Two or three times).

Other Flash pages (msnbc news videos, for instance) work fine, including stop/start buttons.

The 64bit flashplayer is not in the repos, that must have been the 32bit flashplayer.

Check [_this thread_]("http://ubuntuforums.org/showthread.php?t=772490") for more info. In [_post 775_]("http://ubuntuforums.org/showpost.php?p=7717588&postcount=775") is a script to remove the 32bit and install the 64bit flashplayer.

---

### Post by miegiel on 2009-08-10
> **-=hazard=- said:**
> I got the problem of flash too but only for Opera. No video/No audio. Googling so much and cant resolve the problem, but on firefox 3.x flash works fine.

32 bit version.

I don't have opera atm, but you probably need to link to *libflashplayer.so* from opera's plugin/flash directory or copy it there.

---

### Post by scradock on 2009-08-11
> **miegiel said:**
> The 64bit flashplayer is not in the repos, that must have been the 32bit flashplayer.

Check [_this thread_]("http://ubuntuforums.org/showthread.php?t=772490") for more info. In [_post 775_]("http://ubuntuforums.org/showpost.php?p=7717588&postcount=775") is a script to remove the 32bit and install the 64bit flashplayer.
That sounds reasonable - but then why does the libflashplayer.so delivered by  flashplayer-installer (repo) have EXACTLY the same byte size as the one I get from Adobe - the 64-bit one? And why, if the Adobe version is supposed not to need nspluginwrapper, does it fail to work at all if nspluginwrapper is removed? And why does Firefox crash with the "native Adobe 64-bit version" even if nspluginwrapper is installed?

The only version that works at all for me is the version from the repos; in 32-bit Karmic it works as it always has done; in 64-bit Karmic something stopped it responding to button clicks, and that behavior has survived the upgrade from FF3.0 to FF3.5, the new improved nspluginwrapper, and many alternations of trying the experimental version from adobe and then the Ubuntu version from the repos.

Right-clicking on the "window" brings up a menu with "Play" as one option, but choosing that gives me a blank page with "Failure Message" on it. Choosing "Rewind" reloads the same page - see [http://www.latimes.com/sudoku](http://www.latimes.com/sudoku)....

Any ideas for places to look for error messages?

---

### Post by wayne_cat on 2009-08-11
you can check the version with "file" ... this is my 32 bit flash plugin

```
root@macbook:~# file /usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so: **[COLOR=Red]ELF 32-bit[/COLOR]** LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
root@macbook:~# 
```and this is a 64 bit version

```
root@macbook:/home/rschmitt/Desktop# file libflashplayer.so 
libflashplayer.so: ELF 64-bit LSB shared object, **[COLOR=Red]x86-64[/COLOR]**, version 1 (SYSV), dynamically linked, stripped
root@macbook:/home/rschmitt/Desktop#
```and you can compare versions with "md5sum"

---

### Post by scradock on 2009-08-11
> **wayne_cat said:**
> you can check the version with "file" ... this is my 32 bit flash plugin

```
root@macbook:~# file /usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so: **[COLOR=Red]ELF 32-bit[/COLOR]** LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
root@macbook:~# 
```and this is a 64 bit version

```
root@macbook:/home/rschmitt/Desktop# file libflashplayer.so 
libflashplayer.so: ELF 64-bit LSB shared object, **[COLOR=Red]x86-64[/COLOR]**, version 1 (SYSV), dynamically linked, stripped
root@macbook:/home/rschmitt/Desktop#
```and you can compare versions with "md5sum"
Thanks - that helps. After removing all Flash plugins I could find and ONLY installing from the repo, I found that the 32-bit libflashplayer.so in /usr/lib/flashplugin-installer has NOW a different byte-size from the 64-bit one from Adobe. So that solves one part of the mystery. Doesn't seem to me to explain why the previous checks showed two identical files - could there be a mechanism for re-loading the file if it gets removed?????

---

### Post by Sub101 on 2009-08-12
> **miegiel said:**
> The 64bit flashplayer is not in the repos, that must have been the 32bit flashplayer.

Check [_this thread_]("http://ubuntuforums.org/showthread.php?t=772490") for more info. In [_post 775_]("http://ubuntuforums.org/showpost.php?p=7717588&postcount=775") is a script to remove the 32bit and install the 64bit flashplayer.

The script there works perfectly and has resoled my problems with flash. It is now completely responsive for me. 

One thing id add, when copying the script be sure to copy the wget url separately or you get a file not found.

---

### Post by Aries K on 2009-08-12
> **miegiel said:**
> The 64bit flashplayer is not in the repos, that must have been the 32bit flashplayer.

Check [_this thread_]("http://ubuntuforums.org/showthread.php?t=772490") for more info. In [_post 775_]("http://ubuntuforums.org/showpost.php?p=7717588&postcount=775") is a script to remove the 32bit and install the 64bit flashplayer.

Thanks, that script did the trick along with following what Sub101 mentioned about copying the script separately :guitar:.

---

### Post by giorgio130 on 2009-09-18
you should subscribe to the bug, in order to get this solved.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141494](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141494)
I've just done it! :)

---

### Post by dinxter on 2009-09-18
i'm using a flash64 bit package
[https://launchpad.net/~dinxter/+archive/test](https://launchpad.net/~dinxter/+archive/test)
if anyone finds it useful

---

### Post by !nkubus on 2009-09-18
Same here 32bit versuion with Chromium but works in FF

---

### Post by oztrailrider on 2009-09-18
I am seeing the same issue on 32 bit with Google Chrome. I think FF seems to be ok though.

---

### Post by dudude on 2009-09-19
I like the performance of the 64 bit version of Flash, but my main issue is that since it is not contained within NSPluginWrapper, it has a nasty tendency of crashing and bringing Firefox down with it.

If I recall correctly though, I think I remember using the 64 bit Alpha 5 Live CD and being able to interact with Flash on sites like Youtube without any issue.

I still need to have NSPluginWrapper because, 32 or 64 bit, Flash will crash eventually on me, and I don't like having my 100+ tabs in Firefox being taken down with it. :)

---

### Post by Joe_Bishop on 2009-09-24
> **psyke83 said:**
> Folks,

If this is only affecting 64-bit users, it seems likely to be a problem with nspluginwrapper.
It affected me on my previous Karmic 32 bit installation, as well as on a current 64 bit one. I think it's "visual effects" issue.

---

### Post by daas88 on 2009-10-07
I had the same problem with karmic beta 64, although i could still pause with the spacebar and go to fullscreen with the F key. I just uninstalled the flashplugin-installer in synaptic and downloaded the [64bit alpha plugin]("http://labs.adobe.com/downloads/flashplayer10.html") from adobe, and then put it into /usr/lib/mozilla/plugins. 
It's working fine now.

---

