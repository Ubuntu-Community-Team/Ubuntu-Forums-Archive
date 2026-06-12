---
title: "interbase.so for php4 in dapper onwards"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by epix_ian on 2006-10-30
I have recently upgraded from 5.10 to 6.06, then to 6.10 and we have also just installed 6.06 on a couple of machines. We use apache1+php4+firebird1.5 but the "php4" interbase.so that comes with 6.06 seems to be actually the php5 library. This caused us some problems - until we simply copied an old php4 interbase.so over the distributed version.

I had a quick scan of the forums but can't see where I can report problems like this - please could someone point me either in the right direction or to a relevent FAQ. 

Apologies if this information was already available, it is a Monday morning and Im new around here...

Thanks,

Ian

---

### Post by epix_ian on 2006-10-30
Why do you always find the answer the moment you post.

Bug 44789 - "php4-interbase package contains php5-interbase" found by searching the bug tracker "https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=interbase.so"

Sorry for the noise,

Ian

---

