---
title: "Clean install problems with 20.04 ISO"
date: 2020-04-25
forum: Installation &amp; Upgrades
---

### Post by curts on 2020-04-25
I downloaded the 20.04 ISO this morning and ran into a number of problems trying to install it on my multi-boot PC.

Trial 1: Full package set, download updates, install vendor content, XFS for root partition, mount existing /home partition => install failed almost immediately after clicking the install button on the last setup screen with error ubi-usersetup failed with exit code 141.

Trial 2: Full package set, no updates, install vendor content, XFS for root partition => install completed, but failed to boot up to a login screen after restart.

Trial 3:  Full package set, download updates, no vendor content, XFS for root partition => install failed to complete; opening up the details dialog it looked like it was stuck in a slow loop.

Trial 4: Full package set, no updates, no vendor content, XFS for root partition => install completed and successfully booted up to a login screen after restart.

The 20.04 installer appears to need some more work.

---

### Post by wildmanne39 on 2020-04-25
*Thread moved to **Installation & Upgrades since 20.04 is no longer in development**.*

---

### Post by mörgæs on 2020-04-28
How does it work if you select ext4 for all partitions?

---

### Post by VMC on 2020-04-28
Also, where did you install the ISO; DVD or USB flash? Make sure you allow it to verify ISO sums.

---

### Post by curts on 2020-05-05
Install was made using a DVD copy of the ISO. It was allowed to verify the ISO on each boot-up and all were successful.

---

### Post by curts on 2020-05-15
Trial 5: Full package set, download updates, no vendor content, ext4 for root partition => install completed.

So, the combination of download updates with an XFS root partition has issues.

> **mörgæs said:**
> How does it work if you select ext4 for all partitions?

---

### Post by mörgæs on 2020-05-16
Good, please mark the thread solved.

---

### Post by curts on 2020-05-24
Summarizing results:

Failure #1: mount existing /home partition => install failed almost immediately after clicking the install button on the last setup screen with error ubi-usersetup failed with exit code 141.

Failure #2: install root with XFS format and select the download of either updates or vendor content during install.

---

