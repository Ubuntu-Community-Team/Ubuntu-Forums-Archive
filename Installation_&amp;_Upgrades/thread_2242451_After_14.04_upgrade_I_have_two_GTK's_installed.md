---
title: "After 14.04 upgrade I have two GTK's installed"
date: 2014-09-01
forum: Installation &amp; Upgrades
---

### Post by micheus on 2014-09-01
I'm relatively new to Linux so after I upgrade Ubuntu 13.10 to 14.04 I noticed it has two different versions of GTK: 
 - 3.10.8-0ubuntu1.2
 - 2.24.23-0ubuntu1.1

Is there any problem about them coexists? Can this create any problem building programs?

I checked that because I was compiling a program that uses wxWidgets library and I got an error during a call to a function in wx module that gave me this message:
[PHP]./src/gtk/window.cpp(2919): assert "(m_widget != __null)" failed in DoGetClientSize(): invalid window[/PHP]

---

### Post by BazBear on 2014-09-01
I'm almost certain you should have both, as some things use GTK2, some GTK3. In any case, I have both on my system, same exact build numbers.

---

### Post by micheus on 2014-09-02
Thanks for the replay.

---

