---
title: "BIOS Error: Forced Boot into Windows."
date: 2015-02-22
forum: Installation &amp; Upgrades
---

### Post by Bobby_James on 2015-02-22
This is not strictly an installation thread but I've noticed there are a number of BIOS or UEFI related questions in this subforum so I hope it's OK if I post. 

I had a weird experience with my 12.04 system.

I accidentally let the battery die and the Samsung Ultrabook closed down. For some reason, on startup, it booted into Windows 8 rather than into Ubuntu which is the default.

I exited Windows, pressed F2 and went into the boot menu. Weirdly, the "Secure Boot" was "Enabled". This meant that I could only boot into Windows (UEFI). It took me a while to realise that by disabling "Secure Boot", I was able to select CSM OS and hence could boot into Ubuntu as normal.

Also, the BIOS clock went back to January 15 2015 at an incorrect time.

Does anyone have any ideas how this could have happened?  Thanks!

---

### Post by oldfred on 2015-02-22
Sounds like system battery may be low. If system battery on motherboard is not working, then system reverts to all its defaults. That has happen to me on very old system. Usually that battery is good for about 5 years, but maybe newer systems use more?

But I thought UEFI had NVRAM to save settings, so at least some UEFI settings should not have changed.

---

### Post by Bobby_James on 2015-02-23
The laptop is less than two years old. 

When I booted into Windows, I reset the date in Windows but not the time (which was also incorrect). After I had resolved the issue in the BIOS, I went back into Windows. This time the time was also correct.

I'm wondering if the issue could be some kind of rootkit malware. I ran rkhunter and all looked fine. Any thoughts?

Thank you for the answer.

---

### Post by oldfred on 2015-02-23
There are some threads on Windows time & Linux time conflicting.

       [https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)
time, UEFI, windows 8  - several posts by sudodus  
[http://ubuntuforums.org/showthread.php?t=1769482&p=12608648#post12608648](http://ubuntuforums.org/showthread.php?t=1769482&p=12608648#post12608648)

---

