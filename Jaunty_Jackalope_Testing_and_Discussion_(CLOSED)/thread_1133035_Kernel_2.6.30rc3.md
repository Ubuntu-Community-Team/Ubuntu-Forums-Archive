---
title: "Kernel 2.6.30rc3"
date: 2009-04-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kzip on 2009-04-22
I noticed that RC3 of the 2.6.30 kernel was released today on:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Installed on my Jaunty laptop (IBM Thinkpad T60) and everything works great so far (apart from AppArmour which fails at boot but it failed under 2.6.29 too).

It's damn fast too, my boot time dropped from 22.5 seconds using 2.6.29 to 18.8 seconds (the times are recorded using bootchart) and the system is very snappy :)

---

### Post by cl333r on 2009-04-22
I don't get it, what exactly could be new in the 2.6.30 kernel alone to make such a (big) difference for boot time.

---

### Post by unoodles on 2009-04-22
Nice. Thanks for the heads up.

I don't have bootchart running, boot time seemed about the same to me.
Shutdown time was much faster.

---

### Post by HankB on 2009-04-22
Can you do me a favor and see if it includes the WiFi driver I need (rt2860sta) 
```
find /lib/modules -name rt2860sta.ko
```

thanks,
hank

---

### Post by cl333r on 2009-04-22
> **HankB said:**
> Can you do me a favor and see if it includes the WiFi driver I need (rt2860sta) 
```
find /lib/modules -name rt2860sta.ko
```

thanks,
hank
I installed rc3 and I get:
```

/lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2860/rt2860sta.ko

```

But I'm running 2.6.30, uname -a yields:
```

Linux fox-desktop 2.6.30-020630rc3-generic #020630rc3 SMP Wed Apr 22 13:34:16 UTC 2009 x86_64 GNU/Linux

```

---

### Post by HankB on 2009-04-22
> **cl333r said:**
> I installed rc3 and I get:
```

/lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2860/rt2860sta.ko

```

But I'm running 2.6.30, uname -a yields:
```

Linux fox-desktop 2.6.30-020630rc3-generic #020630rc3 SMP Wed Apr 22 13:34:16 UTC 2009 x86_64 GNU/Linux

```
Yes, that's the module from the Jaunty install. 2.6.30RC3 still does not include it. When I googled for this, I found some discussion that indicated that that driver has a license that makes it non-free. There seemed to be some discussion of some mods that could make it acceptable (I thought) but apparently that has not happened.

thanks,
hank

---

### Post by MacUntu on 2009-04-22
It seems to be in staging:

> Ralink 2860 wireless support (RT2860)

type: tristate
prompt: Ralink 2860 wireless support
    dep: STAGING && !STAGING_EXCLUDE_BUILD && PCI && X86 && WLAN_80211

defined at drivers/staging/rt2860/Kconfig:1

This is an experimental driver for the Ralink 2860 wireless chip.


So it should be possible to get it if you build it yourself.

---

### Post by DougieFresh4U on 2009-04-22
I can not get the 'image' to download. Al the others, 'headers' and 'sources' downloaded fine but 'image just hangs when I click it (i386 deb)

---

### Post by Eestlane on 2009-04-22
Works fine for me:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb)

---

### Post by Darkshade on 2009-04-22
Anyone got the Nvidia driver working with rc3? It refused to work with rc2 for me and I ended going back to 2.6.28 which is a shame - .30 was almost twice faster on my machine.

---

### Post by Trespasser on 2009-04-22
Does usplash work on this version? Didn't in 30rc1 and 2.

---

### Post by DougieFresh4U on 2009-04-22
> **Eestlane said:**
> Works fine for me:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb)

This is really ticking me off. I clicked your link and it goes to a blank page and hangs at 'loading'

---

### Post by crjackson on 2009-04-22
> **DougieFresh4U said:**
> This is really ticking me off. I clicked your link and it goes to a blank page and hangs at 'loading'

Really... I click the link and it downloads the deb...

---

### Post by sgosnell on 2009-04-22
Dougie, I think you may have a problem with Firefox or with your internet connection.  

Usplash doesn't seem to work, but at least it boots on my EEE, while the previous rcs wouldn't.  Boot time seems longer than for .29 on my machine.  I'll try it out, but I may not stay with it.

---

### Post by DougieFresh4U on 2009-04-22
I got the headers and the source with out a problem and even the amd64 will download without a problem. but when I click the image i386, it just hangs.

---

### Post by Darkshade on 2009-04-22
Did you try
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/linux-image-2.6.30-020630rc3-generic_2.6.30-020630rc3_i386.deb
```

---

### Post by MacUntu on 2009-04-22
> **Trespasser said:**
> Does usplash work on this version? Didn't in 30rc1 and 2.

Because CONFIG_FB_VESA is not set. It works but not with the builds from the PPA.

---

### Post by DougieFresh4U on 2009-04-22
> **sgosnell said:**
> Dougie, I think you may have a problem with Firefox or with your internet connection.  


How right you are. I was using Swiftfox and I switched to Firefox and all went smooth again. then I had 12 updates and when I went to Swiftfox, it was working ok.
Thanks so much for suggestion/

---

### Post by HankB on 2009-04-23
> **MacUntu said:**
> It seems to be in staging:



So it should be possible to get it if you build it yourself.

Where do I find something in staging? Do I need to download kernel source?

thanks,
hank

---

### Post by Eversmann on 2009-04-23
I have 2.6.30rc3 working on my advent 4211 (using it right now).

If it takes longer to boot, try booting with "profile" added to the kernel boot line once. That way the readahead service will be updated with the current files and confs on the next boot.

---

### Post by Xgen on 2009-04-23
> **Darkshade said:**
> Anyone got the Nvidia driver working with rc3? It refused to work with rc2 for me and I ended going back to 2.6.28 which is a shame - .30 was almost twice faster on my machine.
Using a modified version of the 173 driver, it WFM with rc3.

---

