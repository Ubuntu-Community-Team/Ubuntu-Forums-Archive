---
title: "Ubuntu &quot;Hoary&quot; to Kubuntu &quot;Breezy&quot;: How?"
date: 2005-09-12
forum: Installation &amp; Upgrades
---

### Post by WMCoolmon on 2005-09-12
I've decided I'd like to try and switch to Kubuntu, with the release of Breezy and all. How would I go about doing this via apt, or is it better to 'start fresh' in such a case?

---

### Post by debenham on 2005-09-12
To upgrade from hoary to breezy, change all the lines in your /etc/apt/sources that refer to "hoary" to refer to "breezy"
Then do an 'apt-get dist-upgrade'

Finally to install kubuntu run 'apt-get install kubuntu-desktop'

---

