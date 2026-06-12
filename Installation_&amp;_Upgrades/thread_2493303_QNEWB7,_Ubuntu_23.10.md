---
title: "QNEWB7, Ubuntu 23.10"
date: 2023-12-10
forum: Installation &amp; Upgrades
---

### Post by JohnFDay on 2023-12-10
i've owned Qnewb7 for quite some time (bought it when it was first released...and loved it).  However, I hadn't used it for quite some time and am now trying to install it into Ubuntu 23.10 (which is 64-bit, not 32-bit).

All the "stuff" I loaded before are not usable.  They've been deleted or replaced with other "updated" options...none of which can I locate.
 someone please tell me what packages I need to load that replace the packages needed for 32-bit software to run in the 64-bit mode?

THE ORIGINAL LOAD SAID THESE PACKAGES NEED TO BE LOADED FOR QNEWB7 to operate:
    (1) Microsoft TrueType Core Fonts (I've got them loaded.  This line is A-OK)       (2) libpng12-0.1.2.54-1ubuntu1_i386.deb       CAN NOT LOCATE ANYTHING TO REPLACE THIS ONE...
    (3) ia32-libs  (claims to be replaced by 32libz1...which I have successfully downloaded and installed)      (4) ---AND/OR:   libgtk2.0-0:i386       CAN NOT LOCATE ANYTHING TO REPLACE THIS ONE...

If I can get the replacement packs for the items above, i'm sure I can get qnewb7 running in Ubuntu 23.10 "AT LAST".

Any and all help will be really appreciated. Right now I'm dead in the water.
Best to all,
John F Day

---

### Post by Holger_Gehrke on 2023-12-10
What exactly is "qnewb7" ? The only thing duckduckgo finds when looking for that is "Quick'n Easy Web Builder 7" by Pablo Software. They are on version 10.3 by now and the new version is 64 bit capable. I've tried installing the 30 day trial version and it runs on Ubuntu 22.04 with no visible problems. It's 40 $ and if you're eligible for an upgrade you get a 40% discount.

libpng is on version 1.6 these days (package libpng16-16) and has been for quite a while, so good luck trying to find a version 1.2 that can be installed on a current Ubuntu. The only way I could imagine you could get this is to get the source from sourceforge and compile it yourself and build a .deb-package for it.

GTK 4 is current, GTK 3 is considered the 'old-stable' now, so GTK 2 is not really available anymore.

The only way I could imagine getting something with such out of date dependencies to run would be in an isolated virtual machine running an old version of Ubuntu.

Holger

**Edit:** After a bit of looking I found a download of version 7 on their website in a 'qnewb7.zip'. And that didn't need GTK 2 and was quite happy with libgtk-3-0:i386. So if this is the program you're talking about and you still have your registration code and the email address you used to register it then that would be another option.

---

