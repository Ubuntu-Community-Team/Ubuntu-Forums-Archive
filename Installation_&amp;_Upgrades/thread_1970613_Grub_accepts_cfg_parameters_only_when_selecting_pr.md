---
title: "Grub accepts cfg parameters only when selecting profile - bug?"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by Tomas123 on 2012-05-01
Hello, all,

I'm having an interesting problem. 12.04 server could not recognize graphic mode for my older machine, so I had to go and add nomodeset to the cfg GRUB_CMDLINE_LINUX_DEFAULT (and "sudo update-grub" at the end).

If I just reboot and let it go on it's own, ubuntu boots with wrong graphic mode (unrecognized characters, etc.) as if there is no nomodeset in cfg.

If I select the default profile in grub menu and click Enter, it boots normally - readable characters - assuming it got the nomodeset parameter.

Did any of you experience something like this? Any ideas?

Thanks!

---

