---
title: "UbuntuStudio won't finish loading ontop of new Cd install of 9.04"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by TBerk on 2009-04-06
After (re, re, re) configuring trying to fix and or investigate No Audigy2 Sound in 9.04 beta I scrubbed and repartitioned and reinstalled from my CD. 

 1st thing I did next was to open Synaptics Package manager and while web browsing in the foreground I downloaded Ubuntu-Studio in the background.

It didn't finish loading the files, instead I got the following error:

> 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


So, I reported it to Launchpad then I went and ran:

```
$ sudo dpkg --configure -a
```

This is what I gave back...

>  
Setting up libc6 (2.9-4ubuntu5) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135


The same loop happens now when I open Add/Remove apps or synaptics and refresh the list.

TBerk

- append;  running up against a repository/package problem I couldn't reset easily I re-ran 9.04 beta setup from CD, effectively wiping out the Studio install I had done.

I next 'Mark All Upgrades' and applied them. Rebooted.

I may have caused my trouble in the 1st place by adding an incompatible repository.

---

