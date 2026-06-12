---
title: "Lucid - USB in VirtualBox"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by vkatkade on 2010-10-11
Hi,

I am running Lucid 2.6.32-24-generic and have installed VirtualBox with windowsXp as one of the machines. I am not able to access my USB devices through VirtualBox.
I followed th instructions given here
[https://help.ubuntu.com/community/VirtualBox/USB](https://help.ubuntu.com/community/VirtualBox/USB)
which mentioned that I add myself to the group "vboxusers". The group initially didnt exist so I created it and then added myself to it through the GUI and then logged out and logged back in.
However, the USB option still doesnt show up in the VirtualBox machine settings menu.

Could someone figure this?

Thanks
Vaibhav

---

### Post by pricetech on 2010-10-11
Are you running the OSE version of Virtual Box from the repos or the PUEL version from the site ??

The OSE version doesn't support USB.

---

### Post by vkatkade on 2010-10-12
Thanks pricetech, I was using the VirtualBox from the ubuntu repo. When I downloaded the one from the virtualbox website, I was able to get the USB support.

---

