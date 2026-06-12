---
title: "Lost Xsane Posting"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by sparks40 on 2008-01-14
I recently did a fresh 7.10 instll. There were 160 upgrades and everything seemed to work as required. However, I did notice that Xsane is now version .991 and the System-config-printer.py is version 0.7.75. The printer dialog setup has also changed. The requested information seemed ok and I was able to print under OO.org without any problems.

My printer is an HP 1200 and I use xsane as a photocopier for documents. It has served me well for over two years. However, it will no longer print the scanned image in the copy mode. I have done the following to try and correct the situation:

1. checked the forum for info on this problem.
2. I tried using the default printer driver for my HP 1200.
3. I then tried to use the gutenprint driver which always worked in the past.
4. I removed and then reinstalled both sane and xsane.

During what use to be the printing phase, I can see the data being moved to my printer, (the printer LED blinks when it is receiving data), but it stops and there is no printed output. The document print window shows that the data is being processed by the computer but it then erases this message even though there was no output to the printer. Irrespective of all of the above changes the printer still works fine when printing Open Office Documents. This leads me to conclude that the problem is definitely with sane/xsane and/or the pipe to the printer. Unfortunately I have run out of ideas.

TNX

---

### Post by jeffus_il on 2008-01-15
Did you have a look at the cups logs?
if not,
try localhost:631 in your browser.
pick the Administration tag, and look at the three logs, access, error, and page, see if anything looks strange ...

Would be best to edit the title of this post to "Printing" and not "Posting"

---

### Post by sanitycheck on 2008-01-16
System:  Kubuntu 7.10 32-bit, HP Laserjet 4050 on network, printing with 4050 PS driver.  XSane is printing to KPrinter (setup as described on XSane website) which I then use to direct job to the 4050.

I, too, had the job disappear using copy mode.  The light would flash on the printer to indicate that it received data, but then the light would go off, and no job printed.  Also, using programs other than XSane I've had problems with painfully slow graphics printing (e.g. 7 minutes to print one reasonably-sized JPG) or I would receive a data error on the printer.

Solution:  in XSane, select Preferences / Setup.  Select the Copy tab.  Uncheck "create zlib compressed postscript image (ps level 3) for printing.  Now my copy jobs print, and they print fast.

As jeffus_il said, please rename the title to aid others trying to find a solution.  Please also add [SOLVED] if this fix works for you. - thanks

---

