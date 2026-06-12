---
title: "No syslinux configuration file found"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by Dark_Neo on 2011-04-02
When trying to boot a USB disk image of either 10.10 or 10.04 I get an error saying that no syslinux configuration file could be found and "syslinux error: No DEFAULT or UI configuration directive found.".

The USB disk was created using the Startup Disk Creator on Maverick.

I'm guessing the second error is just caused by the first, since the syslinux.conf definitely isn't there. Thing is, I've used the 10.04 image before and it's worked fine, so I'm starting to think it's the Startup Disk Creator that's at fault.

Any ideas?

---

### Post by Dutch70 on 2011-04-02
> **Dark_Neo said:**
> When trying to boot a USB disk image of either 10.10 or 10.04 I get an error saying that no syslinux configuration file could be found and "syslinux error: No DEFAULT or UI configuration directive found.".

The USB disk was created using the Startup Disk Creator on Maverick.

I'm guessing the second error is just caused by the first, since the syslinux.conf definitely isn't there. Thing is, I've used the 10.04 image before and it's worked fine, so I'm starting to think it's the Startup Disk Creator that's at fault.

Any ideas?

There is a bug in 10.10 with some usb sticks, but it should work in 10.04. 
Have you checked the md5sum to make sure the download is ok?
[[COLOR="Red"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

 I think there are some issues with Maverick creating a usb for Lucid.
If you think it's Startup Disk Creator at fault, use [[COLOR="Red"]Unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/")

---

