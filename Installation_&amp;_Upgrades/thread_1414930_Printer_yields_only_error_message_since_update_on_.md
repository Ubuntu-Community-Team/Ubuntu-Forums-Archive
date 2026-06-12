---
title: "Printer yields only error message since update on Feb 23"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by rewyllys on 2010-02-24
Sometime during the morning of Feb 23, 2010, I accepted Update Manager's updates on both my desktop and my laptop, both of which are running Karmic and both of which have been regularly updated by Update Manager.

Before the updates, which I think I saw included an update to CUPS, my Brother MFC-8820D printer had been running satisfactorily. Since the updates, all the printer yields, in response to my attempts to print from either my desktop or my laptop, is the following six lines:

ERROR NAME;
configurationerror
COMMAND;
setpagedevice
OPERAND STACK;
--dicttype---

Any suggestions will be greatly appreciated. Assuming I'm correct that CUPS was updated on Feb 23, is there some way to find out what the latest CUPS update involved, and/or how to return to a prior version?

---

### Post by bumanie on 2010-02-24
Once had a similar problem (not the exact same error output) with a HP printer - I uninstalled the printer and then reinstalled it by letting ubuntu search for the printer and then drivers without any user input. The printer now works fine. Can't promise it will work in your situation, but might be worth a try.

---

### Post by rewyllys on 2010-02-24
> **bumanie said:**
> . . . I uninstalled the printer and then reinstalled it by letting ubuntu search for the printer and then drivers without any user input. The printer now works fine. . . . . might be worth a try.

Many, many thanks!:popcorn:

Your suggestion worked like a charm!  On both my machines, and only took about 2 minutes each.

Now my problem is:  Why couldn't I have thought of this?:(

---

