---
title: "update-grub and grub-customizer does not save changes."
date: 2019-01-27
forum: Installation &amp; Upgrades
---

### Post by mrjacque on 2019-01-27
Both methods of updating GRUB seems to successfully run but the additional OS it finds on another drive do not appear on the ubuntu menu. On another menu, i must press t to get to the menu after trying to show graphics or it goes off into la-la land. Remove the graphics does not fix the problem.
Hoping to get one of them working right. 
Kubuntu 18 but that should not affect GRUB.

---

### Post by oldfred on 2019-01-27
If you have multiple installs, you may be updating one grub, but booting with another.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
    
I prefer to turn off os-prober and add my own boot stanza to 40_custom.
And I now prefer to use labels for other installs, not UUIDs nor device like /dev/sda1.

---

