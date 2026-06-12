---
title: "Amarok2 not working in Gnome"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by harty83 on 2009-04-07
I've upgraded to Jaunty from Intrepid.  All sound works in Gnome except for amarok2.  How do I get sound to work for KDE apps under Gnome?  No errors are given and it looks like the file is actually playing, but with no sound.

Thanks,
Alan

---

### Post by hobo on 2009-04-07
I too had this problem:

losf | grep snd

fixed it for me. I have no idea what it does, other than it fixed my problem. From:

[http://panela.blog-city.com]("http://panela.blog-city.com")

---

### Post by harty83 on 2009-04-07
> **hobo said:**
> I too had this problem:

losf | grep snd

fixed it for me. I have no idea what it does, other than it fixed my problem. From:

[http://panela.blog-city.com]("http://panela.blog-city.com")

Thanks for replying.  However, I do not have an app called losf.

losf?  I have no such program nor can I find it in apt.  Is that the correct spelling?

Thanks!
Alan

---

### Post by hobo on 2009-04-07
[http://en.wikipedia.org/wiki/Lsof]("http://en.wikipedia.org/wiki/Lsof")

Worked for me under 3.5 but not 4.2 ????   KDE

I am assuming you submitted this via the CLI ?

---

### Post by hobo on 2009-04-07
opps...............lsof would be the command...sorry

---

### Post by harty83 on 2009-04-07
I'm afraid that did nothing but list the current open files with snd in the name.  Still having the problem.

Thanks,
Alan

---

### Post by gwenn on 2009-04-07
Install System Settings.
 SYS SETT > Multimedia > Switch to another Output device

---

### Post by harty83 on 2009-04-09
> **gwenn said:**
> Install System Settings.
 SYS SETT > Multimedia > Switch to another Output device

No go.  The device is fine as sound works in everything for Gnome but not KDE (like amarok2).  

Thanks,
Alan

---

### Post by michaelzap on 2009-04-11
Try

sudo apt-get install libxine1-ffmpeg

If that fails, you can always

sudo apt-get install exaile ;-)

---

### Post by harty83 on 2009-04-11
> **michaelzap said:**
> Try

sudo apt-get install libxine1-ffmpeg

If that fails, you can always

sudo apt-get install exaile ;-)

Both are already installed.  Exaile has come a long way but is still no match for Amarok ;-)

Thanks,
Alan

---

