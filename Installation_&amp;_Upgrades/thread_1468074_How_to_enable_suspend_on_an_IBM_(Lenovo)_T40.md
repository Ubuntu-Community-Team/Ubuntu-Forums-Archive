---
title: "How to enable suspend on an IBM (Lenovo) T40"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by baekgaard on 2010-05-01
I have an IBM T40 that I upgraded yesterday from 9.10 to 10.04.

The upgrade went pretty smothly, as I used the torrents to d/l the alternate CD and used that for a fast upgrade, thus avoiding the slow servers currently.

However, suspend was no longer working after this; it would suspend alright but was not able to resume, as the radeon graphics driver wasn't able to wake up the card correctly. Sometimes ctl-alt-F1 would allow me to log in and check for error messages, but otherwise a clean boot obviously brings the system back to live.

After a bit of google'ing I found a workaround: Boot with an additional radeon.agpmode=-1 option. This is most easily done by editing /etc/default/grub and make a change as follows:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.agpmode=-1"
```

Remember to run sudo update-grub afterwards, as instructed in the file also! This will take care of the problem and allow it resume properly.

The splash/bootscreen isn't shown correctly, BTW, so in my case, I decided to remove the splash and quiet options too. YMMV.

The ipw2100 driver still fails once in a blue moon during boot/resume with a firmware reload error, as it has done in previous releases, with a resulting temporary loss of network connection. Also, the floppy driver continued to spit out error messages that I got rid of by disabling the floppy in the BIOS.

Other than that it appears to run well, so far :P


... just in case someone else has a similar issue.


-- Per.

---

