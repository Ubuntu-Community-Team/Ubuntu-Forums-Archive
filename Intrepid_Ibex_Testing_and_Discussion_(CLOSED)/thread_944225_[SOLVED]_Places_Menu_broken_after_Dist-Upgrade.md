---
title: "[SOLVED] Places Menu broken after Dist-Upgrade"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Abaddon on 2008-10-11
I've run Dist-upgrade to the Intrepid Beta, and now the shortcuts for my Home Folder and Desktop (ie not my custom Nautilus bookmarks) now give the following error:

Error:

Could not open location 'file:///home/user'

No application is registered as handling this file.

Any ideas on how to fix this?

(I've also been completely unable to get flash audio despite fiddling with pulseaudio, but that's another story :( )

---

### Post by Dauthi4 on 2008-10-11
Hi,

I've experienced the same issue and my solution is :

*Right click on a folder -> Properties
*Open With
*Add
*Finally, type "nautilus"

It worked on my laptop :)

---

### Post by Sef on 2008-10-11
> I've run Dist-upgrade to the Intrepid Beta....

That is not an approved way to upgrade in Ubuntu.  (It was, but not now.)  To upgrade correctly, read this [sticky]("http://ubuntuforums.org/showthread.php?t=936696").

---

### Post by taavikko on 2008-10-11
> **Abaddon said:**
> I've run Dist-upgrade to the Intrepid Beta, and now the shortcuts for my Home Folder and Desktop (ie not my custom Nautilus bookmarks) now give the following error:

Error:

Could not open location 'file:///home/user'

No application is registered as handling this file.

Any ideas on how to fix this?


Known bug [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492)

Open places&#8594;computer nautilus opens, go to home dir&#8594;right click folder&#8594;open with, open folder

---

### Post by Abaddon on 2008-10-11
> **Sef said:**
> That is not an approved way to upgrade in Ubuntu.  (It was, but not now.)  To upgrade correctly, read this [sticky]("http://ubuntuforums.org/showthread.php?t=936696").


I did actually upgrade-manager -d ... I was just shorthanding.

But the fix worked - thanks guys.

---

