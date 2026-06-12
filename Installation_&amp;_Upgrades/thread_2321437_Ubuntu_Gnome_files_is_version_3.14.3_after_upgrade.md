---
title: "Ubuntu Gnome files is version 3.14.3 after upgrade"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by sbtypo3 on 2016-04-22
I upgraded my ubuntu Gnome 5.10 to 16.04 and now I have an old version of files. 3.14.

Is there anyway to upgrade to version 3.18??

---

### Post by grahammechanical on 2016-04-22
Yes, so do I. For a few days during the development cycle we did get Files 3.18 but it was broken and the Ubuntu developers had to revert to the older version - 3.14. You will find that some other Gnome utilities are at version 3.18. See Gedit, Disks & Character map as examples.

I am reminded that Nautilus is more than a file manager. It is also integrated into the desktop. And Synaptic Package Manager is showing me that the installed version is 3.18. So, perhaps it is only the file manager user interface  that has been reverted to the 3.14 version.

Best wait until the developers sort things out. 

Regards.

---

### Post by deadflowr on 2016-04-22
You can get by adding this ppa:
[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3?field.series_filter=xenial]("https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3?field.series_filter=xenial")
As stated above 3.18 was used, but since it did not work well with unity, they moved back to an older version.
And since UbuntuGnome and Ubuntu share the same package resources, when they removed it because of unity, they had to remove it for ubuntugnome as well.

Hope it helps

---

