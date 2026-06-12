---
title: "Firefox Font Corruption"
date: 2009-05-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by coutts99 on 2009-05-11
Anyone noticed any font corruption in Firefox? E.g. -:

[http://imagebin.ca/view/alFpAz.html]("http://imagebin.ca/view/alFpAz.html")

Even worse in Konqueror -:

[http://imagebin.ca/view/c_I2CYh.html]("http://imagebin.ca/view/c_I2CYh.html")

---

### Post by coutts99 on 2009-05-11
Rebooted and seems ok now.

Seen this occasionaly on my home machine too

---

### Post by coutts99 on 2009-05-12
Rebooting fixes this, but after some time the corruption comes back.

Anyone else seeing this?

---

### Post by TrueTom on 2009-05-12
Do you have fonts installed that didn't come with Ubuntu? For me fonts like Adobe Garamond completely screw up X.org...

---

### Post by coutts99 on 2009-05-12
I've never specifically gone and installed any fonts so I don't think so.

---

### Post by portis on 2009-05-12
Maybe related to this bug:
[http://bugs.freedesktop.org/show_bug.cgi?id=21415](http://bugs.freedesktop.org/show_bug.cgi?id=21415)

---

### Post by coutts99 on 2009-05-12
Ah yes, that looks like it!

---

### Post by Sarvatt on 2009-05-12
Yep, I have the problem here. It starts with firefox but eventually ends up affecting the whole system if I don't reboot for a few hours after it starts. Thanks for the bug link, I'll try disabling swap and see if it still happens.

---

### Post by jerrylamos on 2009-05-12
My IBM Thinkpad R31 with i830 and latest jaunty & Intel driver updates gets corrupted fonts in a few minutes.  I looked at bugzilla however the patch there is reported as not working.

Jerry

---

