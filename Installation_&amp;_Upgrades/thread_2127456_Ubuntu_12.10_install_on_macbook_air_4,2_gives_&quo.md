---
title: "Ubuntu 12.10 install on macbook air 4,2 gives &quot;Missing operating system&quot;"
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by negev2013 on 2013-03-20
Hi,

I have a macbook air 4,2 which was set up with boot camp to dual boot windows with MacOS.

Today I created a Ubuntu 12.10 flash drive and using the partition manager deleted the windows partition and created a 4gb swap partition and the rest as a linux root partition, then installed Ubuntu on it.  I rebooted and it booted straight into Ubuntu, so far so good.

Then I decided I didn't want it to boot into Ubuntu every time so I used the option key to get back into MacOS, and selected the mac partition in the startup disk section of the system preferences.  Rebooted and this time it booted straight into macos, still good.

The problem now is if I hold the option key on boot, the only other boot option is "Windows" and if I select that I get "Missing operating system", so I don't have a way to get back into Ubuntu now.  During the installation I installed the bootloader on the linux root partition, should I have installed it on the disk, eg /dev/sda, rather than the specific linux root partition?  The reason i chose the root partition was because I have filevault encryption set up on the MacOS partition and I didn't want to mess with it's bootloader as I thought I might break it.

Any help much appreciated.

Thanks,
neg

---

