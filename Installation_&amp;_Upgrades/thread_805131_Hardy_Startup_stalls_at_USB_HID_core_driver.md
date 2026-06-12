---
title: "Hardy Startup stalls at USB HID core driver"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by Hagar Delest on 2008-05-23
Hi All,

I'm trying Hardy on a separate partition (running Dapper usually). But at startup, I've to wait few minutes when the system comes to:
/build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

Any idea? I've searched the forum and the web without any luck.
TIA.

Edit: just noticed that some had issues due to the lines following the one mentioned above:
Clocksource tsc unstable (delta = -552004619 ns)
Time: acpi_pm clocksource has been installed.
But even with the clocksource=hpet or the acpi=off parameters in the boot command line, no way.

---

### Post by saravanan.2407 on 2011-12-30
I am facing similar problem. I am trying to boot live Kubuntu 11.10 from my Transcend 16GB USB drive. It starts booting the live image and it gets stuck at USB HID core driver. I am facing same problem with Fedora 16 as well. Looks like some problem with USB booting. I don't have a DVD drive to try the image with CD/DVD.

---

### Post by Hagar Delest on 2012-01-01
Well, that's an old post and I don't remember if there was even a fix...
If I had found one, I would have posted it here.

I think it was linked to a specific hardware in my laptop but I changed my machine since. Until that, I think I had to put up with it.

---

### Post by saravanan.2407 on 2012-01-02
^ Thanks for the reply. 
Let me post this problem as a new post with all screenshots once I reach home. 
My PC has brand new hardware Intel core i5, Intel H67 M/B, 8GB RAM. My USB stick is being considered as a "Hard disk drive" in my BIOS instead of a "Removable Drive". I suspect this.

---

