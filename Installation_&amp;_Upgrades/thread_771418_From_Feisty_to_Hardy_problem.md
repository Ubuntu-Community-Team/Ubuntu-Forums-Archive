---
title: "From Feisty to Hardy problem"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by technofossil on 2008-04-27
When trying to upgrade Feisty to 7.04, on the way to Hardy, I get the following message: 

Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release) Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)

I uninstalled Wine thinking that if it wasn't installed, it wouldn't need to be upgraded.  Didn't work.  I reinstalled wine, still no luck.  

Any suggestions would be helpful.

Thanks to all,
Stuart

---

### Post by lemming465 on 2008-04-27
Try taking budgetdedicated.com out of your repository list.  You can either comment it out in /etc/apt/sources.list if you are comfortable with editing text config files, or just uncheck it in Synaptic's repository setting dialog.

---

