---
title: "Wubi 12.10 not detecting Desktop CD ISO?"
date: 2012-12-12
forum: Installation &amp; Upgrades
---

### Post by r4fay on 2012-12-12
I have placed the setup that Wubi installer downloads in the same directory as that of Wubi.exe, but the installer still tries to download the setup. Here's a screenshot:

[IMG]http://images.devs-on.net/Image/BqcXxmpn7M7JwSBl-Wholescreen.png[/IMG]

---

### Post by darkod on 2012-12-12
I don't know much about wubi, but I think that only works with the .iso not the .tar.xz.

And they have to be the same version. What you can do is download the iso and open it with any program that can open ISOs. The wubi.exe is also inside. Extract only the wubi.exe leave the ISO as it is (not extracting all of it).
Then place wubi.exe and the .iso in one folder and try again.
In win7 you might need to launch it with right-click, Run as Administrator so that it has higher permissions.

---

### Post by Frogs Hair on 2012-12-12
darkod is correct. The ISO needs to be placed in a folder with Wubi.exe and it will use the ISO in the folder instead of downloading it.

If Wubi is installing the version you want to try you could allow it download . If you want create a Ubuntu DVD then down load the ISO.

---

### Post by bcbc on 2012-12-13
You can explicitly reference the diskimage - or use the ISO as mentioned already.

To use the diskimage you need to supply the --dimagepath parameter as shown here: [http://askubuntu.com/a/143478/14916](http://askubuntu.com/a/143478/14916)

---

