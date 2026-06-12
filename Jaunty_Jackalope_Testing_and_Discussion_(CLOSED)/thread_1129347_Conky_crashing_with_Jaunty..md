---
title: "Conky crashing with Jaunty."
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hikaricore on 2009-04-18
Has anyone else had this issue?

> 
[hikaricore@devistate:~ (8.2 Mb)]$ conky

Conky: desktop window (180012d) is subwindow of root window (13c)
Conky: window type - override
Conky: drawing to created window (0x3400001)
Conky: drawing to double buffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  2 (X_ChangeWindowAttributes)
  Serial number of failed request:  294
  Current serial number in output stream:  295

Running kde4 with an Nvidia card and the latest drivers.
This issue also occurs with the packaged Nvidia drivers in the repo.
No other video problems aside from the standard KDE crap, gaming and desktop effects work perfectly.
This issue also occurs when kwin's effects are turned off.  >.<

---

### Post by hikaricore on 2009-04-19
Mucked around with drivers again and no results.  Thinking of building conky from source to be sure it's not an issue with the package.

---

