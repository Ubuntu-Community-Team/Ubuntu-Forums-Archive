---
title: "Printer Problem since 10.04"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by jobrea on 2010-06-10
My Printer Brother DCP-8045D only prints, when I send the computer (Lenovo X200) to suspend (or shutdown) and wake it up again, whilst a document is in the printer queue. Does anyone know how to solve that problem?

---

### Post by teilnehmer on 2010-06-10
jobrea, 

maybe CUPS (the printing server) isn't running when you first try printing? In that case, you wouldn't be able to configure printers, too. If that is the case, try manually starting cups by entering
```
sudo /etc/init.d/cups start
```

If this helps, you are most likely suffering from a [known bug]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/554172") for which there isn't a fix yet - CUPS sometimes doesn't start on boot. 

I hope this helps until they fix it. This is really a pretty severe bug. 

Jan

---

### Post by revelationman on 2010-08-19
Yes that work for me but the Printing is still off very distorted  etc , but the command worked for me.

---

