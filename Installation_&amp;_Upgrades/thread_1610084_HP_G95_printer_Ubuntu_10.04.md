---
title: "HP G95 printer Ubuntu 10.04"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2010-10-31
With a new install of Ubuntu 10.04 I found that the usb connected HP G95 Officejet all in one printer was recognised but would not print. Some useful activity was happening in the printer at times, but still  apparently no printing.

The hplip version offered was 3.10.2. I tried various drivers from the system>administration>printers facility, and tried printing a short document or test page variously. Whenever I looked, the document print status showed, after a few seconds, 'not connected'.

However, at a later time, I found a correctly printed HPLIP print test page completed from the printer (!), but did not know what were the successful conditions.

However, by that time I had found the HP Linux imaging and printing web site
[http://hplipopensource.com/hplip-web/models/officejet/officejet_g95.html](http://hplipopensource.com/hplip-web/models/officejet/officejet_g95.html)
and then downloaded the latest hplip (currently 3.10.9 for G95)

and after following the instructions, it worked well. It was necessary to remove the earlier hp driver installation first.

Thank you to all involved in this.

---

