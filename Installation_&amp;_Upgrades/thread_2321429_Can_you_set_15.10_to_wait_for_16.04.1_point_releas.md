---
title: "Can you set 15.10 to wait for 16.04.1 point release?"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by David_Wright on 2016-04-22
As per the title: I'm running 15.10 and (as it is working perfectly) am inclined to wait for the first point release.  Is there any way to set it only to prompt me to upgrade at the point release (ie as if it was 14.04LTS)?

If the answer is simply "no", that's fine.

Thanks 
David

---

### Post by grahammechanical on 2016-04-22
Well, it certainly won't upgrade to 16.04 on its own. And the 16.04 release notes say this:

> 14.04 LTS to LTS upgrades will be enabled with the 16.04.1 LTS point release, in approximately 3 months time.

So, you should not be getting a prompt at this time. What is the setting in System Settings>Software & Updates>Updates tab? If "Notify me of a new Ubuntu version"  is set to "For any new version" that might be the reason you are being prompted. Try changing it to "For long-term support versions." Or even "Never." and then change the setting again when you want to upgrade.

Regards

---

### Post by Impavidus on 2016-04-22
I just checked: if you set 15.10 to prompt for upgrade to LTS releases only, it won't offer the upgrade yet. Keep in mind though that there's only a very short time between the release of 16.04.1 and end of support for 15.10, so you'll have a short time window for the upgrade if you wait.

---

