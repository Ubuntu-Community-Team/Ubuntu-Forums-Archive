---
title: "update-manager doesn't ask for password and fails"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by marcushall42 on 2011-05-03
I have a mythbuntu system that has been updated to 11.04 and whenever I run the update-manager directly, it shows any updates that are currently pending, but when I click on the "Install Updates" button, nothing happens.

If I run "sudo update-manager", then sudo asks for my password (as expected), and update-manager is able to perform the update normally.

I was thinking that I must have lost something in a configuration file, so I did a fresh install of 11.04 mythbuntu in a virtual machine as a test.  So I was surprised to find the same behavior in the fresh install!  But, on another machine that runs stock ubuntu, I updated to 11.04 and update-manager functions correctly there..

I did find the file '/usr/share/pyshared/UpdateManager/UpdateManager.py', and it looks like there may be a backend process that may supply an "authorized" flag, but I didn't see anything there that seems to control whether to try to escalate permissions if it is not run as root...  I did run update-manager under strace and it looked like it was sending some messages over DBus that may be significant, but nothing obviously indicating what is going on..

So, is there anything anywhere that documents the overall design of the update-manager program?  In particular, is there any configuration that decides when it needs to ask for root permissions?

Thanks!

marcus hall
[email]marcus@tuells.org[/email]

---

