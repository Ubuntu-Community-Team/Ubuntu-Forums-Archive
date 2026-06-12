---
title: "Intel Wifi not working on Ubuntu 20.04"
date: 2020-12-14
forum: Installation &amp; Upgrades
---

### Post by afmsouza on 2020-12-14
Hi, I search for a solution on other threads and no lucky for now.

After updating ubuntu from 19.10 to 20.04 (LTS) my Wifi network is not working anymore. I found that iwlmvm kernel module is not being loaded in 5.4 kernel. When I turn back to kernel 5.3 everything is working good.

<OUTPUT ON WORKING KERNEL>
```
$ lsmod | grep iwl
iwlmvm                450560  0
mac80211              794624  1 iwlmvm
iwlwifi               376832  1 iwlmvm
cfg80211              692224  4 wl,iwlmvm,iwlwifi,mac80211
compat                 16384  4 iwlmvm,iwlwifi,mac80211,cfg80211
```
```
$ uname -a
Linux alexandre-Inspiron-5570 5.3.0-18-generic #19-Ubuntu SMP Tue Oct 8 20:14:06 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
lspci | grep -i wire
02:00.0 Network controller: Intel Corporation Wireless 3165 (rev 79)
```
```
$ dkms status
backport-iwlwifi, 8324, 5.3.0-18-generic, x86_64: installed
bcmwl, 6.30.223.271+bdcom, 5.3.0-18-generic, x86_64: installed
oem-wifi-intel-iwlwifi-lp1757035-4.4-dkms, 2.1: added
virtualbox, 6.1.6, 5.3.0-18-generic, x86_64: installed
```
Most of them DKMS modules I've installed in a try to make it work, but before that there are not most of them.

It's missing iwlwifi modules (have not found on 5.4)
```
find /lib/modules -name "iwlwifi*"
/lib/modules/5.3.0-18-generic/updates/dkms/iwlwifi.ko
/lib/modules/5.3.0-18-generic/kernel/drivers/net/wireless/intel/iwlwifi
/lib/modules/5.3.0-18-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
```
How can I generate this module, not compiling kernel manually?

---

### Post by gdesilva on 2020-12-14
Check out the following [https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless.html](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless.html) to see whether you are running the correct version of firmware.

---

### Post by afmsouza on 2020-12-15
problem solved... 
The kernel-headers were missing for new kernel making dkms skip new kernel

Solution:
sudo apt-get install linux-headers-5.4.0-26-generic 
sudo dpkg-reconfigure backport-iwlwifi-dkms
reboot

---

