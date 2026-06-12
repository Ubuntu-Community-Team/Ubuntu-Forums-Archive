---
title: "Installing kpdfimport"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by krishnamohan on 2010-01-02
Hi..

I was trying to install kpdfimport so that I can (I guess) work with pdf files in kword...

On doing ***./configure***, I get 

checking for Qt... configure: error: Qt (>= Qt 3.0) (headers and libraries) not found. Please check your installation!

Well...I install all the qt libraries and headers I find but to no avail..but then I found that the following works..
[I][B]
./configure --with-qt-includes=/usr/include/qt3 --with-qt-libraries=/usr/lib/qt3[/B][/I]

But, now it says...

[I][B]checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!


[/B][/I]Iinstalled the kde-dev package but the result is the same....

What is to be done?

---

