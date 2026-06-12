---
title: "Ubuntu 12.04 Would not install or boot live."
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by bboydp on 2012-04-26
Just wanted to say thanks to people linking where to disable boot options.

Computer:

i7 920 
Asus P6T 
Radeon HD 6950 
6 Gigs Ram

I finally was able to install once I disabled the following two boot options:

noapic
nolapic 

Those two did the trick, so much appreciated to all who have been posting those, as they fixed my issue.

=D>

---

### Post by mendhak on 2012-04-28
> **bboydp said:**
> Just wanted to say thanks to people linking where to disable boot options.

Computer:

i7 920 
Asus P6T 
Radeon HD 6950 
6 Gigs Ram

I finally was able to install once I disabled the following two boot options:

noapic
nolapic 

Those two did the trick, so much appreciated to all who have been posting those, as they fixed my issue.

=D>


Did installing with noapic/noacpi affect the actual installation of 12.04 on your machine?   

I found that the Live USB works only if noapic/noacpi is set, but Live USBs of 11.04 and 11.10 work just fine without those switches.

---

