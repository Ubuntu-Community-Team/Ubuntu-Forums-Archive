---
title: "moonlight crashes Firefox"
date: 2010-03-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by executorvs on 2010-03-16
has anyone else had this problem? it prevents firefox from being able to load.
to recreate make sure moonlight is installed and make firefox attempt to rebuild it's plugin database this can be done by installing certain plugins or deleting the pluginreg.dat in ~/.mozilla/firefox/random#s.default

I filed a bug report at [https://bugs.launchpad.net/ubuntu/+source/moon/+bug/538796](https://bugs.launchpad.net/ubuntu/+source/moon/+bug/538796) but can't add any apport reports at the moment because it doesn't seem to like the server...

---

### Post by grandtoubab on 2010-03-16
which version of firefox?
which version of moonlight ?

see the compatibility
[http://go-mono.com/moonlight/faq.aspx](http://go-mono.com/moonlight/faq.aspx)

for me moonlight is not needed as gecko-mediaplayer plug-in package  do the job :=))

---

### Post by executorvs on 2010-03-16
current versions in repo FF 3.6 and moonlight 2.2. when did gecko-media-player achieve the ability to emulate silverlight specific script functions and does it do so by using libmoon? if so you may encounter the same bug.

as for moonlight's site, there are no mentions of this bug on bugzilla and I haven't tried using the development version of moonlight 3.0  as it's still in alpha and thus not a suitable solution for the average user.

---

### Post by grandtoubab on 2010-03-17
> **executorvs said:**
> current versions in repo FF 3.6 and moonlight 2.2. when did gecko-media-player achieve the ability to emulate silverlight specific script functions and does it do so by using libmoon? if so you may encounter the same bug.

as for moonlight's site, there are no mentions of this bug on bugzilla and I haven't tried using the development version of moonlight 3.0  as it's still in alpha and thus not a suitable solution for the average user.


I just want to tell I watch all videos with gecko-mediaplayer.
Could you give us a link where gecko-mediaplayer is not working?

---

### Post by executorvs on 2010-03-17
gecko-media-player does not support silverlight applications apparently..
the olympics hosted at [http://www.ctvolympics.ca/video/index.html](http://www.ctvolympics.ca/video/index.html)
or [http://www.nibblestutorials.net/](http://www.nibblestutorials.net/) or pretty much any site that uses silverlight extensivly. It really only bothers me for a single class related webapp, but as I need that app for now I would like to not have to uninstall and reinstall moonlight whenever I make a large change(this happens daily as I futz with things a lot). 

apparently the moonlight 3 alpha (2.99.0.3) has fixed this bug but still has many others. alpha plugins in alpha OSes so many places for things to go wrong. 
This will all be better tomorrow I'm sure as it will be alpha plugin on a beta OS, and that will make such a difference :-P I actually do like findig problems, I just wish I was better at fixing them as opposed to just isolating them.

---

