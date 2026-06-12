---
title: "After upgrading using the backports-extra PPA, my startup script no longer runs"
date: 2024-06-16
forum: Installation &amp; Upgrades
---

### Post by SpectrumDT on 2024-06-16
I have Kubuntu 22.04. I have a startup script which, among other things, runs xbindkeys to set up some custom key bindings.

Recently I upgraded using the backports-extra PPA by following this guide: [https://www.omgubuntu.co.uk/2023/10/install-kde-plasma-5-27-kubuntu-22-04](https://www.omgubuntu.co.uk/2023/10/install-kde-plasma-5-27-kubuntu-22-04)

sudo add-apt-repository ppa:kubuntu-ppa/backports-extra
sudo apt full-upgrade

After a reboot, my startup script no longer gets executed. 

* The script is still listed under System Settings -> Startup and Shutdown -> Autostart.
* The path looks correct.
* I do not see any error messages in the GUI upon startup.
* The script runs fine if I launch it manually from Konsole.
* I not deliberately changed anything that should impact this. 

How can I debug what goes wrong here? Can I inspect some startup logs or anything?

Thanks in advance!

---

### Post by currentshaft on 2024-06-16
What is the "startup script"? Can you share it here, or at least the first few lines with the interpreter listed?

---

### Post by SpectrumDT on 2024-07-04
> **currentshaft said:**
> What is the "startup script"? Can you share it here, or at least the first few lines with the interpreter listed?
Sorry for not replying! I was away from my PC for a while. The script looks like this (much of it is commented out):

```
#!/bin/bash 
xbindkeys & 
qdbus org.freedesktop.ScreenSaver /ScreenSaver Lock & 
#fcitx &
#(sleep 3s; sudo /usr/local/bin/protonvpn c -f) &
(sleep 15s; clementine) &
(sleep 20s; firefox) &
#(sleep 40s; signal-desktop) &
#(sleep 60s; nice -n 5 ktorrent) &
```

---

