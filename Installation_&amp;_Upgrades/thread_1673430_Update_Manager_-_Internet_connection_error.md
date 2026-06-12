---
title: "Update Manager - Internet connection error"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by PhillyKingston on 2011-01-22
So the Update Manager ran automatically about a week ago and I started getting notified that there was trouble connecting to a server.  I ran the "sudo apt-get update" command and posted the output below.

```

W: Failed to fetch http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```I understand that servers go down once in awhile, so no big deal, but I was wondering if it was possible to get another server or determine what was being updated from this server?  Is it possible to get a replacement?

---

### Post by Old_Grey_Wolf on 2011-01-22
Try going to "System > Administration > Synaptic Package Manager". When the Synaptic window opens, select the menu "Settings > Repositories". When the Repositories window opens select from the "Download from:" pull-down menu "Other...". It will give you a list; however, click the "Select Best Server" button. It will take a while as Synaptic tests for the best server. Click on the "Select Server" button. When you click the "Close" button, it will tell you to click on the "Reload" button. Click "Close" button, then on the main Synaptic window, click on the "Reload" icon. You can close the windows and try to update again.

---

### Post by learst on 2011-01-23
Thanks old_gray_wolf! That worked for me.

---

### Post by Old_Grey_Wolf on 2011-01-23
I'm glade to help when I can. Enjoy.

---

