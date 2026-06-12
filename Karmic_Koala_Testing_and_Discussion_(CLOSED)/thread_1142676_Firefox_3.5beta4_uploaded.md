---
title: "Firefox 3.5beta4 uploaded"
date: 2009-04-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by int on 2009-04-29
Firefox 3.5beta4 uploaded, i think that will be by default when Karmic released
> firefox-3.5 (3.5~b4+nobinonly-0ubuntu1) karmic; urgency=low

  * New upstream release 3.5 b4

  [ H. Montoliu ]
  * fix LP: #361052 - firefox apport hook fails to retrieve pluginreg.dat file
    - update debian/apport/firefox-3.5.py - removed unused code and minor refactoring

 -- Alexander Sack < xxxx>   Wed, 29 Apr 2009 15:19:59 +0200

---

### Post by SKLP on 2009-04-29
Backport planned to jaunty-updates, or are there some PPA for us jaunty users ?

---

### Post by plun on 2009-04-29
> **SKLP said:**
> Backport planned to jaunty-updates, or are there some PPA for us jaunty users ?

Version 3.5 is already within Jauntys repo......just needs a final update when 3.5 is ready.

Package info:
[http://packages.ubuntu.com/jaunty/firefox-3.5](http://packages.ubuntu.com/jaunty/firefox-3.5)

For latest version of **both 3.5 and 3.6** you can use
Ubuntus Mozilla teams ppa

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by kabloink on 2009-04-29
> **SKLP said:**
> Backport planned to jaunty-updates, or are there some PPA for us jaunty users ?

I have been using the mozilla daily ppa for intrepid and jaunty.

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa")

---

### Post by Slug71 on 2009-04-29
Sweet, hopefully it will be default in Alpha 1.

---

### Post by SuperSonic4 on 2009-04-29
Does this run alongside normal firefox or instead of? I need firefox to check my bank online :p

---

### Post by meeples on 2009-04-29
> **SuperSonic4 said:**
> Does this run alongside normal firefox or instead of? I need firefox to check my bank online :p

it runs alongside normal firefox, it comes up in the app menu as Shiretoko Web Browser

---

### Post by freeman2000 on 2009-05-10
These 2 new versions come up as other browsers that run alongside FF 3.0.10.  Version 3.5 beta 4 shows up as Shiretoko.  Version 3.6 alpha 1 shows up as Minefield.  Both are listed as such in Applications --> Internet.  

There's also a new version of Thunderbird 3.0.  It shows up as Shredder 3 Mail/News.  Almost all of the add-ons and themes are not working at this point; however, NoScript and WOT both work.  Good luck.

---

### Post by madhi19 on 2009-05-26
I got 3.5 running and damn if it not the fastest Firefox ever build and it stable memory wise at around 100mb a pity considering how much memory Firefox use to leak. And I have not done any about:config tweek yet. Mozilla is going to make one hell of a bang with that browser!

---

### Post by yellerKat on 2009-05-26
> **madhi19 said:**
> I got 3.5 running and damn if it not the fastest Firefox ever build and it stable memory wise at around 100mb a pity considering how much memory Firefox use to leak. And I have not done any about:config tweek yet. Mozilla is going to make one hell of a bang with that browser!

Got any add-ons working or are you using nightly tester tools?

---

### Post by super.rad on 2009-05-26
A lot of the add-ons already work with 3.5, I only use a few (adblock, hide menubar and smart bookmarks) but all of those are fine

---

### Post by tad1073 on 2009-05-26
I just added and installed 3.5.
This thing is awsome and fast.
Now if the add-ons would come up to speed...

---

### Post by taavikko on 2009-05-26
> **tad1073 said:**
> 
Now if the add-ons would come up to speed...

Add-ons ? 
I use it to browse the content available in the www.
Not to play with add-ons ;) (notice the wink)

It sure is fast but memory usage is excessive with adobes 64-bit flash plugin.
Then again, running with radeon driver, which explains jerking and tearing...

