---
title: "ATi driver problem"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by shaydn on 2011-04-05
hi i have an Ati x1100 grapics card and i was wondering how to install the driver for it. i went to ATi's website i downloaded the x1100 driver and put it in the terminal (.run file) but it didn't seem to work.
does any one have any suggestions?
i used the restricted drivers program but nothing showed up except for a modem???? =0


i am unsure if this is the right place to post this thread sorry in advance! =)
PLEASE HELP ME!!!!

Specs:
Intel Pentium 1.73 ghz
Ati Xpress 1100
1024 mb ram
Ubuntu 10.10 maverick

---

### Post by ajgreeny on 2011-04-05
I don't think there is an ATI driver for that card any more; you will have to use the open source driver that came when you installed Ubuntu.

That driver works quite well for some cards, including my old 9200SE, but not so good for others, perhaps including yours, though the driver is getting better as versions move forward, and you may get good support with it in future.

For now I don't think there is anything you can do.

---

### Post by Mark Phelps on 2011-04-05
ajgreeny is correct -- there is no fglrx driver that will work with that card and recent versions of Ubuntu.  ATI dropped Linux driver support for that card years ago.

The open-source driver is installed by default when you first setup Ubuntu.  That is the only driver available now.

---

### Post by shaydn on 2011-04-05
Thanks for the information! 

is there any way to achieve Compiz effects  with the open source driver?
what versions of Ubuntu support the Ati x1100 driver?

---

### Post by Darren Sparrow on 2011-04-05
I hope this page helps you some what. 

[http://wiki.compiz.org/ATI%20with%20AIGLX](http://wiki.compiz.org/ATI%20with%20AIGLX)

I use a Radeon HD2400 and that still has drivers etc from ATI that work ok, or I just use Ubuntu/Linux drivers instead.


Regards,

Darren.

---

