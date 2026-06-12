---
title: "upgrade from 8.04 to 8.10"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by b-boy on 2008-10-31
Hi guys i want to upgrade to 8.10 from 8.04 but update manager does not give me an option to upgrade 

i have follwed theses instructions:```
Network Upgrade for Ubuntu Desktops (Recommended)

You can easily upgrade over the network with the following procedure.

   1. Start System/Administration/Software Sources
          *

            intrepid_upgrade1.png
   2. click on the "Updates" tab and change "Show new distribution release" to "Normal releases"
          *

            intrepid_upgrade2.png
   3. Start System/Administration/Update Manager
          *

            intrepid_upgrade2.5.png
   4.

      Click the Check button to check for new updates.
   5.

      If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.
   6. A message will appear informing you of the availability of the new release.
          *

            update-manager-upgrade-810.png
   7.

      Click Upgrade.
   8. Follow the on-screen instructions.

```
but it does not help

---

### Post by Partyboi2 on 2008-10-31
Make sure that your system is current with all the updates.

---

### Post by b-boy on 2008-10-31
> **Partyboi2 said:**
> Make sure that your system is current with all the updates.

I have checked for updates but none available ...so i am sure my system is up to date

---

### Post by nereid on 2008-10-31
I've got the same problem. So I'm now searching how to do the upgrade by hand ;)

EDIT:
It seems, that ```
sudo apt-get dist-upgrade
``` also won't work. IMHO Ubuntu hasn't got the information, that there is a new distribution available. Although, I changed the settings in the software repositories.

---

### Post by tylerspaska on 2008-10-31
gksu update-manager -d

---

### Post by nereid on 2008-10-31
Thanks a lot, this did the trick :)

---

### Post by GooglieS on 2008-10-31
Does not helps for me :(

---

### Post by emusbau on 2009-05-22
This is the best way to update from 8.04 to 8.10. It works for me.



> **b-boy said:**
> Hi guys i want to upgrade to 8.10 from 8.04 but update manager does not give me an option to upgrade 

i have follwed theses instructions:```
Network Upgrade for Ubuntu Desktops (Recommended)

You can easily upgrade over the network with the following procedure.

   1. Start System/Administration/Software Sources
          *

            intrepid_upgrade1.png
   2. click on the "Updates" tab and change "Show new distribution release" to "Normal releases"
          *

            intrepid_upgrade2.png
   3. Start System/Administration/Update Manager
          *

            intrepid_upgrade2.5.png
   4.

      Click the Check button to check for new updates.
   5.

      If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.
   6. A message will appear informing you of the availability of the new release.
          *

            update-manager-upgrade-810.png
   7.

      Click Upgrade.
   8. Follow the on-screen instructions.

```
but it does not help

---

