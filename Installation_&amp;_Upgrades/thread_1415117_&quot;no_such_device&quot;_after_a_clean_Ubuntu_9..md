---
title: "&quot;no such device&quot; after a clean Ubuntu 9.10 install"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by Fafnr on 2010-02-24
Hello all,

I was just given an old IBM Thinkpad laptop, that I'd like to install Ubuntu on.
I got the 9.10 release, burned it, booted it, installed it (default install options - just use entire harddrive, format existing and all that), but I can't boot it.

When I try to boot, after the GRUB menu I just get the following error:

error: no such device: 2ff01019-7c91-45d8-b681-c461d53e7be4
  Failed to boot default entries.

Press any key to continue...

and, if you press any key, it just repeats itself.

I've tried installing both directly (install from the CD boot menu) and via the live-thing (double click on the desktop).
I won't swear the complicated device ID was the same on both occasions, but it is the same error no matter what I do...

Help! :)

Regards,

Søren

---

### Post by kansasnoob on 2010-02-24
This may help:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by Fafnr on 2010-02-24
Cheers - that did it!

---

### Post by trekon86 on 2010-02-24
Same thing happened to me just these last few days. It was a nightmare.
I burned a Jaunty CD, popped it in, installed, rebooted, and what do you know? Worked like a charm;)
PMZ

---

