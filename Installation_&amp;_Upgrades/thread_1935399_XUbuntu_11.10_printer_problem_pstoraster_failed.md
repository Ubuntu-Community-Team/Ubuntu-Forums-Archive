---
title: "XUbuntu 11.10 printer problem: pstoraster failed"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by Arthur P on 2012-03-04
On previous (recent) versions of Linux I haven-t encountered this problem but with 11.10 my Epson BX600FW was found on the network and the EPS (ESC) printer driver installed but printing failed with an error message pstoraster failed. I did quite a bit of searching and found lots of posts on this topic with various printers but no clear solutions, or at least none that worked. I even completely removed everything CUPS and Ghostscript related and reinstalled with no improvement. 

Eventually for this printer I found that installing the printer, and then going to the printer properties and choosing as the specific sub-driver "Epson Stylus Office BX600FW - CUPS+Gutenprint v5.2.7" (or "Epson Stylus Office BX600FW - CUPS+Gutenprint v5.2.7 (Simplified)"), with overwriting of previous settings with the default settings for these subdrivers, solved the problem. 

One thing that will immediately signal the problem is resolved is that you will see options to print a printer test page and printer maintenance, and will get information on the ink levels which I was not getting with the ESC/P-R driver being installed as the default and recommened.

Not sure why the other subdriver is having problems. But I hope this information is helpful and may also help others resolve the "pstoraster failed" problems.

---

