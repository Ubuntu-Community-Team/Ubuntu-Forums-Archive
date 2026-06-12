---
title: "What to keep in mind with 17.04 to 17.10 upgrade?"
date: 2017-10-27
forum: Installation &amp; Upgrades
---

### Post by russkyca on 2017-10-27
I currently have 17.04 and use Gnome.   I think an upgrade will be fluid/smooth but I'm only speculating since Ubuntu moved to Gnome as their default but I'm wondering if I just follow the instructions out there, should I assume it will be a smooth upgrade process?

I also use the Nvidia proprietary driver.   Should I upgrade that afterwards or before?

The Nvidia driver choices right now are 381 and 384.

Should I worry about this if I use 384?:
[https://devtalk.nvidia.com/default/topic/1025477/linux/x-org-crashes-on-ubuntu-17-10-with-driver-nvidia-384-after-upgrade/2](https://devtalk.nvidia.com/default/topic/1025477/linux/x-org-crashes-on-ubuntu-17-10-with-driver-nvidia-384-after-upgrade/2)

[http://tipsonubuntu.com/2017/08/23/nvidia-384-69-released-new-gpu-support-fixes/](http://tipsonubuntu.com/2017/08/23/nvidia-384-69-released-new-gpu-support-fixes/)

[https://askubuntu.com/questions/967955/ubuntu-17-10-on-wayland-how-can-i-install-the-nvidia-drivers](https://askubuntu.com/questions/967955/ubuntu-17-10-on-wayland-how-can-i-install-the-nvidia-drivers)

It's already in Ubuntu packages....
[https://www.ubuntuupdates.org/package/core/artful/restricted/base/nvidia-graphics-drivers-384](https://www.ubuntuupdates.org/package/core/artful/restricted/base/nvidia-graphics-drivers-384)
[https://askubuntu.com/questions/968059/ubuntu-17-10-how-to-install-the-proprietary-nvidia-drivers](https://askubuntu.com/questions/968059/ubuntu-17-10-how-to-install-the-proprietary-nvidia-drivers)
[https://www.reddit.com/r/linux/comments/78ne39/getting_nvidia_drivers_working_on_ubuntu_1710/](https://www.reddit.com/r/linux/comments/78ne39/getting_nvidia_drivers_working_on_ubuntu_1710/)

But, there's complaints of some bugs recently?

My current video card is a GTX 750.

Anything else to be concerned about?

---

### Post by Autodave on 2017-10-27
Backups. Make backups. Lots of backups.

As far as the Nvidia driver: if you installed it from the repositories, it *should* be OK.

---

### Post by Impavidus on 2017-10-28
Read the [release notes](https://wiki.ubuntu.com/ArtfulAardvark/ReleaseNotes) and [known bugs and workarounds](https://ubuntuforums.org/showthread.php?t=2375077).

---

### Post by uRock on 2017-10-28
I just ran the upgrade on an ASUS laptop and it ran without a hitch.

+1 on the backups. I had no data of worth on the laptop, but am on track to see how many upgrades it will do before breaking. So far it has went from 6.04 to 7.04, then to 7.10.

---

### Post by kurt18947 on 2017-10-29
The recommendations I've seen are to disable or uninstall any additional drivers or PPA s. Try to get back to a 'stock' install, do the upgrade then reactivate/reinstall additional drivers or PPA s.

---

### Post by funicorn on 2017-10-29
Keep in mind when the upgrade process asks you whether to keep the fallback software installed on the old version which actually can work well after upgrade,  think over to make a decision. I choose no and many good applications are gone forever.

---

### Post by danik56 on 2017-10-29
I have 17.04 running on ASUS Z270H based system with ZFS based root file system.
Should I expect any issues upgrading to 17.10 ?  (I will take a ZFS system snapshot before the upgrade..)

---

