---
title: "Android SDK on Ubuntu"
date: 2015-10-28
forum: Installation &amp; Upgrades
---

### Post by lubox2 on 2015-10-28
Hello,

I followed this instructively description about Android SDK on Ubuntu [https://help.ubuntu.com/community/AndroidSDK](https://help.ubuntu.com/community/AndroidSDK)

But in the section "Downloading the SDK platform tools" I dont know what exactly  of the packages do I need, if I need only ADB and fastboot to do an installation of Cyanogenmod on my smartphone from my laptop with Ubuntu.

Thank you.

---

### Post by mystics on 2015-10-28
If all you want to do is install adb and fastboot, just type the following commands into a terminal:

```

sudo add-apt-repository ppa:phablet-team/tools
sudo apt-get update
sudo apt-get install android-tools-adb android-tools-fastboot

```

You don't need to get them from the Android SDK.

---

