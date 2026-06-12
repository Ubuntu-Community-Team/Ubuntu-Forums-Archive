---
title: "Updates failing.."
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by toasty_ghosty on 2008-10-29
Hello

I went to update my machine today to notice that it is failing to download the package information. Most of the packages that seem to fail are "Translation-en_US" files. Still, there are many others that fail. Any reason? I am on 8.04.1 btw.

Thanks

---

### Post by cariboo on 2008-10-30
Try a different serve, I get the same thing that the translation lists don't load. To change the server you download from go to System-->Administration-->Software Sources and change the download from  to Main or select other then click the best server button.

Jim

---

### Post by toasty_ghosty on 2008-10-30
> W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/Release.gpg](http://wine.budgetdedicated.com/apt/dists/hardy/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184), connection timed out

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/hardy/main/i18n/Translation-en_US.bz2)  Unable to connect to wine.budgetdedicated.com http:

W: Failed to fetch [http://playonlinux.botux.net/dists/hardy/Release.gpg](http://playonlinux.botux.net/dists/hardy/Release.gpg)  Could not resolve 'playonlinux.botux.net'

W: Failed to fetch [http://playonlinux.botux.net/dists/hardy/main/i18n/Translation-en_US.bz2](http://playonlinux.botux.net/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'playonlinux.botux.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.

This is what I get as far as errors go. Even if I change the server.

---

### Post by Partyboi2 on 2008-10-30
If you are not using these repo's you could disable them in your sources.list or from Software Sources.

---

