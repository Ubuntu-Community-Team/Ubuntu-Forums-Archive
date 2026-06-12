---
title: "Problem installing 12.04"
date: 2014-02-12
forum: Installation &amp; Upgrades
---

### Post by hakimoerton on 2014-02-12
I broke my working 13.04 uninstalling cinnamon and decided to install 12.04. I have an old live cd for 12.04 and ran that, ending up with a grub problem which I have not been able to get rid of.

Numerous installs, auto or manual result in a grub file not found fail. Currently I have physically disconnected a second hdd and removed all partitions  from the hdd I'm trying to put 12.04 on with gparted . 
Still grub is trying to load - where is it hiding?

I am thinking a hdd with no partitions should not be trying to load.

What's my next step?

Hakim

---

### Post by hakimoerton on 2014-02-13
Problem solved after reading this: [http://askubuntu.com/questions/131168/how-do-i-uninstall-grub]("http://askubuntu.com/questions/131168/how-do-i-uninstall-grub")

Essentially: disconnect hdd until live cd/usb loads - don't do anything for a minute - reconnect hdd and select install.

Worked like a dream ... 12.04 purring nicely.

Thank you lambda23

---

