---
title: "After installing the NVIDIA driver I had a strange incident with linux-modules-extra."
date: 2024-11-26
forum: Installation &amp; Upgrades
---

### Post by yurad on 2024-11-26
I needed to install nvidia-driver-535. After installing and rebooting, I got a black screen instead of the login screen. I changed prime-select to intel in the virtual terminal and then I was able to login to Gnome. However, network, bluetooth and sound were missing. I realized that linux-modules-extra was not installed. The current kernel was linux-image-5.15.0-125-generic. I found the package linux-modules-extra-5.15.0-125-generic_5.15.0-125.135_amd64.deb in /var/cache/apt/archives/. But before installing linux-modules-extra, I booted with the previous kernel 5.15.0-124-generic to get networking and read on the internet about my problem. Then I booted again with the default kernel 5.15.0-125-generic to install the extra modules. But after booting I found that network, Bluetooth and sound started working, and linux-modules-extra-5.15.0-125 had already been removed from /var/cache/apt/archives/
Can anyone help me figure out what happened to modules-extra-5.15.0-125? 
Why didn't it show up after installing nvidia-driver-535 and rebooting a few times, but it did after booting with the previous kernel?

---

