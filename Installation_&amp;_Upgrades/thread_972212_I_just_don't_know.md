---
title: "I just don't know"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by mucmicu on 2008-11-05
Hi there

I was trying to install my epson scanner and after a restart my Ubuntu doesn't start anymore. It stops at 
```

[     6.026671]   init[1]: segfault at d ip b7e15710 sp bfda0e10 error 4 in libc-2.8.90.so[b7dff000+158000]
[     6.027116]   Kernel panic - not syncing: Attempted to kill init!

```

I don't know what I've did wrong. How can I have my Ubuntu in previous state??

...please

---

### Post by ad_267 on 2008-11-05
What did you do to try to install your scanner?

Can you boot into the recovery mode? If not you might be able to boot into the live CD to fix what you've done.

---

### Post by mucmicu on 2008-11-06
> **ad_267 said:**
> What did you do to try to install your scanner?

Can you boot into the recovery mode? If not you might be able to boot into the live CD to fix what you've done.

How can I fix what ive done wrong? I'm a newbie...i don't remember the last error I get.
Ive tried [this]("http://ubuntuforums.org/showpost.php?p=3287406"), but after 
```
sudo dpkg -i iscan_2.3.0-2_i386.deb
``` ive get a message:
```
ldconfig deferred processing now taking place
```
After a search starting from that message i've understand is a bug in Ubuntu 8.10. 

How can i recover my old ubuntu with a live CD?

---

