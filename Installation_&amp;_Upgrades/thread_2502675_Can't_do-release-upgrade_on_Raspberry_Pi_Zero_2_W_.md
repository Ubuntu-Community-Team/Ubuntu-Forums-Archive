---
title: "Can't do-release-upgrade on Raspberry Pi Zero 2 W [23.10]"
date: 2024-11-24
forum: Installation &amp; Upgrades
---

### Post by hubi97 on 2024-11-24
[COLOR=#555555][FONT=Roboto]I would like to do an upgrade of unsupported Ubuntu 23.10 via do-release-upgrade. I have never had any problem with this until now. When I want to upgrade my Raspberry Pi Zero 2 W. During the upgrade it displays this message:
```
[/FONT][/COLOR]Sorry, cannot upgrade this system to 24.04 LTS

The Raspberry Pi kernel for Ubuntu 24.04 LTS does not support the
armhf architecture.


Updates for Ubuntu 23.10 will continue until July 2024.




Restoring original system state



Aborting[COLOR=#555555][FONT=Roboto]
```

[/FONT][/COLOR][COLOR=#555555][FONT=Roboto]This is strange because the ubuntu 24.04 LTS image is downloadable and installable for this platform. Could someone please advise on the best way to do the upgrade for rpi zero?
Thanks[/FONT][/COLOR]

---

### Post by grahammechanical on 2024-11-24
I am completely unfamiliar with Ubuntu on the Raspberry so I am assuming that there is a reasonable similarity between the armf and the amd64 User Interfaces.

When a version of Ubuntu reaches End Of Life (EOL) the addresses of the software repositories are changed. This is why we cannot update/upgrade or do an online upgrade to the next version. We are into the fourth month since EOL for 23.10. It could be that this is the situation you are in. Can you do an update/upgrade?

Your options may be to do a fresh install of Ubuntu 24.04 LTS. Or, changing the internet addresses of the software repositories to old-releases.ubuntu.com/

[https://old-releases.ubuntu.com/releases/](https://old-releases.ubuntu.com/releases/)

I was hoping to provide a link to how to do this but I am getting a 503 Service Unavailable from the address. Which is

[URL="https://help.ubuntu.com/community/EOLUpgrades"]https://help.ubuntu.com/community/EOLUpgrade

[/URL] Can you get a printout or your sources.list file? To see the present internet addresses of the repositories. I am sorry I cannot do more.

Regards

---

### Post by deadflowr on 2024-11-24
There are no armhf raspi images any more
from the release notes: [https://discourse.ubuntu.com/t/ubuntu-24-04-lts-noble-numbat-release-notes/39890#p-99950-no-32-bit-armhf-images](https://discourse.ubuntu.com/t/ubuntu-24-04-lts-noble-numbat-release-notes/39890#p-99950-no-32-bit-armhf-images)

Edit:
> From 24.04 (noble), we will no longer be producing 32-bit (armhf) images for the Raspberry Pi. The only images produced will be 64-bit (arm64). For the avoidance of doubt, this does not mean that armhf is no longer supported as an architecture on Raspberry Pi; it will remain supported as a foreign architecture in noble

---

### Post by hubi97 on 2024-11-26
Yes! Thank you, I didn't realize that my system is 32-bit.

---

