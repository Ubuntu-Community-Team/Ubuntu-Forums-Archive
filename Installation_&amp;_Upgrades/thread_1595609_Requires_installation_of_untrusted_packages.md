---
title: "Requires installation of untrusted packages"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by badaveil on 2010-10-13
I successfully installed Ver 10.10 but a number of applications from the Ubuntu Software Center e.g. Quantum GIS cannot be installed because I get the "Requires installation of untrusted packages" message.:(

Please advice.

---

### Post by oldos2er on 2010-10-13
The error is caused by not having GPG keys for a particular repository (see [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)), but it shouldn't stop any package installation. Can you run ```
sudo apt-key update && sudo apt-get update && sudo apt-get install qgis
``` in a terminal, and if there are errors post the output here?

---

### Post by badaveil on 2010-10-14
> **oldos2er said:**
> The error is caused by not having GPG keys for a particular repository (see [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)), but it shouldn't stop any package installation. Can you run ```
sudo apt-key update && sudo apt-get update && sudo apt-get install qgis
``` in a terminal, and if there are errors post the output here?

Thank you

Whilst it managed to install the current version 1.4, I was hoping it would have installed the development version 1.5 :biggrin: since there is a mark difference in performance in the 1.5. Well, better a 1.4 than nothing at all.

---

