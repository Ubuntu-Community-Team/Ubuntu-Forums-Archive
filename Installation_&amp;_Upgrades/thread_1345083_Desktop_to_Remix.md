---
title: "Desktop to Remix"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by WilliamCobb on 2009-12-03
I have recently installed Desktop 9.10 on my netbook and would actually like to switch to Remix. I am a newbie. Is there a way to do this without reinstalling the whole thing? I tried to do it using the usb drive but it hangs on boot and does not come out.
 
Thanks

---

### Post by raymondh on 2009-12-03
> **WilliamCobb said:**
> I have recently installed Desktop 9.10 on my netbook and would actually like to switch to Remix. I am a newbie. Is there a way to do this without reinstalling the whole thing? I tried to do it using the usb drive but it hangs on boot and does not come out.
 
Thanks

UNR (or 'remix') is in the repos.

1.  Make sure you are updated.  If you want terminal use ...

```
sudo apt-get update
sudo apt-get upgrade
```

2.  Close terminal (if you used it) and access synaptic package manager (system > admin).  Search for ubuntu netbook remix, mark for installation and apply/install.

P.S. Research/peruse the forum for member experiences with UNR vis-a-vis your Ubuntu version.

Regards,

---

