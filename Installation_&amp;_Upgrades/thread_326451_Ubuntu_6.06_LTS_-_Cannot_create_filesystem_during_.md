---
title: "Ubuntu 6.06 LTS - Cannot create filesystem during install"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by Xyem on 2006-12-27
I am attempting to install 6.06 LTS onto one of my older computers ( 350Mhz, 256MB RAM ) so I can use it as a gateway to a wireless network and hence, the internet. I chose 6.06 because of it's "native" support for the RT61 wireless PCI card I have.

I am running into a small problem during installation which may or may not be known about..

After selecting it to erase my entire HDD ( 120GB ) it will go to "Creating filesystem" and at about 13% it will crash and say "Cannot create filesystem". When I click OK, Ubuntu actually continues to attempt to install. I haven't had any problems installing Fedora Core 6 to this drive ( the wireless support is not there, funny considering it is supposed to be bleeding edge ) so I don't think it is a hardware issue ( despite the BIOS reporting it as a 59GB drive ).

Has anyone else had this problem and know of any workarounds or extra steps I could take to get it to install so I can get this gateway up and running before I go crazy? 8) Not a big fan of wireless..

---

### Post by Xyem on 2006-12-28
I believe I have found the cause to this problem but not a direct solution.

If I open Gparted and try to manually delete the partitions, it claims that some are busy/mounted ( though 'mount' shows nothing is using the harddrive ) such as the swap partition.

If I let Ubuntu come up with the aforementioned error and then rerun the installation, it works fine the second time around.

---

