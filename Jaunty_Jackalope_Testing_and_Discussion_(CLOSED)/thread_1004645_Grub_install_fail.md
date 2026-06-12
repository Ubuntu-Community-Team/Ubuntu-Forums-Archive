---
title: "Grub install fail"
date: 2008-12-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by w3rt on 2008-12-07
Just downloaded the daily build of jaunty, the install went fine until the end where grub should have been installed. An error message came up saying 'grub could not be installed, this is a fatal error' I have never experienced any grub problems when installing any version of ubuntu before so I have no idea what happened this time .....

---

### Post by caljohnsmith on 2008-12-07
> **w3rt said:**
> Just downloaded the daily build of jaunty, the install went fine until the end where grub should have been installed. An error message came up saying 'grub could not be installed, this is a fatal error' I have never experienced any grub problems when installing any version of ubuntu before so I have no idea what happened this time .....
At least for previous versions of Ubuntu, sometimes that fatal Grub error during the installation can be circumvented by having Grub installed to /dev/sda or whichever is the drive you are installing Ubuntu to, and not using the default which is (hd0). In other words, if you are installing via a Live CD, you would click the "advanced" button near the end of the installation process and that's where you can specify where Grub gets installed to. How about trying that with Jaunty and let me know if it helps; if it doesn't, I know of another workaround that is almost as simple, and may at least enable you to install Ubuntu successfully.

---

