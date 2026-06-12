---
title: "Readahead status 5 error on new kernel 2.6.36"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by mark.altern on 2010-11-17
Hi, guys, 

I just updated to the new 2.6.36 kernel from the Ubuntu kernel ppa, then I start to have the readahead errors during boot: 
```
**ureadahead main process (485) terminated with status 5**
```I add console output into /etc/init/ureadahead.conf, only to find it is a tracing error, no file or directory found, and no more information. 

So is this a bug for the new kernel or readahead, any help is appreciated. 

Thanks a lot.

---

### Post by mark.altern on 2010-11-18
no one with the new 2.6.36 kernel has the same issue? 

I have reinstalled system twice with the same problem. Right after updating the kernel to 2.6.36 from 35, there is no error in the first a few boot, since the /var/lib/ureadahead/pack file is there, which is created before, but after a while, the pack file disappear, and the stutus 5 error comes out. 

I was googling for hours, with a lot of results, but they are not relevent to this issue, which I suspect is related to the new 2.6.36 kernel.

---

### Post by dino99 on 2010-11-18
this package is made to "gain" a few seconds by reading "ahead" the needed packages before they are used. Nothing to worry about :)

sudo dpkg-reconfigure ureadahead

---

### Post by mark.altern on 2010-11-18
Thanks, dino. By the way, I like your picture ;-)

Yeah, I understand what ureadahead is. I am just testing out the new 2.6.36 kernel, and would very much like everything to work fine. dpkg --reconfigure does nothing. 

Are you using the new 2.6.36 kernel? It is decent in many ways. An important one for me is that suspension regression in 2.6.35 was gone, and intel IGP driver was improved. 

Any other suggestions?

The kernel is from:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.36-maverick/")

---

