---
title: "Downloading with Chrome causes it to crash"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by paradoxni on 2010-04-17
Anyone else having Google Chrome crash on them when trying to download (any!) files??

When I click on a download link, or right click save as, or download Chrome extensions, the download bar appears at the bottom with the file beginning to download, however a few seconds later Chrome crashes and disappears, stopping me from downloading anything.

Any site / any file type.
Ubuntu 10.04 64bit
2.6.32-21-generic

google-chrome-beta and google-chrome-dev are both affected, including the latest dev version (5.0.375.9 dev) which was updated today (2010-04-17)

Syslog:
> Apr 17 09:06:50 computer-name kernel: [  711.347823] chrome[3369]: segfault at 7f286006dff8 ip 0000000000a21b00 sp 00007f286006e008 error 6 in chrome[400000+279d000]


---

### Post by JCoster on 2010-04-17
Run chrome from terminal and see if it outputs any specific error messages?

---

### Post by paradoxni on 2010-04-17
it does...the same segfault as mentioned in the syslog above

---

### Post by phillw on 2010-04-17
Hi,

you may want to get Chromium from the repositry, I've been using it for a while now and it downloads quite happily.

Regards,

Phill.

---

### Post by paradoxni on 2010-04-17
same problem using chromium browser, although it has created an automatic crash bug report, which I  have uploaded to launchpad.

---

### Post by phillw on 2010-04-17
> **paradoxni said:**
> same problem using chromium browser, although it has created an automatic crash bug report, which I  have uploaded to launchpad.

Hmm, most odd I'm using the 5.0.342.9 (43360) Ubuntu version of Chromium and have just gone and gotten java from the java website no problem. Sorry I can't suggest anything else :-\

Regards,

Phill.

---

### Post by d3v1150m471c on 2010-04-17
axel + flashgot + firefox

---

### Post by MacUntu on 2010-04-17
Not seeing this with 5.0.379.0 (44736) from the daily PPA (x86). Maybe a bad addon?

> **d3v1150m471c said:**
> axel + flashgot + firefox

Err, no?

---

