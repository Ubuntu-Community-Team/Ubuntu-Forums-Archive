---
title: "Confirm a typo?"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mc4100 on 2008-10-06
Just need someone to check before I file a bug:
If you open Seahorse (Applications -> Accessories -> Passwords and Encryption Keys), then go to the "Remote" menu, then "Find Remote Keys...";
The title of the window (which should, of course, be Find Remote Keys) says, "***d* Remote Keys**". Also, if you do or do not see this, can you give the locale you're using.

---

### Post by volanin on 2008-10-06
Or maybe the string should have been **"%d Remote Keys"**.
This **%d** part is then replaced by the number of keys.
:)

---

### Post by wgrant on 2008-10-06
Works fine for me - en_AU.UTF-8 with Compiz.

---

### Post by jfernyhough on 2008-10-06
I see the d with en_GB.

---

### Post by klange on 2008-10-06
en_US, "Find Remote Keys".
(Maybe the "Fin" is just missing?)

---

### Post by mc4100 on 2008-10-06
> **jfernyhough said:**
> I see the d with en_GB.

I thought so: I am en_GB, too. I'll file the bug accordingly (it'll need to wait, the screenshot tool is being weird -- but I'll post it here when I do, in case other locales are affected, they can be added).

---

### Post by wgrant on 2008-10-06
The issue is in the translation [here](https://translations.edge.launchpad.net/ubuntu/intrepid/+source/seahorse/+pots/seahorse/en_GB/+translate?batch=10&show=all&search=find+remote+keys).

---

### Post by jfernyhough on 2008-10-06
I never thought translating en_US to en_GB could cause so much trouble.

:lolflag:

---

### Post by bruce89 on 2008-10-06
> **jfernyhough said:**
> I never thought translating en_US to en_GB could cause so much trouble.

Launchpad is too easy to mess with. Of course, translation shouldn't be done in LP.

---

### Post by mc4100 on 2008-10-06
I'm puzzled. wgrants' link shows the translation problem on launchpad, as a translation mishap, and...
>  This translation is managed by **Ubuntu** English (United Kingdom) Translators, assigned by **ubuntu**-translators. ... so therefor the bug should *not* be reported to bugzilla?
Where should I file it, upstream or on launchpad?

---

### Post by bruce89 on 2008-10-06
> **mc4100 said:**
> Where should I file it, upstream or on launchpad?

It's a Ubuntu problem.

---

### Post by mc4100 on 2008-10-06
[https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/279391](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/279391)

---

### Post by bruce89 on 2008-10-06
> **bruce89 said:**
> It's a Ubuntu problem.

My mistake, it's upstream - [http://svn.gnome.org/viewvc/seahorse/trunk/po/en_GB.po?view=markup](http://svn.gnome.org/viewvc/seahorse/trunk/po/en_GB.po?view=markup).

[http://bugzilla.gnome.org/show_bug.cgi?id=555323](http://bugzilla.gnome.org/show_bug.cgi?id=555323)

---

### Post by mc4100 on 2008-10-20
> seahorse (2.24.1-0ubuntu1) intrepid; urgency=low

  * New upstream version:
    - Fix problems with seahorse crashing when searching for remote keys.
      (lp: #272390)
    - Build fixes on Solaris
    - Fix selection of keys in libcryptui.
    **- I18n fixes. (lp: #279391)**
  * debian/patches/80_autoconf_update.patch:
    - new version update

 -- Sebastien Bacher <seb128@ubuntu.com>  Mon, 20 Oct 2008 09:07:00 +0200

This is supposed to be fixed, but I'm still seeing "*d Remote Keys*" after the update!
Can anyone using en_GB confirm this?

---

### Post by jfernyhough on 2008-10-20
Confirmed. Still there.

j@t7200:~$ aptitude show seahorse
Package: seahorse
State: installed
Automatically installed: no
Version: 2.24.1-0ubuntu1
Priority: optional
Section: gnome

---

### Post by wgrant on 2008-10-20
Ubuntu translations come in language packs. You won't see those fixes until the next language pack upload, but I saw them go through the import queue.

---

