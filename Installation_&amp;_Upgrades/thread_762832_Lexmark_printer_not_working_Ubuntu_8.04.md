---
title: "Lexmark printer not working Ubuntu 8.04"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by wrgb2 on 2008-04-22
Hi,

I just installed Ubuntu 8.04.  Everything is working except the printer.  Ubuntu installed a text-mode driver for my Lexmark 730 series printer (actual printer is a Z730), but it doesn't work.  When I try to print from an application, nothing happens.  When I try to print a test page from the printer control panel I get the following error:

CUPS server error: There was an error during the CUPS operation: 'client-error-document-format-not-supported'

Can someone help, please?

Randy
[http://nocostsoftware.blogspot.com](http://nocostsoftware.blogspot.com)
[http://freebloggingtools.blogspot.com](http://freebloggingtools.blogspot.com)

---

### Post by wpshooter on 2008-04-22
My "guess" is that if your specific model of Lexmark is not listed in the drivers listing then you are probably not going to get it to work.

I recently tried to get a Lexmark model 611Z working for my brother-in-law and I finally gave up !!!

P. S. - get yourself a HP printer and make your life a little easier !!!

---

### Post by wrgb2 on 2008-04-22
Thanks, wpshooter, you were right.  The Z730 was not listed as one of the available drivers when I deleted it and tried to reinstall it.  I had high hopes because it correctly came up with the model name of the printer (at least the 730 portion of it).  I have another printer, a HP Deskjet D4160 and it came up and played (almost) perfectly.  Still seems to be a little trouble with selecting between the B&W and Color cartridges, but I think the B&W may be getting low - anybody know of a utility to check ink levels on this model of HP - D4160?  Anyway, thanks for the good advice wpshooter.

Randy
[http://nocostsoftware.blogspot.com](http://nocostsoftware.blogspot.com)
[http://freebloggingtools.blogspot.com](http://freebloggingtools.blogspot.com)

---

### Post by rossperk on 2008-07-13
> **wrgb2 said:**
> Hi,

I just installed Ubuntu 8.04.  Everything is working except the printer.  Ubuntu installed a text-mode driver for my Lexmark 730 series printer (actual printer is a Z730), but it doesn't work.  When I try to print from an application, nothing happens.  When I try to print a test page from the printer control panel I get the following error:

CUPS server error: There was an error during the CUPS operation: 'client-error-document-format-not-supported'

Can someone help, please?

Randy
[http://nocostsoftware.blogspot.com](http://nocostsoftware.blogspot.com)
[http://freebloggingtools.blogspot.com](http://freebloggingtools.blogspot.com)

I'm also having the same issue, but with a Canon PIXMA MP160. Under Ubuntu 7.10, it mounted as a MP150, and printed fine, but under Ubuntu 8.04, it shows up as an MP160 (the *actual* model) in the printer configuration, but won't print. That same CUPS error displays when I hit Print Test Page, as well. Any ideas?
(note: I switched hard drive and installed 8.04 to a blank drive, instead of upgrading from 7.10)

---

