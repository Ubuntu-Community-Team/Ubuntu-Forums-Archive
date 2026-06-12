---
title: "Ubuntu 18.04 won't upgrade"
date: 2019-07-16
forum: Installation &amp; Upgrades
---

### Post by workaccount127387921 on 2019-07-16
I want to upgrade Ubuntu 18.04 to 19.04. The steps I've taken are as follows

```

sudo apt update
sudo apt upgrade 
sudo apt dist-upgrade
sudo do-release-upgrade
# Outputs: Checking for a new Ubuntu release
# Please install all available updates for your release before upgrading.

```

I've also updated my laptop's firmware to the latest version and tried after rebooting the laptop. Any ideas?

---

### Post by workaccount127387921 on 2019-07-16
Fixed it by uninstalling an old version of golang which resided next to the newer version. Thanks for your time.

---

### Post by Impavidus on 2019-07-16
Without the output of your commands, there's no way we could have guessed that.

Have you made sure the upgrade brought you to 19.04, not to 18.10? Upgrading 18.04 brings you to the next supported release and 18.10 reaches end of life just about now.

---

