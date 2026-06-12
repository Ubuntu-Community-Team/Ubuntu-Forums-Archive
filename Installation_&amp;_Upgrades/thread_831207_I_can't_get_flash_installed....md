---
title: "I can't get flash installed..."
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by DAE_JA_VOO on 2008-06-16
When installing flash, i get this:

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.


Why's it doing this?

---

### Post by tamoneya on 2008-06-16
close all of your web browsers and type this into terminal (applications -> accessories -> terminal):
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by snowpine on 2008-06-16
> **DAE_JA_VOO said:**
> When installing flash, i get this:

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.


Why's it doing this?

Hi D_J_V, the easiest way to get Flash is to start up the Synaptic Package Manager (in the System menu) and install flashplugin-nonfree.

All that you've done at this point is download a "tarball" which is kind of like a zip file in windows. It doesn't do anything unless you extract it and run the installer within. I prefer the Synaptic method I mentioned above.

Good luck!

---

### Post by DAE_JA_VOO on 2008-06-16
> **tamoneya said:**
> close all of your web browsers and type this into terminal (applications -> accessories -> terminal):
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```



```
ett@ett-modding-room:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ett@ett-modding-room:~$ 

```

:(

---

### Post by snowpine on 2008-06-16
What exactly happens when you try to view a Flash video?

---

### Post by aysiu on 2008-06-16
Try this:
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

---

### Post by fishbulb1022 on 2008-07-22
if none of the above methods help, this is how i got it...in firefox on a flash page a message comes up if you don't have flash, should be at the top of the page, just under the toolbar. there should be a button that says install plug-in, just click it.

---

