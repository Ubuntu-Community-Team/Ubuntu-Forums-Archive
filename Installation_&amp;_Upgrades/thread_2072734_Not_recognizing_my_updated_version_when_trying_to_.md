---
title: "Not recognizing my updated version when trying to install apps"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by vwise on 2012-10-18
Hey Everyone,

Sorry for the confusing title. 

Okay, so I updated from 10.04 to 12.04 last night. Now, when I try to install the "Screenlets" app, it informs me that I need to insert the installation cd. It does this even when the CD is in the drive, and persists in sending this message indefinitely in the terminal (or in the software center until it crashes). Am I doing something wrong?

---

### Post by snowpine on 2012-10-18
Ubuntu has a list of software sources stored in the text file /etc/apt/sources.list

You can edit this file directly using your favorite text editor, or by using the supplied GUI tool (if you're using Unity, tap the Super/Windows key, then type "Software Sources").

It should be pretty obvious which is the CD, but if not, post the contents of the file here, and I will help you interpret. :)

---

