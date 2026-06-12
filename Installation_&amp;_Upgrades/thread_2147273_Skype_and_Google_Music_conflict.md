---
title: "Skype and Google Music conflict"
date: 2013-05-21
forum: Installation &amp; Upgrades
---

### Post by Ratscallion on 2013-05-21
I don't think this has been posted previously, so apologies if it has.
[B]Ubuntu 13.04
64-bit
All packages latest version
[/B]So I installed Skype on Ubuntu 13.04; then I went to install Google Music shortly afterwards. There appears to be some kind of conflict in verisons of dependent libraries or some jazz like that, as the two cannot be installed side by side.
It worked perfectly fine in 12.10, so I'm presuming something has changed from either one version to another, or either of the applications has received an update, resulting in some library conflicts.

Anyone else having a similar problem and, if so, did you find a fix?
Cheers.

---

### Post by gordintoronto on 2013-05-21
What was the error message? I can't recreate the problem, because Google has not made Music available in Canada.

---

### Post by Ratscallion on 2013-05-24
> **gordintoronto said:**
> What was the error message? I can't recreate the problem, because Google has not made Music available in Canada.

I just uninstalled Skype and went to install Google Music first. That installs fine, but then Skype gives dependency issues.
It appears as though one package requires a library to be one version while another requires it to be a different version. 
Skype requires libssl1.0.0:1386.
Oddly, whether something has changed in the last two days, doing Google Music first *then*Skype results in a perfectly fine install for both applications.

---

