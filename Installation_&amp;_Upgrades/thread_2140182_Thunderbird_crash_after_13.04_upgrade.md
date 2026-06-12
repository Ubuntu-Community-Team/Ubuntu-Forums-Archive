---
title: "Thunderbird crash after 13.04 upgrade"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by avidesh on 2013-04-28
After I upgraded to 13.04, Thunderbird is not working. I get the following error message.
[ATTACH=CONFIG]241942[/ATTACH]

I even tried to re install Thunderbird but no luck.

What could be the reason and how to fix this?

avinash

---

### Post by avidesh on 2013-06-26
Any help on this?

---

### Post by vanadium on 2013-06-27
It could be an issue with your current configuration data, which is from the old version of Thunderbird. Try moving that user configuration out of the way. 

To do that, open nautilus. Find the hidden .thunderbird folder in your home directory, and rename that to for example ".thunderbird_old". When thunderbird is sucessfully started, you know that was the issue.
From what version did you upgade?

---

