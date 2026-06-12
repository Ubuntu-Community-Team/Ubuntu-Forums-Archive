---
title: "Installing XP (Ubuntu 9.10 already installed)"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by teachmeifyoucan on 2009-11-17
Hi,

I'm trying to follow the instructions here:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=2](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=2)

The guide informs I should backup this file: /boot/grub/menu.lst

Unfortunately, this file doesn't seem to exist in Ubuntu 9.10 (the guide was written for Ubuntu 8.04).

Where can I find the equivalent file in Ubuntu 9.10?

Is there anything else I need to watch out for?

Thanks!

---

### Post by darkod on 2009-11-17
See this recent thread:
[http://ubuntuforums.org/showthread.php?t=1329264](http://ubuntuforums.org/showthread.php?t=1329264)

It's the same. The file doesn't exist because you are using grub2 which does not work with menu.lst. The link in the thread has precise instructions how to restore grub2 after installing windows.

---

