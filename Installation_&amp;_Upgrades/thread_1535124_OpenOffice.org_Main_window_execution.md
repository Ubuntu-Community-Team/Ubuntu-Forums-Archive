---
title: "OpenOffice.org Main window execution"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-07-20
I have installed OpenOffice 3.2.0 on Ubuntu 10.04 (64-bit) and all seems to be working ok. Currently, I need to click on

Applications -> Office -> ,,,

and select which OpenOffice module I would like to execute. It would be much easier (and preferred) to be able to execute OpenOffice.org (Main window) directly from an icon in a panel. That is, I would like to have an icon in a panel that when clicked on would bring up the Main window for OpenOffice --- this Main window menu is shown in the attached screenshot.

How can I get this single icon to give (when clicked on) this Main window for OpenOffice?

Any suggestions would be appreciated.

---

### Post by ajgreeny on 2010-07-20
On my system I just made a launcher in my panel for /usr/bin/ooffice and get exactly what you want.

However, I am wondering why you have "installed OpenOffice 3.2.0" as it is installed by default in ubuntu 10.04.  Perhaps you mean that you just installed the whole system with OOo 3.2.0.

---

### Post by virsto on 2010-07-20
> **ajgreeny said:**
> On my system I just made a launcher in my panel for /usr/bin/ooffice and get exactly what you want.

However, I am wondering why you have "installed OpenOffice 3.2.0" as it is installed by default in ubuntu 
10.04.  Perhaps you mean that you just installed the whole system with OOo 3.2.0.


Your analysis is correct --- it was installed. I had to uninstall it a few days ago, and then I re-installed it.

How can I make a launcher for this Main window? This should have been my original question.

Thank you, ajgreeny :D

---

### Post by ajgreeny on 2010-07-20
Right click in an empty part of the panel and use "Add to Panel" then "Custom application Launcher" and a Create launcher window will appear.  Enter text as in my screenshot and click OK.

All done!

---

### Post by virsto on 2010-07-20
> **ajgreeny said:**
> Right click in an empty part of the panel and use "Add to Panel" then "Custom application Launcher" and a Create launcher window will appear.  Enter text as in my screenshot and click OK.

All done!

Yes, I have it working. But, there is still one missing part --- How can I find the icon for the OpenOffice Suite (seagulls on a blue sky background). I know how to change the icon for an application launcher; but, where is this icon image (*.svg or *.png or ??)

Any hints on where I can get it?

---

### Post by ajgreeny on 2010-07-20
**/usr/share/icons/hicolor/48x48/apps/openofficeorg3-startcenter.png**

They don't make it easy to find, do they? It is also in some of the other size folders eg 32x32, but not all, so look around a bit.

---

