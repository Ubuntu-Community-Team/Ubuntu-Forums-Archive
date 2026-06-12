---
title: "Watermark Icon &quot;AMD Unsupported Hardware&quot;"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2013-01-29
I have had a watermark (semi-transparent) icon on the lower right corner of my screen for some time.  

It first appeared when I tried one of the "Additional Drivers" found by System Settings.  

I recently got the following from AMD : "Please note that this issue has been resolved with our latest CAT 13.1 driver.  http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English"

So I've been waiting for an update including the new drivers.  An update arrived today, but it did NOT fix the problem.  How do I check the version of the drivers in the recent update to make sure they are the right (latest) ones?

But MUCH more importantly, how do I get rid of the #%^$^%& watermark icon?

I've tried all of the Additional Driver options with the following results:
- first one in the list - Works, but exchanged the "Unsupported" icon for a "3D Testing Only (or similar)" icon.
- second one - Works, but has "Unsupported" icon
- third one - "Post Release Updates" - would not complete installation
- using none of them - STILL has "Unsupported" icon

---

### Post by dino99 on 2013-01-29
you probably already have heard about synaptic to check the package version (catalyst), dont you ?

so why not using the genuine ubuntu package ?

---

### Post by RogerDavis on 2013-01-29
I've tried to use the Ubuntu drivers by not using ANY of the "Additional Drivers", but the $^&^&*^&* watermark icon remains.

I think it gets dropped into static ram or something similar and needs something to wipe it out intentionally, otherwise it just sits there forever.

I'm not sure how to use Synaptic to just check versions.  Can you give more details?

---

### Post by RogerDavis on 2013-01-29
This may be fixed!

I used Catalyst to install the post-release updates that wouldn't install from "Additional Drivers", and it worked.  It both installed and removed the $%^&^%&* watermark icon - at least for now.

I couldn't equate the driver info shown in Catalyst to the AMD info, it was totally different.

---

### Post by RogerDavis on 2013-01-29
It's been a day, and all seems to work - no watermark icon!!!

My advice to anyone with this problem would be to:

Use Synaptic to install the driver, DO NOT do it through the "System Settings > Additional Drivers".  There be dragons and bugs there...

---

### Post by EAZ on 2013-03-22
I always download the catalyst from their Linux Support website, which also includes the latest Beta
(which in my case always works best, because i always run Xubuntu Nightly builds)

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

---

