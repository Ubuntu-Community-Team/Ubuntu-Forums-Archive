---
title: "Prompt for network settings in preseeded install"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by sgifford on 2012-02-25
Hello,

I'm working on a preseed configuration for a network that does not have a DHCP server.

I'd like the installer to ask me for the network settings, then use those settings to retrieve the preseed file from a URL and automate the rest of the configuration.  I can't figure out how to get it working though.

If I boot with "auto=true url=http://.../install.txt", it will only ask questions with priority of critical, so skips over the network settings.  If I choose a lower priority, then the installation is cluttered with unimportant questions.  I don't seem to be able to specify that it asks non-critical questions only until it gets the preseed file, or to be able to tell it to ask only critical questions except for a few specific ones.

Has anybody done this and can help point me in the right direction?

Thanks!

------Scott.

---

