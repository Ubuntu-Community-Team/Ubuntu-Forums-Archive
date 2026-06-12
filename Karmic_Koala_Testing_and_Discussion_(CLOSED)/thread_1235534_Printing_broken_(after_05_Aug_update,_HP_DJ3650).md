---
title: "Printing broken (after 05 Aug update, HP DJ3650)"
date: 2009-08-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by nick_stokie on 2009-08-09
After the updates earlier this week (around 05 Aug) to hplip, hpijs and others (cups and foomatic?), I can't print.

My HP DeskJet 3650 is reported by Ubuntu as either being okay or connection error (error 5012), there is no pattern as to whether it reports okay or not. When I send a document to print the print status reads: "Printing, weird page contents". The printer then feeds through the corresponding number of blank pages, ie a 3 page document results in 3 blank pages coming through. The printer does not have any cartridge action, it just feeds the pages through. Happens with OpenOffice, pdf viewer and text editor (gedit) so I'm fairly sure it is the printer driver rather than application specific.

Reverting to the jaunty drivers (at jaunty release) seems to fix so it must be one of the recent updates. Before I raise a bug has anyone else had a similar experience?

---

### Post by Tim 3255 on 2009-08-09
Yes, I have the almost the same problem. 
I have a network HP C6280 to which I can print wirelessly from my Thinkpad X41. Printing is fine with Windows XP and Karmic Kubuntu Beta 3 but with Karmic Ubuntu Alpha 3 all I get is blank pages.

Tim S

---

### Post by phenest on 2009-08-09
This is the first time I've tried my printer with Karmic, and I am having the same issue.

I have a HP Deskjet 460 via bluetooth. Test page printed nothing. The paper was simply fed through.

---

### Post by ayates on 2009-08-09
[https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/410556](https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/410556)

---

### Post by nick_stokie on 2009-08-09
ayates - thanks, I'd been searching on hp/hplip/hpijs and cups so hadn't spotted that one.

---

### Post by autocrosser on 2009-08-09
I'm seeing it also--Brother 2070N networked printer--all the other computers can print to it--Karmic can't---subscribed to the bug report.

---

### Post by nick_stokie on 2009-08-09
Reverting to the old version of libpoppler from here:

[https://launchpad.net/ubuntu/+source/poppler/0.11.0-0ubuntu4/+build/1087828/+files/libpoppler5_0.11.0-0ubuntu4_amd64.deb](https://launchpad.net/ubuntu/+source/poppler/0.11.0-0ubuntu4/+build/1087828/+files/libpoppler5_0.11.0-0ubuntu4_amd64.deb)

appears to resolve the issue.

---

### Post by Tim 3255 on 2009-08-09
Reverting to the older version of libpoppler5 did the trick for me, thanks
for the heads up.

Tim S

---

### Post by rogerdean on 2009-08-10
seems to be fixed with today's update...

---

### Post by phenest on 2009-08-14
> **rogerdean said:**
> seems to be fixed with today's update...

Mine is also working. A fix was commited: [bug 409962]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/409962")

---

