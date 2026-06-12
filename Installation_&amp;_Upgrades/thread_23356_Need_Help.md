---
title: "Need Help"
date: 2005-04-01
forum: Installation &amp; Upgrades
---

### Post by Luellin on 2005-04-01
Hey There I Got The UBUNTU Open Source Disk From My Brother And I Installed It But U Couldent Figure Out How To Install My Wireless Usb Network And Also Couldent Figure Out How I Would If I Could Install The Device Get The Internet To Run Trough It. The Device Is A X-Micro Please Help

---

### Post by p0ke on 2005-04-02
I found this ndiswrapper guide most helpful in getting my wireless connection enabled. 

[http://zd7000forums.com/viewtopic.php?t=3575&sid=d27bc8e5bdd8514ca6f6faf7b3f798ae](http://zd7000forums.com/viewtopic.php?t=3575&sid=d27bc8e5bdd8514ca6f6faf7b3f798ae)

There is another howto here [http://www.ubuntulinux.org/support/documentation/howto/ndiswrapper/talkback/1104103251/view?searchterm=ndiswrapper](http://www.ubuntulinux.org/support/documentation/howto/ndiswrapper/talkback/1104103251/view?searchterm=ndiswrapper)

Once you have the driver installed (sudo ndiswrapper -i bcmwl5a.inf), verified (sudo ndiswrapper -l) and the module loaded at startup (sudo ndiswrapper -m), reboot and start Networking under System Configuration. You should now see the wlan0 device and be able to complete the setup of your network.

Hope this helps.

---

