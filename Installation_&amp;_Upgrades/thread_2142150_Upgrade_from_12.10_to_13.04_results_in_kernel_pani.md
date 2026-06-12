---
title: "Upgrade from 12.10 to 13.04 results in kernel panic; won't boot"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by dekaru01 on 2013-05-04
Hey,
So I decided to take the plunge today and let Ubuntu update itself to 13.04 (was on 12.10). Everything seemed to go smoothly, all the way up until rebooting after the upgrade. Upon reboot, and every subsequent try after that, I get this:

```
Kernel panic - not syncing: Fatal exception in interrupt
drm_kms_helper: panic occurred, switching back to text console
```

And everything stops there. These above are just the last two lines of text I can see, there are many others above.
I can access Grub.
No idea how to proceed though. Help would be much appreciated.

Thanks.

---

### Post by dino99 on 2013-05-05
try booting with an older kernel (from 12.10)
then be sure to only use 13.04 archives (sudo gedit /etc/apt/sources.list) and maybe comment out ppa(s) in case you have some activated, then update again.
of course, logs are your friends to find usefull warnings/errors (.xsession-errors, xorg.0.log, dmesg)

---

### Post by bogan on 2013-05-05
Hi!, **dekaru01**,

After updating 13.04, I get a similar Kernal Panic and freeze up when I select "Ubuntu" from the grub menu.

But if I press 'Enter' with Advanced Options highlighted, and choose one of the option listed, boot-up proceeds normally.

A nuisance, but worth trying. Don't ask Why?.

Chao!,** bogan.**

---

### Post by doorunrun on 2013-05-05
I seemed to be having a lot of trouble getting my system to boot to 13.04 so I'm trying out kernel 3.9 and so far (about 1 day of usage) my system boot is more stable. I used this as my guide:
[http://www.upubuntu.com/2013/04/installupgrade-to-linux-kernel-39.html]("http://www.upubuntu.com/2013/04/installupgrade-to-linux-kernel-39.html")

My upgrade from 12.10 to 13.04 about a week ago went pretty smoothly and I didn't seem to have boot problems. But, I began to notice more and more start-up as well as power-down hangs. It couldn't figure how to go back to an older kernel so I just tried going forward.

Best of luck; I hope you get your system stable!

---

### Post by dekaru01 on 2013-05-07
Thanks for the ideas everyone. It turns out the culprit was Jupiter, which I had installed in 12.10.
I managed to boot with a kernel from 12.10, uninstalled Jupiter, and then all was fine.

---

