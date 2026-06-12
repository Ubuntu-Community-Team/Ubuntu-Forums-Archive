---
title: "Where's the screensaver in Kubuntu?"
date: 2009-04-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2009-04-20
As the title suggests I have no screensaver settings at all in Kubuntu. Has someone hidden them somewhere really obscure or did my pc just forget to install them?

---

### Post by Reiger on 2009-04-20
System Settings -> Desktop -> Screensaver.

You may have to install a bunch of them first before more than just a `blank screen' pops up in the list of available choices.

---

### Post by macroshaft on 2009-04-20
Found the beggar! I've looked all over for that. Now if only I knew where to install them from...

---

### Post by macroshaft on 2009-04-20
Ok, on a gamble I found the correct package to add extra screensavers. Seriously did some designer think 'I know, I'll bundle in no screensavers and then hide them in the repositories, every newbie will psychicly know which package to grab!'

These are the things that leave people feeling frustrated & let down, they need to be either included or it needs to be made obvious where to get them (i.e. a get screensavers button in the screensaver app)

---

### Post by Zorael on 2009-04-20
Not sure if it's the one you mean, but there is a package that lets the KDE screensaver use xscreensaver's savers. This command should fetch it and some extras.
```
$ sudo aptitude install **~n**kscreensaver-xsavers
```

See [http://packages.ubuntu.com/search?keywords=kscreensaver&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=kscreensaver&searchon=names&suite=jaunty&section=all).

---

### Post by hikaricore on 2009-04-20
If you install Kubuntu properly via the kubuntu-desktop package or from a kubuntu install cd, screensavers should have been included.

---

### Post by macroshaft on 2009-04-20
I installed through a kubuntu live cd, I don't think it gets more properly than that.

---

### Post by Zorael on 2009-04-20
Yeah, in a default installation the only available screensaver is Blank Screen, unless something changed between Jaunty beta and Jaunty rc.

---

### Post by hikaricore on 2009-04-21
I suggest a bug report on launchpad then because that's not right.

---

### Post by Zorael on 2009-04-21
It seems to me to be more of an issue with screensavers not having been *written* yet. There are no KDE4 screensavers besides Blank Screen; you can only get more by installing that conduit between kscreensaver and xscreensaver.

---

### Post by NightwishFan on 2009-04-21
There are no screen savers on Jaunty Kubuntu Live CD. Nor were there on Intrepid.

---

