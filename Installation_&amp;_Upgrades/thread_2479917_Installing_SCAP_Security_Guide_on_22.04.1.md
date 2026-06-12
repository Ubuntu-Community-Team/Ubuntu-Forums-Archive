---
title: "Installing SCAP Security Guide on 22.04.1"
date: 2022-10-12
forum: Installation &amp; Upgrades
---

### Post by omogeorge on 2022-10-12
I am currently unable to install the Open SCAP Security Guide on Ubuntu 22.04.1

I followed the documentation on [http://static.open-scap.org/ssg-guides/ssg-ubuntu2204-guide-index.html](http://static.open-scap.org/ssg-guides/ssg-ubuntu2204-guide-index.html) but it shows a package that can not be installed.

The site that it redirect me to for instructions  ([https://www.open-scap.org/security-policies/scap-security-guide/](https://www.open-scap.org/security-policies/scap-security-guide/)) asks me to perform the install of the following packages for Ubuntu 18.04 or newer.

```
 apt install ssg-base ssg-debderived ssg-debian ssg-nondebian ssg-applications


```

 None of the above packages are available Ubuntu 22.04.1

Is there any way I can get the OpenSCAP Security Guide installed on Ubuntu 22.04.1? Can I just download the artefacts/XML Guides from any source and then use it on the OS?

From my research it was available on 18.04, why has it now been removed?

Any help on this would be appreciated.

---

### Post by TheFu on 2022-10-13
For anything related to SCAP, you should contact SCAP.  Perhaps they weren't ready for 22.04 or they didn't meet Ubuntu standards to be included.

[http://static.open-scap.org/ssg-guides/ssg-ubuntu2204-guide-index.html](http://static.open-scap.org/ssg-guides/ssg-ubuntu2204-guide-index.html) is clear that the 22.04 efforts are DRAFT.  That means pre-alpha.

Considering that the 20.04 SCAP wasn't released until Feb 2022, [https://public.cyber.mil/announcement/disa-releases-ubuntu-v20-04-scap-security-technical-implementation-guide-benchmark/](https://public.cyber.mil/announcement/disa-releases-ubuntu-v20-04-scap-security-technical-implementation-guide-benchmark/) I really don't expect the 22.04 version to be ready for use by normal admins for another year.  
I see updates to the 20.04 STIGs in July 2022, but nothing for 22.04 at all.

> Users who are unable to find and download the benchmark or other content can report their issue to the Cyber Exchange web team at [email]dod.cyberexchange@mail.mil[/email]. Individuals who have further questions related to STIG content should email the DISA STIG customer support desk at [email]disa.stig_spt@mail.mil[/email].
Have you contacted them? What did they say?  I suspect they will say to join the STIG email lists to stay informed.

Canonical isn't the team pushing this project, but if you like, you can open a bug report in Landscape to get their take on the packages.

---

