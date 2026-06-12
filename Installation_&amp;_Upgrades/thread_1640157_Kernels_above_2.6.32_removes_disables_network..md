---
title: "Kernels above 2.6.32 removes disables network."
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by smooth_dudes on 2010-12-07
Hello people

When ubuntu 10.10 came out, i upgraded from my 10.04 install. At that point i ran into a problem:
Kernel 2.6.35-22, which is installed by default, apparently does not support my networks card, or at least after i installed i was unable to get on any kind of network. (my card is a ralink RT2860)
So i went ahead and commented out the 2.6.35-22 kernel from my grub.cfg, and thought to myself that this would propably be fixed in a future kernel update.
However i recently installed kernel 2.6.35-23, and yet again no network is available. 
So now i am again back to kernel 2.6.32-25, and i am a little worried that this problem will never be fixed?

Has any of you got any idea as to how i might be able to solve this problem and get my network working? Or maybe if there is a different cause?

Any help is much appreciated.

---

### Post by smooth_dudes on 2010-12-08
bump

---

### Post by smooth_dudes on 2010-12-09
bump

---

### Post by anglican on 2010-12-09
> **smooth_dudes said:**
> Hello people

When ubuntu 10.10 came out, i upgraded from my 10.04 install. At that point i ran into a problem:
Kernel 2.6.35-22, which is installed by default, apparently does not support my networks card, or at least after i installed i was unable to get on any kind of network. (my card is a ralink RT2860)
So i went ahead and commented out the 2.6.35-22 kernel from my grub.cfg, and thought to myself that this would propably be fixed in a future kernel update.
However i recently installed kernel 2.6.35-23, and yet again no network is available. 
So now i am again back to kernel 2.6.32-25, and i am a little worried that this problem will never be fixed?

Has any of you got any idea as to how i might be able to solve this problem and get my network working? Or maybe if there is a different cause?

Any help is much appreciated.I think the answer may be here:

[http://ubuntuforums.org/showthread.php?t=1587107](http://ubuntuforums.org/showthread.php?t=1587107)

H

---

### Post by TBABill on 2010-12-09
I have a RT2860 and I have to ```
sudo gedit /etc/modprobe.d/blacklist.conf
``` and add the following to the end of the file ```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
``` and then I have to ```
sudo gedit /etc/modules
``` and add the following to the end of that file ```
rt2860
rt2860sta
``` Then either restart or modprobe the driver and restart network manager.

---

### Post by smooth_dudes on 2010-12-09
Thank you so much TBABill, that solved my problem :)
Do you know why this is necessary? Why do we have to blacklist some modules apparently related to the driver, and then tell the kernel to load the driver on startup? Or am i misunderstanding something? :o

---

### Post by TBABill on 2010-12-09
It appears we are blacklisting similar drivers for different Ralink chipsets and only using the driver for the proper chipset we have. I suppose the general config just sets up the wrong driver and we have to go back in and tell the system to use the proper driver and ignore the incorrect ones. It's frustrating but I am very glad you are up and running now.

---

