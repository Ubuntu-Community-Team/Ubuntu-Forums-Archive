---
title: "Lost control of GRUB to Kubuntu during updates"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by JimmyJeremiah on 2010-01-07
Sorry if this has been answered somewhere but I can't find it.

I have a quad boot setup on my Toshiba:
Vista, moonOS 3, Ubuntu 9.10, Kubuntu 9.10.
All are 64 bit except for Vista which is 32.

Ubuntu is my main OS and Kubuntu is simply for guests. I had my GRUB entries configured the way I wanted and everything was great. Also, everything was up to date except for Kubuntu because, as it was for guests, I hadn't used it. After I went in to do the updates it took control of GRUB. I don't want to configure GRUB from Kubuntu since I won't really use it, therefore I need a way to get control back in Ubuntu.

Will I have to just restore GRUB with a live USB even though it's not really broken?

Thanks!

---

### Post by JimmyJeremiah on 2010-01-08
I found my solution!

Title: How to restore the Ubuntu grub bootloader (9.10 and beyond)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

And for anyone else with this problem. Be sure to install grub on only one OS when doing a multiboot. I originally thought that I had to install my main OS last so it would be in control of grub, but we just need to install grub once (and possibly run "update-grub" later).

---

