---
title: "Upgraded to 12.04, Software Sources still shows oneiric repositories and not Precise"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by ravisghosh on 2012-05-01
I upgraded ubuntu to 12.04 and ended up with a blank screen of death. Finally, figured out that xorg was not installed and that to install xorg, I have to downgrade xserver-xorg-core. I did that and I am able to log in, however, I don't see any change. The login screen shows 11.10.

On looking into Software Sources, I find the repositories point to Oneiric and not to Precise. However, "lsb_release -a" tells me it is Precise.

Can someone guide as to how to get the Precise repositories and get it properly upgraded.

---

### Post by plucky on 2012-05-01
> **ravisghosh said:**
> I upgraded ubuntu to 12.04 and ended up with a blank screen of death. Finally, figured out that xorg was not installed and that to install xorg, I have to downgrade xserver-xorg-core. I did that and I am able to log in, however, I don't see any change. The login screen shows 11.10.

On looking into Software Sources, I find the repositories point to Oneiric and not to Precise. However, "lsb_release -a" tells me it is Precise.

Can someone guide as to how to get the Precise repositories and get it properly upgraded.

From a terminal ```
sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
```

But I am surprised it managed to do the release upgrade as one of the first things it does is change the sources.list to point to the new repositories.

Good Luck

---

### Post by ravisghosh on 2012-05-02
> **plucky said:**
> From a terminal ```
sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
```

But I am surprised it managed to do the release upgrade as one of the first things it does is change the sources.list to point to the new repositories.

Good Luck


Thanks a lot. It worked.

---

