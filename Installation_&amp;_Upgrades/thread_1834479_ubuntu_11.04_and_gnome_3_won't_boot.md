---
title: "ubuntu 11.04 and gnome 3 won't boot"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by zalba on 2011-08-27
I just installed gnome 3 on ubuntu 11.04. When I tried to log in after shutting down however, the attached image comes up. The login screen doesn't appear, and I can't seem to find any way to log in.
Any help would be greatly appreciated.

---

### Post by dummy910 on 2011-08-27
I ran into an identical situation on a friends laptop, just last weekend as it seems _**g3 is not ready for prime-time with 11.04**_.   I did some digging as to see if anything was kicked out of the way during the g3 install, and voila!, ubuntu-desktop got nailed, so in a terminal I typed the following. ```
sudo apt-get update && sudo apt-get ubuntu-desktop
``` ... then I reboot the machine and almost everything was where it had left off prior to g3 being installed as the customizations like wallpapers, fonts etc were placed back to the 1st time login settings. I think some small progs like ubuntu-tweak and a couple of others had to be reinstalled as well, again, a small price to pay 

This was my experience just last weekend with this issue.

---

### Post by zalba on 2011-08-27
Thanks for the advice. Unfortunately, when I tried using the code using root prompt in recovery mode, I get the message that none of my ppa could be updated, and that apt-get ubuntu desktop was an invalid command.

---

### Post by Kexolino on 2011-08-27
> **zalba said:**
> Thanks for the advice. Unfortunately, when I tried using the code using root prompt in recovery mode, I get the message that none of my ppa could be updated, and that apt-get ubuntu desktop was an invalid command.

dummy910 probably meant apt-get *install* ubuntu-desktop.

---

