---
title: "Upgrades for 12.04 on Feb 6, 2014"
date: 2014-02-07
forum: Installation &amp; Upgrades
---

### Post by bigmatlem on 2014-02-07
OK I stupidly just allowed my system to just download and install todays updates without looking at them  Now my screen is all messed up and if I knew what they were I'd get rid of them.  

I have an HD monitor at 1080p running an ATI chip which worked great up until today.  Now the monitor has no edges.  They are off screen.  I down graded the resolution to 720 no help, I put it in vga mode made it worse.

I remember one of them being a chrome install don't know if it was a browser chrome or other.  NEED HELP!  I'm back to my old monitor and while it was good compared to what I have it really sucks.

---

### Post by Dennis N on 2014-02-07
You can find out what was done from the log files. **dpkg.log**  in /var/log contains a record of what happened by date and time.

---

### Post by bigmatlem on 2014-02-10
Found the issue and corrected it.  During the last update the system somehow corrupted the catalyst for ATI and wiped out all settings.  I went to ATI and downloaded their driver for it rather than hoping Ubuntu would see the graphics adapter.  Installing their software cleared up the issue.  It installed a new version of jockey-gtk 0.9.7-0ubuntu7.13 which messed everything up.

---

### Post by bigmatlem on 2014-02-10
For the ATI card users out there watch out for the new version of jockey-gtk it has a problem.

---

