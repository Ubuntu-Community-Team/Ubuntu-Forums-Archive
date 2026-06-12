---
title: "Firefox issue after 10.04 upgrade"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by sambarusty on 2010-12-21
I have been at a loss to figure out what is wrong with firefox this time.  But I updated to 10.04 because I was two updates behind and now I still have 1 issue I haven't figured out.  It isn't huge, but just annoying.  I can't print from firefox.  I have a wireless printer hp officejet J4680, and get the following error in the messages log. 

Dec 21 20:37:45 burgec-desktop kernel: [168305.449290] type=1503 audit(1292981865.203:52):  operation="exec" pid=8503 parent=8502 profile="/usr/lib/firefox-3.6.13/firefox-*bin" requested_mask=":: x" denied_mask=":: x" fsuid=1000 ouid=0 name="/usr/bin/lpr"  
    
Not sure what the translation for this is.  This is what I get when I try to print from firefox.  Opera works, office works, just doing an lpr command on something I had firefox save to a file works.  So I don't think it is drivers, the update or anything else outside of something again ridiculous firefox doesn't have working yet.  Anyone run into this or know where the patch is.  I haven't been able to find anything.  Have tried purging cups reinstalling.  updating firefox etc.  just nothing hit the target.  Like I said firefox is the only thing not working.  I can print from opera and office.  So it isn't a printer problem as much as it is a firefox issue.

---

### Post by sambarusty on 2010-12-22
Tried removing and reinstalling firefox also, but that didn't resolve the issue either.

---

### Post by sambarusty on 2010-12-22
Guess the answer is just not to use Firefox.  I just haven't been able to find a translation on that error, to determine what steps to take next.

---

### Post by sambarusty on 2010-12-30
Just thought I would bump this and see if anyone else out there knows what the error is indicating.  Thanks in advance.

---

