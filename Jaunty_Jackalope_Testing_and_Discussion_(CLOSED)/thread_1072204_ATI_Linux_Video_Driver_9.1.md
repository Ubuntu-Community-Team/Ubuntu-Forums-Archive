---
title: "ATI Linux Video Driver 9.1"
date: 2009-02-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Exsecrabilus on 2009-02-17
[http://news.softpedia.com/news/Latest-ATI-Linux-Video-Driver-Introduces-Full-OpenGL-3-0-Support-103262.shtml](http://news.softpedia.com/news/Latest-ATI-Linux-Video-Driver-Introduces-Full-OpenGL-3-0-Support-103262.shtml)

Will this make it into Jaunty?

---

### Post by MadMan2k on 2009-02-17
I am sorry to say no.

it is already in... :D

---

### Post by daponz on 2009-02-17
I thought I heard that fglrx 9.1 was not compatible with the xserver 1.6 included in Jaunty.

Does fglrx 9.1 really runs under Jaunty ?

Thanks for any input, that's the last thing I'm waiting for before switching to Jaunty :)

---

### Post by ace214 on 2009-02-17
No, it's not compatible. If you look at the [changelog for the fglrx driver package]("http://changelogs.ubuntu.com/changelogs/pool/restricted/f/fglrx-installer/fglrx-installer_8.573-0ubuntu4/changelog") it has this:
> fglrx-installer (2:8.573-0ubuntu1) jaunty; urgency=low

  * New upstream release. (9-1).
    - This release still does *not* meet the Xorg server 1.6 ABI.
      It is being uploaded to ensure that there are no other integration
      related issues that come up.

 -- Mario Limonciello <superm1@ubuntu.com>  Thu, 29 Jan 2009 20:37:38 -0600

The updates since then have not been significant.
Things seem to work fine for me for every day desktop use with the open source driver, though. I don't play any games or anything like that. Only thing that's a little funny is Skype video.

---

### Post by daponz on 2009-02-18
Does the RadeonHd driver allows to use any kind of 3d acceleration for desktop compositing (compiz) with rv770 (4800 series) ?

---

### Post by rbmorse on 2009-02-18
No, not quite yet. There is an experimental branch available for testing:

[http://www.x.org/wiki/radeonhd%3Ar6xx_r7xx_branch](http://www.x.org/wiki/radeonhd%3Ar6xx_r7xx_branch)

---

### Post by Exsecrabilus on 2009-02-23
Yeah, I read that changelog, but looked at the package version number, so was confused.

Thanks. I was just curious, but I don't need it, because after upgrading to Intrepid, I found out my graphic card finally worked with an out-of-the-box open-source driver.

---

