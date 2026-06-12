---
title: "Upgraded to 10.04 &quot;Could not open location&quot;"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by up2early on 2010-03-20
Upgraded from 9.10 to 10.04 and when I attempt to open any of my "Places" I get the following error message:

Could not open location 'file:///home/mike/Documents(or whatever folder I am trying to open)'

No application is registered as handling this file.

Thanks for any help

---

### Post by Ozymandias_117 on 2010-03-20
Try opening gconf-editor from a terminal, then navigating to /desktop/gnome/session/required_components Make sure there is a key there named "filemanager" with the value of "nautilus"

---

### Post by cosmicbuff on 2010-03-20
yup having the same problem, and had to bring on terminal to kick start gnome-panel . And in gconf editor it is set to "nautilus".
Added gnome-panel to auto start apps, it works,right click is not working from start,and still having problem with nautilus.

---

### Post by NightwishFan on 2010-03-20
This is related to this bug I reported a fix is in progress:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343)

---

### Post by Sef on 2010-03-20
Moved to Lucid.

---

