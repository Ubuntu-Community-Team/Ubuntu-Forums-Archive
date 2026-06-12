---
title: "synaptic hangs"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by vinfred on 2006-06-08
When trying to apply modification of network settings in synaptic, synaptic hangs for ever using 100% CPU

see [http://www.ubuntuforums.org/showthread.php?t=191965](http://www.ubuntuforums.org/showthread.php?t=191965)
for how I did upgrade to dapper.

May be some files incorrectly cleaned during upgrade process ?

Any clue ?

---

### Post by lkagan on 2006-06-08
Have you looked at any of your log files to see if you can get a clue there?

Larry

---

### Post by vinfred on 2006-06-08
> Have you looked at any of your log files to see if you can get a clue there?

Where should I look for log files ?

---

### Post by lkagan on 2006-06-08
/home/<username>/.xsession-errors
/var/log/debug 
/var/log/dmesg 
/var/log/kern.log 
/var/log/messages 
/var/log/user.log 
/var/log/Xorg.0.log

---

### Post by vinfred on 2006-06-12
I didn't find anything in the log files you mentionned, But may-be I missed the important information.

Any other idea ?

---

