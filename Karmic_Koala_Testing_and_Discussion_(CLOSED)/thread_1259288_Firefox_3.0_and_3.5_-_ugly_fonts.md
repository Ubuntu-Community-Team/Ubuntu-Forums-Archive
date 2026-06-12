---
title: "Firefox 3.0 and 3.5 - ugly fonts"
date: 2009-09-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andrek on 2009-09-06
Hi!

First of all, I know about the issue in Firefox 3.5 that renders some fonts in a different way comparing to Firefox 3.0 and I've tried all the fixes that were supposed to solve that. Nothing worked, including custom ~/.fonts.conf file or deleting some stuff from /etc/fonts. 

Here's exactly what I mean :

[[img]http://a.imagehost.org/t/0536/f3_0.jpg[/img]](http://a.imagehost.org/view/0536/f3_0)
*Firefox 3.0*

[[img]http://a.imagehost.org/t/0928/f3_5.jpg[/img]](http://a.imagehost.org/view/0928/f3_5)
*Firefox 3.5*

(nevermind the weird gamma settings, looks like gimp or imagehost screwed something)

As you can see, only few parts of websites are being rendered incorrectly, without antialiasing.

Any piece of advice would be appreciated.

edit: As far as I recall, I had a similar issue on Archlinux and deleting some xorg-related fonts solved it. Unfortunately, the solution was written in "other os talk" section..

---

### Post by Starks on 2009-09-06
Ugh... This bug again.

[https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/412195](https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/412195)

---

### Post by andrek on 2009-09-06
Thanks, purging wine1.2 solved it.

---

### Post by frustphil on 2009-09-06
May I know what version of firefox you're using? How did you remove the menubar?

---

### Post by andrek on 2009-09-06
Both 3.0 and 3.5.2, as shown on screenshots.
It's the Hide Menubar add-on. (although I use Personal Menu which has that ability, too)

---

### Post by Starks on 2009-09-06
> **andrek said:**
> Thanks, purging wine1.2 solved it.
That hasn't worked for me.

---

