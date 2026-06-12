---
title: "how to change repository from InRelease to Release"
date: 2018-10-21
forum: Installation &amp; Upgrades
---

### Post by soldier3 on 2018-10-21
I am install lubuntu 18.10 beta. How to update to lubuntu 18.10 final.
When sudo apt updeta =>
i get.
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security InRelease 
http:// ... InRelease 
http:// ... InRelease

how to change repository to Release
 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security Release

---

### Post by oldos2er on 2018-10-21
Support, not chat, so moved to Installation & Upgrades.

To fully update run ```
sudo apt update && sudo apt full-upgrade
``` There's no need to change your sources.list.

---

