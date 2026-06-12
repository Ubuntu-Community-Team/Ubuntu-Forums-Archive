---
title: "custom filesystem.squashfs is not used when doing PXE netinstall"
date: 2017-05-03
forum: Installation &amp; Upgrades
---

### Post by unholymachine on 2017-05-03
I am using the method outlined here [https://www.hiroom2.com/2016/05/19/ubuntu-16-04-debian-8-run-pxe-boot-server-for-automated-install/](https://www.hiroom2.com/2016/05/19/ubuntu-16-04-debian-8-run-pxe-boot-server-for-automated-install/) to install ubuntu via a PXE server. However, when I  specify a location to a filesystem.squashfs in the preseed file under '[COLOR=#000000]d-i live-installer/net-image string /install/filesystem.squashfs' using '[/COLOR][COLOR=#000000]d-i live-installer/net-image string tftp://<sever ip>/install/filesystem.squashfs it never gets booted/used and I end up with a stock ubuntu installation. I've asked this question a few places and have not received any answers or possible methods as to how i would go about troubleshooting this issue. Hopefully someone here can help me out? Please let me know what  config files are needed for me to post to make the troubleshooting easier. 

Thanks[/COLOR]

---

