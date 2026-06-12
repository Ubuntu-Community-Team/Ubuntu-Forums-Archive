---
title: "Triple Boot to test Ubuntu 20"
date: 2020-10-09
forum: Installation &amp; Upgrades
---

### Post by bulgin on 2020-10-09
Hello, I'm confident a guru or two may be able to give me some guidance.

My laptop geometry is 2 sd cards - one running Windows 10 and the other Ubuntu 18.

Because I'd like to have an *encrypted* Linux operating system, I'd like to take advantage of installing Ubuntu 20 next to Ubuntu 18 and try it out.  I understand that I can choose to install an encrypted partition using LVM on a fresh install of Ubuntu 20 (currently the Ubuntu 18 does not have an encrypted home directory).

Grub currently gives me the option of booting into to either Ubuntu 18 or Windows 10.

I have additional space on the sd card that currently runs Ubuntu 18.

What would be the suggested way to retain boots for Windows 10, Ubuntu 18 and a new install of Ubuntu 20?

Currently when I provide an extra empty partition next to my Ubuntu 18 install on the Ubuntu SD card, the Ubuntu 20 install prompts do not offer the option to install Ubuntu 20 *next to* Ubuntu 18.

Any help much appreciated.

Thank you.

---

### Post by guiverc on 2020-10-09
FYI: Ubuntu uses *yy* releases only for specialist *snap* based releases for IoT appliances/devices or cloud based use (having done so since 2016). Main releases use *yy.mm* such as used by server & desktops releases.

Assuming you're talking Ubuntu Desktop (thus 18.04 & 20.04, and not Ubuntu Core 18 and Ubuntu Core 20), you can use *Something-else* to create partitions yourself and install.  Myself I find it easier to setup what I want before hand (using `gparted`, KDE Partition Manager or whatever tool you like), then just select your pre-prepared partitions with the installer.

You also mention "*encrypted home directory*" which was offered in prior releases, default installs now are *full-disk* (or* partition*) securing more of your system than just the home directories.  

I'm assuming you're talking Ubuntu Desktop (thus 18.04/20.04) and not Ubuntu Core 18/20, so it might help if you clarify.

---

