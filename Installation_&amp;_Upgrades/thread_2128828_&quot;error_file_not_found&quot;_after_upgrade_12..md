---
title: "&quot;error: file not found&quot; after upgrade 12.04 --&gt; 12.10"
date: 2013-03-24
forum: Installation &amp; Upgrades
---

### Post by SanA333 on 2013-03-24
I've just upgraded to 12.10 (64 bits). Whenever I start my computer, I briefly see the message "error: file not found" 3 times, just before the Grubs appears. 
```

error: file not found
error: file not found
error: file not found
```
The message last only a couple of milliseconds then the Grubs appears. Ubuntu seems to work fine

I have a dual boot with Windows 8

Any idea about what's going on?

Cheers!

---

### Post by larryvc on 2013-03-24
I have the same issue and haven't found anything in the logs to indicate what files were not found.  I am running Ubuntu in VirtualBox on a Windows 8 host.  Ubuntu boots and works fine.

Searching the forum did not help as most "Error:file not found" posts for upgrade from 12.04 to 12.10 were in regard to grub boot problems.  That is not the case here.

Hopefully somebody has some ideas or the answer.

---

### Post by larryvc on 2013-03-24
The solution was to reinstall Grub2.

 [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

I still do not know what files were not found though.

---

### Post by SanA333 on 2013-03-25
Nice!
I will try that tonight

edit - Seems like it's working, thanks :)

---

