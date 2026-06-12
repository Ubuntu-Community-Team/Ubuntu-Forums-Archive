---
title: "cupsd broken in ubuntu 16.10"
date: 2016-10-20
forum: Installation &amp; Upgrades
---

### Post by mcarro on 2016-10-20
I have upgraded from 16.04 to 16.10.  The upgrade went smooth.  But it turns out that cupsd breaks when starting.  syslog shows the error

cupsd: malloc.c:2880: mremap_chunk: Assertion `((size + offset) & (GLRO (dl_pagesize) - 1)) == 0' failed

Any workaround?  I would downgrade to the 16.04 version, which worked well, but I am not sure how to do it safely and whether it would work.  


Any help will be appreciated!

Cheers.

---

### Post by Geoffrey_Arndt on 2016-10-21
Perhaps a clone of 16.04 would be one option (am not sure though).   A re-install of 16.04.1 would work though after saving your important data.   There seem to be a lot of reports about broken CUPS, Xsane, and general printer functionality in 16.10.

---

### Post by mcarro on 2016-10-21
Hi.  Thanks for your message.  Yes, 16.04 was working fine, but I wanted to avoid having to go through the hassle of reinstalling 16.04.  I was considering reinstalling 16.10 from scratch (I did an upgrade from 16.04, which went very smooth).  I didn't find reports about CUPS being broken,  but I was likely not searching well.  Today I run into problems with the HDMI external display.

---

### Post by Geoffrey_Arndt on 2016-10-21
After spending many years in IT for a couple major companies, the Cardinal rule was to ensure stability and security.   That's why I prefer to run the LTS versions, and if I want to go with the interim releases, it would only be installed on a test PC or an external usbv3 ssd (full install, not Live or Persistent Live OS).   But each person should decide how to run their own systems based on their own needs.   Over the years, I've seen one too many "regressions" . . .

---

### Post by monkeybrain20122 on 2016-10-21
If something is working, why rush to upgrade? 16.10 is out not even a month and you would expect there are bugs and breakage. There is no sensible reason to trade in a LTS which is barely 6 month old and is working for an unknown interim right after it is released. I have 16.10 installed on an external hard drive but just for testing, already I found things that are working perfectly in 16.04 that doesn't work or take a bit of tweaking to work in 16.10 and my testing has been very limited.

---

### Post by mcarro on 2016-10-22
Hi.  Thanks for your recommendations.  Yes, I'm aware that jumping onto a new release can always bring unstability.  I guess I'm kind of eager to see "what's new" even if there is not much new.  But once I stumble upon a problem, I don't mind helping others triage and solve it.  However, if it's been already solved, then I can just test and eventually adopt that solution.  That doesn't seem to be the case now, so I guess I'll be heading to launchpad.  

Best.

---

