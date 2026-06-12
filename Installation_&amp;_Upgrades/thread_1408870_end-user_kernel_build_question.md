---
title: "end-user kernel build question"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2010-02-16
Please don't flame me about posting a kernel build question to these pages. I seek an end-user answer to this situation not a kernel developer answer to a newbie. Specifically, should I care about this problem and what do I need to do about it?

I downloaded the parts to build the [highlight] 2.6.31-19.56 [/highlight] edition of the 32-bit ubuntu karmic kernel.

During the config, I named the string "mumbles" for addition to my kernel version signature. ( I now know I should have used "-mumbles".)

When all was said and done, I got this:
```


user@host:path $ ls
linux-headers-2.6.31.6mumbles_2.6.31.6mumbles-10.00.Custom_i386.deb
linux-image-2.6.31.6mumbles_2.6.31.6mumbles-10.00.Custom_i386.deb
ubuntu-karmic/


```

Notice that the signature **2.6.31...mumbles** appears twice in each package name.

Notice, too, that the signature is corrupted from "2.6.31-19.56" to "2.6.31.6" -- where "-19.56" becomes simply ".6"

Personally, I suspect the fact that the string in error ".6" is a corrupted sub-string of what it should be. Further, I suspect that the corruption stems from the trailing ".56" (an extra final dot) in the correct signature.

When I check my kernel config file, I see this:
```


user@host:path $ grep "2\.6\.31"  .config

# Linux kernel version: 2.6.31.6mumbles
CONFIG_VERSION_SIGNATURE="Ubuntu 2.6.31-19.56-generic-pae"


```

Notice that the remark is corrupt but the SIGNATURE variable is correct. I welcome your suggestions and comments. Any flame is never appreciated.

Thanks,
~~~ 0;-Dan

---

