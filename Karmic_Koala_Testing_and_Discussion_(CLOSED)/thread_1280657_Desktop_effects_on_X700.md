---
title: "Desktop effects on X700"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Enigmatic on 2009-10-02
I have a (mobile) X700 graphics card in my laptop, and I can't seem to enable desktop effects. I actually have no xorg.conf at the moment but everything seems to work fine. If I go into hardware drivers it doesn't find any drivers. Ideas?

---

### Post by danwood76 on 2009-10-02
You shouldnt need to edit the Xorg.conf.
What exactly happens when you enable desktop effects?

---

### Post by Enigmatic on 2009-10-02
It just says they could not be enabled.

---

### Post by danwood76 on 2009-10-02
Is this a clean install?
Are all updates installed?

A little more info is always welocme.

Also its worth remembering that karmic is afterall a dev release, if it doesnt work open up a bug report on the subject.

---

### Post by Enigmatic on 2009-10-02
Sure - no it's not clean, I've had it for a while and I don't think I've ever tried enabling desktop effects. I see I have the radeon, ati and fglrx packages installed. Should I try removing those perhaps?

---

### Post by Enigmatic on 2009-10-03
A reinstall fixed it. 3 years and about 7 Ubuntu releases were probably a bit too long to not reinstall.

---

