---
title: "hp pavilion dm1 wireless problems reappear after update"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by jabrilm on 2011-08-29
I installed Ubuntu 10.04 (64-bit) on my HP Pavilion DM1 laptop a couple of days ago. Laptop specs here: [http://www.newegg.ca/Product/Product.aspx?Item=N82E16834157940](http://www.newegg.ca/Product/Product.aspx?Item=N82E16834157940)

This is a dual-boot alongside Windows 7. At first Ubuntu wasn't recognizing my wireless device. I followed the steps in this thread and got it working:

[http://ubuntuforums.org/showthread.php?t=1776880](http://ubuntuforums.org/showthread.php?t=1776880)

Then this morning the Update Manager prompted me to install a bunch of critical updates (many dozens, so I don't remember what they all were). Now when I boot up I am presented with not just Ubuntu and Windows 7 to choose from, but *two different versions* of Ubuntu. It looks like this:

Ubuntu, with Linux 2.6.32-34-generic
Ubuntu, with Linux 2.6.32-34-generic (recovery mode)
Ubuntu, with Linux 2.6.32-33-generic
Ubuntu, with Linux 2.6.32-33-generic (recovery mode)
...
Windows 7 (loader)

If I choose the first Ubuntu (2.6.32-34) then wireless again does not work. If I choose the second (2.6.32-33) then wireless works fine. So I can still use Ubuntu with wireless, but I've got two version of Ubuntu and only one works. Can I delete one of them somehow? Can I get wireless to work on both? Will this happen each time I install critical updates?

Thanks for your help.

---

### Post by wormyblackburny on 2011-08-29
I had the same problem with my DM1. You updated Kernel and the module for your wireless card is not present in the new kernel modules. 

[http://ubuntuforums.org/showthread.php?p=10283670](http://ubuntuforums.org/showthread.php?p=10283670)

---

### Post by jabrilm on 2011-08-29
Which solution ended up working for you? There are several proposed in that thread, with varying degrees of success it sounds like.

Also, every time I upgrade the kernel in the future, will it add a new version of Ubuntu to the bootup screen each time? Is there a way to prevent that?

Okay, I got the wireless working under the new kernel. I basically re-did the last few steps that I had done under the previous kernel:

[http://ubuntuforums.org/showthread.php?t=1776880](http://ubuntuforums.org/showthread.php?t=1776880)

Specifically:

```
$ cp RT5390STA.dat /etc/Wireless/RT5390STA/
$ cp -i os/linux/rt5390sta.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
$ echo rt5390sta >> /etc/modules
$ echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
$ depmod -a
```

I hope I don't have to do this every time the kernel is upgraded.

Speaking of which, I'm curious to hear any responses about multiple Ubuntus appearing at the bootup screen after kernel upgrade. Is this normal? Maybe I should ask that in a new thread.

Ah, this works:

[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

---

