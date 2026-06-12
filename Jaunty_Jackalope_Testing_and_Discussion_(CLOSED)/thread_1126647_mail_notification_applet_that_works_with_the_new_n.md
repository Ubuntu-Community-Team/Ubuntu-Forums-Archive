---
title: "mail notification applet that works with the new notifications?"
date: 2009-04-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ELD on 2009-04-15
Is there any applet that will work with the new notifications Jaunty has, only needs to support gmail for me.

---

### Post by olskar on 2009-04-15
mail-notification, at least if you delete all entries in /apps/mail-notification/popups/actions (gconf)

---

### Post by phaed on 2009-04-15
I'm looking forward to Specto being developed further.  Right now I use Firefox add-ons to check Gmail and Google Reader.  Would be nice if I could get notifications through the new system rather than Firefox pop ups.  That could be accomplished with an app like Specto, or if Firefox is modified to use Notify OSD.

---

### Post by G|N| on 2009-04-16
> **phaed said:**
> I'm looking forward to Specto being developed further.  Right now I use Firefox add-ons to check Gmail and Google Reader.  Would be nice if I could get notifications through the new system rather than Firefox pop ups.  That could be accomplished with an app like Specto, or if Firefox is modified to use Notify OSD.

Specto is already able to notify you for Gmail and Google Reader updates :)
But the official release does not support Notify OSD yet so you will have to use this ppa:
[https://launchpad.net/~specto-bzr/+archive/ppa](https://launchpad.net/~specto-bzr/+archive/ppa)
This ppa is stable and it always contains the latest bugfixes, features,... :)

I hope you will like it!

---

### Post by olskar on 2009-04-16
> **G|N| said:**
> Specto is already able to notify you for Gmail and Google Reader updates :)
But the official release does not support Notify OSD yet so you will have to use this ppa:
[https://launchpad.net/~specto-bzr/+archive/ppa](https://launchpad.net/~specto-bzr/+archive/ppa)
This ppa is stable and it always contains the latest bugfixes, features,... :)

I hope you will like it!

Segfaulting for me...


> /usr/lib/python2.6/dist-packages/spectlib/tools/iniparser.py:309: DeprecationWarning: the sets module is deprecated
  from sets import Set
/usr/lib/python2.6/dist-packages/spectlib/plugins/watch_web_static.py:32: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
ImportError: No module named numpy.core.multiarray
Segmenteringsfel


---

### Post by G|N| on 2009-04-16
sudo apt-get install python-numpy

Since python 2.6 numeric python is replaced by numpy, but the deb does not cover this yet.

---

### Post by phaed on 2009-04-18
Thanks, that works really nice.  And Specto has Facebook support!  I like seeing updates from Gmail, Google Reader and Facebook with the new notifications system.

---

### Post by phaed on 2009-04-18
BTW, are you a Specto developer?  Because I have a feature request.

---

### Post by Technoviking on 2009-04-19
I'm enjoying specto, just what I was looking for.

T-V

---

