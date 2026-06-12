---
title: "HELP! Epson Stylus Color 740 mysterious priting problems in Intrepid"
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by metapaso on 2008-10-28
I have Intrepid Ibex installed with full updates as of today, Oct 28

My epson stylus color 740 is simply not printing.

I think it has something to do with the %%BoundingBox and %%Pages errors in the cups_error_log file, but I've wasted half a day on this problem with no solution in sight.

This printer was working a few days ago.
I installed a Samsung proprietary printer driver and as far as I could tell, everything was working fine.

Now, today, the files go into the print queue, they take awhile to process, as though they're being sent to the printer, the error_log shows that the printer has data being written to it, yet nothing actually prints!  It's as though my printer driver were stuck in Simulation mode!  

Things I have already tried:
Uninstalling samsung proprietary driver
Disabling apparmor
reinstalling cups
reinstalling foomatic
adding additional foomatic drivers

I have attached my cups_error_log.

The printer works on my old computer with Hardy.
Any help or thoughts please!

---

### Post by metapaso on 2008-10-28
Well I never.

I must have rebooted a dozen times today and installed and reinstalled all kinds of software, and then I gave up.

Now it seems to be working.

I think I may have specified a PPD from somewhere else, anyway, the primary difference is that I am using this driver:

Epson Stylus Color 740 Foomatic/gutenprint-ijs-simplified.5.2

Instead of: 
Epson Stylus Color Foomatic/stcolor  (and related did not work)

The new driver which is working is using ijsgutenprint somehow.  I hope that helps if anyone else has this problem!

Attached is new error_log from a job that actually printed!

---

