---
title: "Any lubuntu cloud image available?"
date: 2017-06-10
forum: Installation &amp; Upgrades
---

### Post by blsaws on 2017-06-10
I'm looking for a very low-weight ubuntu variant to run under OpenStack on a <1G RAM VM (500 MB or less if possible). Lubuntu looks like it is lower-weight than main Ubuntu, but I can't find a cloud image for it, e.g. as found in [https://cloud-images.ubuntu.com/](https://cloud-images.ubuntu.com/).
Any advice as to where to find one, or how to create one?

---

### Post by deadflowr on 2017-06-10
The cloud image is lighter.
Cloud images are server images and server images equal Ubuntu without any desktop.
That automatically makes it lighter than anything that would have a desktop.

---

### Post by ajgreeny on 2017-06-11
You would probably be best served by starting with the [minimal-CD version]("https://help.ubuntu.com/community/Installation/MinimalCD") and adding to that only what you want and need, such as the lxde DE, xorg, and whatever GUI applications you use.

---

