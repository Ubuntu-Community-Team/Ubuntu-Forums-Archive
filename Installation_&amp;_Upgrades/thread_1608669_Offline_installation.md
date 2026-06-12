---
title: "Offline installation"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by dlublink on 2010-10-29
Hey,

So about once a month I have to install Ubuntu ( or a ubuntu variant ) onto a computer which has no working boot media. CDROM won't boot, can't boot USB etc...

Back when I was using Gentoo, I could plug any harddrive into my computer, bootstrap it, plug it back into the computer it came from, boot and finish the installer.

Is this possible with Ubuntu? As I right this, I have an USB <-> IDE adapter connecting an IDE harddrive to my laptop.

I found this :

[https://help.ubuntu.com/community/Installation/FromLinux#Without%20CD](https://help.ubuntu.com/community/Installation/FromLinux#Without%20CD)

I am trying it right now

Thanks for any suggestions.

David

---

### Post by mikewhatever on 2010-10-29
Is the other hdd visible in the installer when that hdd is connected to your computer? If so, just install to that hdd and make sure grub goes to its mbr. You could also make an image of a dummy installation and use it henceforth.

---

