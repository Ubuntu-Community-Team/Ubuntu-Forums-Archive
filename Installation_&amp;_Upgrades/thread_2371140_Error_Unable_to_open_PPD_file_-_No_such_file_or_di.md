---
title: "Error: Unable to open PPD file - No such file or directory -- Not true!"
date: 2017-09-11
forum: Installation &amp; Upgrades
---

### Post by ffrr on 2017-09-11
Hi all,

After a change to 16.04 from 12.15 I am trying to get an Epson ET-14000 back to work. It had been working  before.

I installed cups. I opened the printer manager from the launcher. 

Properties -> Settings. Displays are:
Description: "EPSON ET-14000 Series" (correct),
Make and Model: "Generic ESC/P Dot Matrix Printer" (extremely incorrect,) -> Change Driver -> Choose Driver

Choose Drive displays three options:
"Select printer from database". (No ET series printers. Forget it!)
"Search for a printer driver to download". Make and Model shows correct.  Klick "search": Error "The application PRINTERS has closed  unexpectedly" (Forget it!)
"Provide PPD file" (Great, I have it!). File name shows correct. Klick "Forward": Error: "/etc/cups/ppd/EPSON-ET-14000-Series.ppd: FAIL", "Unable to open PPD file - No such file or directory"

NOT TRUE!!! 

$ ll /etc/cups/ppd/EPSON-ET-14000-Series.ppd
rw-r--r-- 1 root lp 15655 Sep  9 19:56 /etc/cups/ppd/EPSON-ET-14000-Series.ppd

Suggestions more than welcome. Thanks for any input.

Frederic

---

### Post by ffrr on 2017-09-13
I'm closing the thread with thanks to the adviser who suggested to use a Workforce driver. I picked the last one on the list (WF 1100) and it workedT

Frederic

(I would tag the thread 'CLOSED' if I could make out a way to do it)

---

