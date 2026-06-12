---
title: "Thunderbird crash after gutsy install"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by psantangeli on 2007-10-19
After installing Gutsy last night, thunderbird now crashes on me when I go to open an email message in a new windows. I redownloaded/installed the lastest 2.0.0.6 thunderbird from mozilla.org, no joy.

Inspiron 9400, Geforce graphics.

Anyone seen this?

Pete

---

### Post by talon314 on 2007-10-19
After upgrading to Gutsy today, my Thunderbird crashes every time it's launched.

Running from the commandline returns this:

*** glibc detected *** /usr/bin/thunderbird/thunderbird-bin: double free or corruption (out): 0x08f69180 ***

???

---

### Post by Em-Buntu on 2007-10-19
I have a thread here on this also.

Mozilla appears to have some serious problems under Gutsy. It hangs on over 60% of the websites I browse.i'm hear looking for a browser to replace mozilla until this bug is fixed.
There seems to be a problem with Evolution also. When writing a lengthy email, the disk starts thrashing in an endless loop that kills activity on all other tasks. The only way I could get out was to force a quit. Luckily, when I restarted evolution it jumps back to where you quit, saving the text.

What is a good browser to use instead of mozilla on Gutsy?

---

### Post by OnSite511 on 2007-10-21
I'd like to add my 2 cents as well. I performed a fresh install of Gutsy last night and now thunderbird version 2.0.0.6 (20071008)  crashes with a seg fault when I try to read any email.

any help resolving this would be appreciated (at least I have a web interface as a backup)

---

### Post by noobnoob on 2007-10-21
Let me add my voice to the chorus.  After upgrading to 7.10, Thunderbird starts up and I can read mail, but when I try to send mail it core dumps with a segmentation fault.  Tried uninstalling and re-installing thunderbird, no joy.  Anybody have any ideas at all?

---

### Post by Bert_2 on 2007-10-22
I have a fresh installation of gutsy and thunderbird craches every time I receive a new mail. The only way to get things working again is by forcing it off and restarting it (then the mail is sitting there and i can open it without a problem then).

I don't have any idea which thing is causing this problem, I'll try to find it out with the command line I think...

---

### Post by michaelzap on 2007-10-23
Check out this thread: [http://ubuntuforums.org/showthread.php?p=3610310#post3610310](http://ubuntuforums.org/showthread.php?p=3610310#post3610310)

Lightning seems to be the culprit.

---

### Post by Bert_2 on 2007-10-23
I fixed my problems yesterday evening by turning off the pop-up message that Thunderbird displays when I receive a new mail ;)

---

### Post by OnSite511 on 2007-10-23
So there was an update to the lightning, enigmail and reminderfox extensions I had installed. Updating one of them resolved my particular problem, so its very possible that the lightning extension was the cause. check your version. mine is now 0.5 and no seg faulting yet with messages that previously caused them

---

### Post by bipco on 2007-10-26
Had a similar/same problem - appeared to start after some updates. I seem to have fixed it by re-installing Thunderbird (after removing .mozilla-thunderbird from home dir), then replacing all the old stuff from .mozilla-thunderbird until I found something that broke it. Seems compreg.dat was the culprit for me.

Warren

---

