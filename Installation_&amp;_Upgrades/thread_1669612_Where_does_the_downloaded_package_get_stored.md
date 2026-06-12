---
title: "Where does the downloaded package get stored?"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by Holmes.Sherlock on 2011-01-18
I'm new to Ubuntu. I've installed Ubuntu 10.10 Netbook edition on my laptop recently. It happened that for some reason I had to issue the "patch" command where I found it missing. After some googling, I discovered that it can be installed bu ```
sudo apt-get install patch
```. It worked. Now, my question is  - I run a poor Internet connection where it's impossible for me to download the same package again & again. I want to collect the downloaded package for future so that if I reinstall the OS, I don't need to download it again & again. Can anybody tell me where does the **apt-get** command store packages & how can they be locally installed?

---

### Post by adeee on 2011-01-18
the downloaded files are stored in the folder /var/cache/apt/archives. They are stored .deb files.

---

