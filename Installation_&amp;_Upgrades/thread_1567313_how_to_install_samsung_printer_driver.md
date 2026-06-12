---
title: "how to install samsung printer driver"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by hodad on 2010-09-03
I tried following tweedledee's guide, and appreciate the trouble that (he/she?) went thru, but it was just too complicated for me. I tried several of the ideas therein with no luck.  I finally got it working as follows; hopefully this will work for you...

First, I looked for hints from "Log File Viewer" under System-Admin menu. I watched the "lpr-log" while unplugging and plugging the printer USB cable (great troubleshooting tool - the Log Files under Admin!).

1. Add to the the repository  [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) using "System-Admin-Software Sources".  I did get this from Tweedledee's guidance - Thanks!

2.  Open Synaptic Package Manager and download Samsung Unified Driver.

3. You should now have a new folder called "cdroot" in you home directory.

4. Open Terminal, navigate to  the cdroot/Linux subdirectory in your home directory.

5.  Type sudo ./autorun.  This "should" run a configurator that will install the printer drivers.  Note: mine hung up at %95; but I just shut down the pc and restarted it.  I also had trouble choosing the right "port" under the configurator, but it at least installed most of what was needed...

I then found out thru "Log File Viewer's" lpr-log that there was some kind of CUPS problem.  I manually restarted CUPS with the line:

sudo /etc/init.d/cups start.

At this point, the printer was recognized! 

7. Use Synaptic to install Samba (needed for CUPS to recognize the printer - got this from another thread).

8. Now the printer should work - or at least this should get you pretty close!

Good luck (you'll need it if my experience was any guide!)):P

---

