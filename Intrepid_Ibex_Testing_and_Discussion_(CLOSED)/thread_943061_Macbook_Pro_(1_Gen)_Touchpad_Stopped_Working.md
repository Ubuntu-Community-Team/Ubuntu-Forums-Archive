---
title: "Macbook Pro (1 Gen) Touchpad Stopped Working"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by flakzeus on 2008-10-09
I just did an update on my Macbook Pro 1st Gen and rebooted, when it came back my touchpad did not work. Any ideas?

```

Linux Zion 2.6.27-6-generic #1 SMP Tue Oct 7 04:15:04 UTC 2008 i686 GNU/Linux

```

---

### Post by wgrant on 2008-10-09
Update meaning to or within Intrepid?

Do you have any InputDevice sections in your xorg.conf? If so, remove them and reboot.

---

### Post by flakzeus on 2008-10-09
Thanks, it was the InputDevice in the xorg.conf file. I was trying to get my touchpad to work like it did in OSX. Not sure how to do t hat in Intrepid now.

Thanks again.

---

### Post by wgrant on 2008-10-10
> **flakzeus said:**
> Thanks, it was the InputDevice in the xorg.conf file. I was trying to get my touchpad to work like it did in OSX. Not sure how to do t hat in Intrepid now.

Thanks again.

Thanks for confirming that that works. We're teaching the upgrade tool to automatically remove such sections, as they generally now cause more harm than good.

For configuring the touchpad, see the Input Configuration section of [this wiki page](https://wiki.ubuntu.com/X/Config).

---

