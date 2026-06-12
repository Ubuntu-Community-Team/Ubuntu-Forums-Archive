---
title: "can't upgrade to 10.10 from Ubuntu 10.04.2 LTS"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by raider-G on 2011-02-08
Hi,

~$ cat /etc/issue
Ubuntu 10.04.2 LTS \n \l

If I open update-manager and hit check no updates are left and still it doesn't tell me to upgrade to the new 10.10 version . What can be the issue ?

Thanks,
-Ghita

---

### Post by Old_Grey_Wolf on 2011-02-08
Using the menus select "System > Administration > Synaptic Package Manager". Then select the menu "Settings > Repositories". Click on the "Updates" tab. There should be a pull-down menu for "Show new distribution releases:". The pull-down menu probably shows "Long term releases only". Change that to "Normal Releases". Click on the "Close" button. In the Synaptic page click on the "Reload" icon. Close the Synaptic page with either the "x" or "File > Quit". Then using the menus, select "System > Administration > Update Manager". At the top it should show the option to upgrade to 10.10.

Please read my signature and follow the advice before you do the upgrade. :)

---

### Post by raider-G on 2011-02-11
Thanks ! that worked

---

