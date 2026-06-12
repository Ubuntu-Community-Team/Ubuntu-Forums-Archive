---
title: "after update to 18.04: cups-pdf broken"
date: 2018-08-29
forum: Installation &amp; Upgrades
---

### Post by fbusse on 2018-08-29
After update (with no error noticed), printing to PDF fails: Jobs are accepted, but not executed. The printer queue window show the error message (see screen shot)

**[COLOR="#0000FF"]File "/usr/lib/cups/backend/cups-pdf" unavailable: No such file or directory[/COLOR]**
(translation from German might not exactly fit to the original English text)

... and before you ask: There is indeed no such file or directory.

My search for hints to solve the problem gave no results, so far - any idea, here? (Answers to the parallel requests at the German fora [ubuntuusers.de]("https://forum.ubuntuusers.de/topic/nach-update-auf-18-04-cups-pdf-defekt/#post-9000986") and [kubuntu-de.org]("http://forum.kubuntu-de.org/index.php?topic=19285.0") will be forwarded.)

---

### Post by fbusse on 2018-08-29
**sudo apt-get install --reinstall printer-driver-cups-pdf**
solved the problem - thanks to [Kellerkind_2009 at ubuntuusers.de]("https://forum.ubuntuusers.de/topic/nach-update-auf-18-04-cups-pdf-defekt/#post-9001002")!

---

