---
title: "Disabled on upgrade to wily"
date: 2015-10-30
forum: Installation &amp; Upgrades
---

### Post by zkab on 2015-10-30
I upgraded Ubuntu desktop 15.04 -> 15.10 with 'do-release-upgrade' ... and it went OK.
But after the upgrade there are a bunch of software that have been 'disabled on upgrade to wily' in the repository (Software & Updates/Other Software).
In Updates I have enabled:

* Important security updates (wily-security)
* Recommended updates (wily-updates)

Will the disabled software be enabled automatically when they are supported by 15.10 or do I have to do something manually ?

---

### Post by ian-weisser on 2015-10-30
Your older PPAs and non-Ubuntu sources are, of course, invalid now. They are incompatible with your upgraded system.
Your system has no way to discover non-Ubuntu sources for the new release, nor can it judge if you want those non-Ubuntu sources in your upgraded system.

You must manually add anew any PPAs and other non-Ubuntu sources that you wish for your upgraded system.

---

### Post by zkab on 2015-10-30
Thanks - most of the PPAs were unchanged ...
So I marked/enabled the software (in Software & Updates/Other Software) that were disabled and after a reload & sudo apt-get update & sudo apt-get dist-upgrade it picked up the compatible versions.

---

