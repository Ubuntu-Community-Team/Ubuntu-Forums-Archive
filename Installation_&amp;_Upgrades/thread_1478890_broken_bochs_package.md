---
title: "broken bochs package?"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by dracayr on 2010-05-10
Hi,

I need bochs for a project of mine. It worked fine for quite a while, until some upgrade happened, and all at once it couldn't find any display librarys: ```
dlopen failed for module 'wx': file not found
```This happens for all the display librarys (wx, x, term, etc.) I'm aware that this is a common error and the normal fix is to install bochs-x. However, bochs-x is installed. A strace showed that bochs is looking for the file libbx_x.la (or libbx_wx.la) in /usr/lib/bochs/plugins. However, the file doesn't exist there. in /usr/lib/bochs/plugins, there's only libbx_x.so. Symlinking this to libbx_x.la doesn't work. So I checked the filelist of bochs-x in it's newest version in the software channel, and indeed: libbx_x.la isn't provided, while it is provided by some older versions of bochs-x. In fact, there is no libbx_x.la on my entire system, or the currently provided packages in the software channels. So I painstakingly uninstalled bochsbios, bochs-x, bochs-wx, bochs-term, and bochs to manually download and install them all in the version 2.3.7-1ubuntu1. _Then_ bochs worked. However, soon after, the update manager popped up, complaining about broken dependencies (reffering to bochs for some reason; there's nothing that depends on bochs). In the update manager, there were also several other updates. So I unchecked bochs, bochs-x, and bochsbios, and updated the rest. but that sh*tty update manager installed bochs in it's newest version even though I unchecked it. Now I'm back to the beginning. I may be able to copy that libbx_x.la from the older version, but I'm not sure if it'll work with the new version (and I don't want to constantly downgrade them, just to have them upgraded again by the update-manager).

It seems to me that the version of bochs in the software channel is broken. Why do they put a broken package into the channel??

dracayr

---

### Post by dracayr on 2010-05-10
So I tried copying the library from the older version to the plugin dir. It didn't work. this sucks :mad:

EDIT: Ok, got it. After a closer look at the output of bochs when running it, and the deb file of bochs 2.4.2, I noticed that a) bochs 2.3.7 is run even though 2.4.2 is supposedly installed, and b) that the deb file replaces only /usr/bin/bochs-bin, but not /usr/sbin/bochs-bin, /usr/local/bin/bochs-bin, and /usr/local/sbin/bochs-bin.
/usr/bin/bochs apparently started one of those remaining older versions of bochs-bin. After deleting those, the correct version of bochs-bin was started, which apparently doesn't need the libbx_x.la file anymore.

---