---

### Post by tad1073 on 2009-05-26
> **taavikko said:**
> Add-ons ? 
I use it to browse the content available in the www.
Not to play with add-ons ;) (notice the wink)

It sure is fast but memory usage is excessive with adobes 64-bit flash plugin.
Then again, running with radeon driver, which explains jerking and tearing...

The add-0ns I use

```

Application: Firefox 3.0.10 (2009042523)
Operating System: Linux (x86_64-gcc3)

- Adblock Plus 1.0.2
    http://adblockplus.org/
    Firefox 2.0 - 3.6a1pre
- All-in-One Gestures 0.19.1
    http://pagesperso-orange.fr/marc.boullet/ext/extensions-en.html
    Firefox 1.0 - 3.0.*
- All-in-One Sidebar 0.7.10
    http://firefox.exxile.net/aios
    Firefox 3.0 - 3.5.*
- AVG Safe Search 8.5
    http://www.avg.com
    Firefox 1.5 - 3.1.*
- CustomizeGoogle 0.76
    http://www.customizegoogle.com/
    Firefox 1.0 - 3.6a1pre
- Delicious Bookmarks 2.1.041
    http://delicious.com
    Firefox 2.0 - 3.5.*
- disablemenu 0.3.2
    http://www.genoetigt.de/site/projects/disablemenu
    Firefox 1.5 - 3.0.*
- DownloadHelper 4.4.1
    http://www.downloadhelper.net
    Firefox 1.5 - 3.6a1pre
- Extension List Dumper 1.14.1
    http://sogame.awardspace.com/
    Firefox 1.5 - 3.0.*
- Fast Dial 2.22b
    http://userlogos.org/extensions/fastdial
    Firefox 3.0 - 3.6a1pre
- FirefoxNotify 1.5.2
    Firefox 1.5 - 3.5.*
- Forecastbar Enhanced 0.9.6
    http://users.rcn.com/shoofy/forecastfox_enhanced/
    Firefox 1.5 - 3.5.*
- GooglePreview 3.21
    http://ackroyd.de/googlepreview/
    Firefox 1.5 - 3.6a1pre
- Linky 2.7.1
    http://gemal.dk/mozilla/linky.html
    Firefox 0.7 - 4.0
- Microsoft .NET Framework Assistant 1.1
    http://www.windowsclient.net/
    Firefox 1.5 - 3.*.*
- Personal Menu 4.1.4
    https://addons.mozilla.org/firefox/addon/3895/
    Firefox 1.5 - 3.6a1pre
- Stop-or-Reload Button 0.2.2
    http://v2studio.com/k/moz/
    Firefox 2.0 - 3.0.*
- Tab Mix Plus 0.3.7.3
    http://tmp.garyr.net
    Firefox 2.0 - 3.1b2pre
- Ubuntu Firefox Modifications 0.7
    Firefox 1.5 - 3.0.*

```

---

### Post by inportb on 2009-05-26
@taavikko: you get the graphics issues with radeon too? I thought I was the only one experiencing the "jerking," as you put it. Perhaps I just don't know how to describe the problems adequately.

---

### Post by taavikko on 2009-05-26
> **inportb said:**
> @taavikko: you get the graphics issues with radeon too? I thought I was the only one experiencing the "jerking," as you put it. Perhaps I just don't know how to describe the problems adequately.

Radeon driver running 
```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3400 Series [1002:95c4]
	Subsystem: Hewlett-Packard Company Device [103c:3600]
```

"Jerking" is subtle, best observed in flash. No mentionable while watching content via "smplayer || mplayer"

---

### Post by inportb on 2009-05-26
Ah... same here w/ the radeon driver, but also during massive screen updates. Oh well... it'll be fixed sooner or later lol.```
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
        Subsystem: Toshiba America Info Systems Device ff00
```

---

### Post by ghindo on 2009-05-26
Just make sure you file a bug report ;)

---

