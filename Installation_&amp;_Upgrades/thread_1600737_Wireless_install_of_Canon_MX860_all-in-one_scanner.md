---
title: "Wireless install of Canon MX860 all-in-one scanner?"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by Spinland on 2010-10-19
I've done a ton of searching and all I've found seems geared to having your printer/scanner connected via USB cable in order to get the scanner working.  I have the printer working wirelessly but thus far no go on the scanner.

I've downloaded and installed the scangearmp packages.

I've tried installing the sane package via git according to [this blog]("http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html") but when I try to run configure I see this:

*** mustek_usb2 backend requires pthread library - disabling

and usb isn't listed among the installed backends.  I don't even know whether I need usb because this is wireless, but after compiling I run [FONT=courier new]**scanimage -L **[/FONT]and nothing comes up.  

I'm still a Linux newb, and have learned a ton in the past couple of days, but this one is stumping me.

Can anyone offer some clues/hints/advice?

Thanks in advance!

ETA: this is for Ubuntu 10.10, 64 bit

---

### Post by Spinland on 2010-10-19
Okay, guess I jumped the gun on this one.  The solution was to go out and get the XSane scanner application.  Right "out of the box" it found my scanner on the network and it worked just fine.  I don't know for sure, but I presume I still needed to install the scangear drivers from the European Canon site.

---

