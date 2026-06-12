---
title: "Upgrade Problem"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by rex66 on 2010-07-25
Hi all...I'm trying to upgrade from 8.04 LTS to 10.04 LTS using this method:

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

Upgrade from 8.04 LTS to 10.04 LTS
Network upgrade for Ubuntu desktops (Recommended)

You can easily upgrade over the network with the following procedure.   

   1.Press Alt-F2 and type update-manager --devel-release  
   2.Click the Check button to check for new updates.  
   3.If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.  
   4. A message will appear informing you of the availability of the new release.  
   5.Click Upgrade.  
   6. Follow the on-screen instructions. 


My problem is after step 3 there is no message informing me of the availability of a new release.

Does anyone have any idea how I would get that message to appear. I would really like to upgrade and keep my files as is.

Thanks

---

### Post by fbobraga on 2010-07-25
the page you referred above seems to be wrong. The correct form of starting update manage is with the command ```
update-manager **--proposed**
``` (from [https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS]("https://help.ubuntu.com/community/LucidUpgrades#Upgrade%20from%208.04%20LTS%20to%2010.04%20LTS") - the command in the page [http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade) seems outdated, related to a "pre-release" of 10.04)

---

### Post by rex66 on 2010-07-25
Thanks for the information....worked great! :)

---

