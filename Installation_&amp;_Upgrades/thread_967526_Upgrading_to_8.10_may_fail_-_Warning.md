---
title: "Upgrading to 8.10 may fail - Warning"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by Muflon on 2008-11-02
Hi

This is a warning to anyone who is thinking of upgrading to 8.10. This doesn't apply if you are doing a clean/new install.

I and several other users have experienced a problem when upgrading from 8.04 to 8.10 that has left Ubuntu in a very sorry state.

[http://ubuntuforums.org/showthread.php?t=963774](http://ubuntuforums.org/showthread.php?t=963774)

What appears to happen is that the upgrade doesn't install the new kernel or many of the new packages but instead removes several hundred packages that you would quite like to use (firefox, pidgin, network manager, and evolution).  You are left with the old kernel and a PC that won't boot.

[http://ubuntuforums.org/showpost.php?p=6079202&postcount=49](http://ubuntuforums.org/showpost.php?p=6079202&postcount=49)

There is a fix for this:

[http://ubuntuforums.org/showpost.php?p=6079837&postcount=63](http://ubuntuforums.org/showpost.php?p=6079837&postcount=63)

You may need to then reinstall (apt) some of your applications/packages to get them to work.

Obviously this doesn't effect everyone and many users have upgraded successfully.  Unfortunately I don't know what the common link is between the users that have experienced this problem, so I can't advise you if it will happen to you.

By they way I am writing this message in 8.10 and I thoroughly recommend it.

Muflon

---

