---
title: "Problem with sudo."
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by isgie on 2009-11-24
I was planning to install skype today. I downloaded the deb from the website. Earlier, I installed flash using the deb from the flash website.

Instead of running the skype deb, I accidently ran the flash one and now flash is messed up. I do not have flash anymore. Plus, when I try to install something or fix it, I get this error:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

How do I fix this?

---

### Post by aysiu on 2009-11-26
What happens if you paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal)? ```
sudo apt-get -f install && sudo apt-get remove --purge adobe-flashplugin && sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

---

