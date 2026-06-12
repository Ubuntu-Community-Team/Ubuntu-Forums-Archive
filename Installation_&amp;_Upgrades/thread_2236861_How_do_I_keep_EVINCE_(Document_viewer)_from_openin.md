---
title: "How do I keep EVINCE (Document viewer) from opening PDF files?"
date: 2014-07-29
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2014-07-29
I use PDF Studio Pro 9 (an Adobe Acrobat equivalent for Linux) for my PDF documents.  In 12.04, I uninstalled Evince.   In 14.04, I cannot do that.  How do I disable or whatever to keep Evince from opening PDF files?

John

---

### Post by uRock on 2014-07-29
Right click a PDF, click **Properties**, go to **Open With tab**, select the **preferred application**, then click the **Set as default** button.

---

### Post by cigtoxdoc on 2014-07-29
Thank you, but that doesn't do it.  I need something that takes Evince out of the choices.  I think I need to modify evince.desktop, but don't want to do that w/o some knowledge of what to do.
John

---

### Post by uRock on 2014-07-29
I just ran **sudo apt-get remove evince** in a terminal and though it uninstalled the **ubuntu-desktop** package, it had no effect on the desktop system.

---

### Post by vasa1 on 2014-07-29
See 
help.ubuntu.com/community/MetaPackages 
and
[www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html](www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html) (even though it's about Lubuntu)
to know more about metapackages.

I understand that deleting a metapackage such as ubuntu-desktop has no adverse effect except if you want to upgrade in situ to a new release rather than do a fresh install of a new release. Even then, you can just re-install ubuntu-desktop before the upgrade, upgrade, and then again delete whatever you want (including the ubuntu-desktop).

I usually "lose" lubuntu-desktop within a few minutes of a clean install.

############

Your other approach seems more interesting. If you never want Evince to open a pdf file, removing **application/pdf** from the **MimeTypes=** list in */usr/share/applications/evince.desktop* (after backing up that file) may be worth trying. But I'm not sure that's the only thing that needs changing. Someone like mc4man will know the answer.

However, a more conventional approach would be to 
right-click on the pdf file in your file manager
choose Open with ...
then point to the application of your choice (unless it's a Wine thing about which I know nothing)
and click "Set selected app as default" (or whatever your file manager says here) 
*oops .. already covered by urock*

---

### Post by cigtoxdoc on 2014-07-29
Thank you for your help.  The folks at Qoppa Software, makers of the Studio Pro 9 software did not know about the bug I found in the studiopro9.desktop file.  Next alternative is Adobe reader which installs under wine.  That won't play nicely either.  Modifying the evince.desktop file may be a good option.

John

---

### Post by vasa1 on 2014-07-29
> **cigtoxdoc said:**
>  ... Modifying the evince.desktop file may be a good option.
...
I tried that briefly. Still opened with Evince. Why don't you just uninstall Evince?

---

### Post by cigtoxdoc on 2014-07-30
Thank you to all.  The answer is to remove evince as suggested by uRock.

John

---

### Post by zclock on 2014-09-10
I want to do the opposite, I want to convert a.pdf to an editable file.  Can this be done?

---

### Post by zclock on 2014-09-17
Thank you all.  I did solve my problem.  It was quick a dirty... I simply selected all & pasted into a document (.odt)  I didn't need the complex embedded objects(pictures) and the formatting was easy enough to recreate,  Then I had an editable document.  
I will try several of these and post back of there are relevance or preferred,  I was making things more complicated than necessary.
Learning, relearning. Thanks.

---

