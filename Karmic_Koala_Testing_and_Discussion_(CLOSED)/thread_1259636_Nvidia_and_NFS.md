---
title: "Nvidia and NFS"
date: 2009-09-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vorgusa on 2009-09-06
Hi, I just installed the Alpha 5 for Karmic and updated it immediately.  I also installed Nvidia drivers 185 and nfs-client (the nfs-common and portmap).  And I am having issues with both.

   The nividia settings do not seem to be working correctly... I opened the settings using root "sudo nvidia-settings" made my changes like I have done many times before on other versions.  I clicked apply to see that they are working correctly but when I tell it to save to the xorg.conf it says it can not parse the file.  If I do a "sudo nvidia-xconfig" it says it completes it and says there is an unknown device <null> and when I reboot my settings are back to they were originally (one monitor instead of two)

   For my NFS it keeps saying 

"mount.nfs:  access denied by server while mounting" x.x.x.x:/mnt/Folder.  

I used this mountpoint from the same computer and ip address using Fedora a couple days ago and nothing has changed.  same hostname and same IP.  I am just doing mount x.x.x.x:/mnt/Folder /mnt/Folder. I have tried rebooting both computers and trying again with no success.

Any ideas?

---

