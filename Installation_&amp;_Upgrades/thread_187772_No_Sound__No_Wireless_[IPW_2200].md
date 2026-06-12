---
title: "No Sound / No Wireless [IPW 2200]"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by ninocass on 2006-06-03
Hi all 

I have upgraded from breezy to dapper but im having a few problems when i was installin the update i got  a error saying something about "installArchives()" and a lot of errors about "tetex"

i have no sound when i click the volume i get: 

"No volume control GStreamer plugins and/or devices found."

and my wireless error is:

```

[4294684.538000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294684.538000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294684.538000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294694.538000] ipw2200: ipw-2.3-boot.fw load failed: Reason -2
[4294694.538000] ipw2200: Unable to load firmware: 0xFFFFFFFE
[4294694.538000] ipw2200: failed to register network device
[4294694.539000] ipw2200: probe of 0000:03:03.0 failed with error -5

```

Thanks

Nino

---

### Post by briguy on 2006-06-03
You could try installing the firmware from source at [http://ipw2200.sourceforge.net/]("http://ipw2200.sourceforge.net/")

---

### Post by ninocass on 2006-06-03
imstalled the latest kernal from the synaptic manager and it seems to have done the trick sound and wireless is working, i think i might have messed something up along the way through the upgrade or something

---

### Post by ajaustin on 2006-08-15
Similar experience here.  Kernel 2.6.12-9-386 had everything working on Breezy but after upgrading to Dapper wireless and sound didn't work.  Upgrade kernel to 2.6.15-23-386 and it all works again.

---

