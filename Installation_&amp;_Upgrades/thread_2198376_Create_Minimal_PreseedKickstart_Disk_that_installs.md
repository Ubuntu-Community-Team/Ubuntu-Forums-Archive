---
title: "Create Minimal Preseed/Kickstart Disk that installs from local network Repo"
date: 2014-01-08
forum: Installation &amp; Upgrades
---

### Post by hack_axle on 2014-01-08
Hello all,

Objective:

Create very minimal usb install that uses preseed/kickstart to perform an automated install. As many files as possible must be hosted on a server. (PXE is not an option).

For the most part I have been successful in this, and my preseed and kickstart seem to be working and my kickstart file is hosted on the network. However, I need to not have any of the debs on the minimal image. Basically delete pool from the tree and install all the debs from my local respository. That way no matter when installed they are always the most later version. In my preseed I have

### Mirror settings 
d-i mirror/country string manual 
d-i mirror/http/hostname string pathtorepo 
d-i mirror/http/directory string /ubuntu 
d-i mirror/http/proxy string


With all my google-fu I am stuck. Either I am not understanding a portion or just need pointed in the right direction. Any help would be appreciated.

The still appears to be using pool from the cdrom. Could anyone point me in the direction to create a minimal install iso that will install everything from network based files?

---

