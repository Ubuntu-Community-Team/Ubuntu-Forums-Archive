---
title: "Cant't install 19.04 - bad unsquash configuration"
date: 2019-04-29
forum: Installation &amp; Upgrades
---

### Post by kaktux on 2019-04-29
Hi there,

as my old netbook (asus eee pc 1015 pde) is quite slow using kubuntu i wanted to try lubuntu 19.04 (installing via liveusb stick).

So in the installation i kept all partitions - and choose to format+mount the current home and root.

But after the installer is done formatting the following error occurs:
> bad unsquash configuration cdrom/casper/filesystem.squashfs does not exist

And thats it. I tried to reinstall squashfs-tools, search the net (this was supposedly fixed... [https://bugs.launchpad.net/ubuntu/+source/calamares-settings-ubuntu/+bug/1769781](https://bugs.launchpad.net/ubuntu/+source/calamares-settings-ubuntu/+bug/1769781)) - but couldn't find an answer.
Other distributions - like kubuntu don't give the error when trying to install via liveusb - so i guess its lubuntu causing this.

Anyone else who can confirm that or knows a workaround?

---

### Post by Rubi1200 on 2019-04-29
Would be good to take a look here:
[https://help.ubuntu.com/community/SquashfsErrors](https://help.ubuntu.com/community/SquashfsErrors)

Often these errors are caused either by a corrupted image or bad burn.

Try another USB stick also to see if that was the issue.

---

### Post by kaysar on 2019-06-09
***Heads-up...***

**Lubuntu 19.04 Support lifespan **Lubuntu 19.04 will be supported for 9 months, until January 2020. If you need Long Term Support, it is recommended you [use Lubuntu 18.04 LTS instead]("https://lubuntu.me/downloads/") (with LXDE), which will be supported for 3 years, until April 2021.

---

### Post by g7x on 2020-02-15
i sold problem with diferent instaler in usb. I used before Yumi boot instaler and get error [h=2]bad unsquash configuration[/h]After that i try use Rufus usb installer. And ualia, get correct install lubuntu 19.10 !!!

---

### Post by stratokopos on 2020-02-16
> **g7x said:**
> i sold problem with diferent instaler in usb. I used before Yumi boot instaler and get error **bad unsquash configuration**

After that i try use Rufus usb installer. And ualia, get correct install lubuntu 19.10 !!!

That worked for me as well. Many thanks!

---

### Post by wildmanne39 on 2020-02-16
Old thread back to sleep.

---

