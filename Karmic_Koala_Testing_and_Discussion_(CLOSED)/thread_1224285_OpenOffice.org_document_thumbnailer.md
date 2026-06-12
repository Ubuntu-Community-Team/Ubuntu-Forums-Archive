---
title: "OpenOffice.org document thumbnailer"
date: 2009-07-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Flimm on 2009-07-27
[guidoc](http://ubuntuforums.org/member.php?u=406023) and I, (among others), have been working on an OpenOffice.org document, spreadsheet, presentation and drawing thumbnailer for Ubuntu Karmic Koala.
We've gotten pretty far: the thumbnails are generated properly, but only if imagemagick is installed. Without it, "film strips" are added to the thumbnails.

I haven't installed Karmic yet, so I'm looking for some volunteers to test it, with and without imagemagick installed.

You can find the .deb at my experimental PPA: [https://launchpad.net/~flimm/+archive/experimental](https://launchpad.net/~flimm/+archive/experimental)
You can find the bazaar branch at [https://code.launchpad.net/~flimm/+junk/bash-ooo-thumbnailer](https://code.launchpad.net/~flimm/+junk/bash-ooo-thumbnailer)
Bug report: [https://bugs.launchpad.net/ubuntu/+source/ooo-thumbnailer/+bug/25827](https://bugs.launchpad.net/ubuntu/+source/ooo-thumbnailer/+bug/25827)

I've attached a screenshot.

Tell me if it works in this thread please. Thank you!

---

### Post by Martje_001 on 2009-07-27
Looks great :). I don't use Karmic, so I can't test it :(.

Can you tell me why filmstrips are added to the thumbnails without imagemagick? And is it fixable before launching Karmic?

---

### Post by MadMan2k on 2009-07-27
thunar (xfce filemanager) does this already in jaunty - probably you can take a look at that...

---

### Post by biasquez on 2009-07-27
how works this addon? i'm using karmic and i installed addon from ppa but i don't know how test here.

---

### Post by wayne_cat on 2009-07-27
> **biasquez said:**
> how works this addon? i'm using karmic and i installed addon from ppa but i don't know how test here.

you can find some links do discussions and documents in the bug report:

[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/25827](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/25827)

---

### Post by Flimm on 2009-07-27
> **biasquez said:**
> how works this addon? i'm using karmic and i installed addon from ppa but i don't know how test here.
Hmmm. Okay, try this:
[list][*]Delete ~/.thumbnails
[*]kill nautilus by running nautilus -q
[*]Log in and out.[/list]
Then create a new OpenOffice.org document and see if the thumbnail has been created.

---

### Post by Flimm on 2009-07-27
> **MadMan2k said:**
> thunar (xfce filemanager) does this already in jaunty - probably you can take a look at that...
We did use some of thunar-thumbnailer's code. Trouble is, it depends on imagemagick. If we want ooo-thumbnailer to be included by default for Ubuntu (GNOME), we can't depend on imagemagick, in order to save space.

---

### Post by zekopeko on 2009-07-27
Question: Doesn't OO.org embed the thumbnails in the document by default?
If they are of lower quality then perhaps targeting OO.org would be a better time investment.

---

### Post by durand on 2009-07-27
> **zekopeko said:**
> Question: Doesn't OO.org embed the thumbnails in the document by default?
If they are of lower quality then perhaps targeting OO.org would be a better time investment.

It does. I've checked an ODS and and ODT and both thumbnails are 181x256 though I'm not sure if its a good idea to use them. They're pretty bad quality and they don't have any antialiasing..

---

### Post by zekopeko on 2009-07-27
That's why I suggest that it's fixed on the OO.org side and on our we simply extract them.

---

### Post by durand on 2009-07-27
And that would also remove the need for imagemagick.

---

### Post by JohnJackson on 2009-08-02
Seems to work OK with odt, ods and odp files, with one exception. I have an odt file saved from a doc with Word 2007 and it doesn't generate a thumbnail for that. If I save the doc as odt from OpenOffice it does generate a thumbnail. I guess that's down to a difference in Word's odt file format.

---

### Post by MadsRH on 2009-08-02
[SIZE="3"]Awesome work![/SIZE]

I do hope this work will land in 9.10 - imagemagick or not :D

---

### Post by Slug71 on 2009-08-04
A bit OT but are we gonna get OOo-3.1 in Karmic?


Update:
Nevermind, i guess we are at 3.1.0. It just says 3.0 at start up.

---

### Post by zekopeko on 2009-08-04
Using my ninja skillz that no other mortal can master:

[http://packages.ubuntu.com/search?keywords=openoffice&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=openoffice&searchon=names&suite=karmic&section=all)

---

### Post by Flimm on 2009-08-12
The bug I'm talking about seems to be fixed. Could somebody test [this patch](http://bugzilla.gnome.org/show_bug.cgi?id=576750) and tell me if it adds a white background to a transparent png when using the -r option?

---

