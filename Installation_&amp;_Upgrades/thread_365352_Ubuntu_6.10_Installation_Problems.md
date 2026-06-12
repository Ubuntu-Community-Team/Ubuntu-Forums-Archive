---
title: "Ubuntu 6.10 Installation Problems"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by Hamsterman on 2007-02-19
Hi, I'm completely new to Ubuntu, so I have no idea how to fix whatever is wrong with my computer.

When I boot from the Ubuntu 6.10 CD it loads the menu, but when I try to install Ubuntu it almost immediately gives the following messages:

[17179570.196000] PCI: JMB36X: Enabling dual function on 000:02:00.0
[17179570.220000] PCI: Cannot allocate resource region 0 of device 0000:02:00.0
[17179570.220000] PCI: Cannot allocate resource region 1 of device 0000:02:00.0
[17179570.220000] PCI: Cannot allocate resource region 2 of device 0000:02:00.0
[17179570.220000] PCI: Cannot allocate resource region 3 of device 0000:02:00.0

And something else that I didn't write down.

My machine is an Intel Core 2 Duo 2.13 GHz with 2GB RAM, and a 250GB SATA harddrive, if that's at all relevant.

---

### Post by rsambuca on 2007-02-19
What motherboard do you have?  There is a problem with Edgy and certain intel MB's with the JMicron controller chipset.

---

### Post by Hamsterman on 2007-02-19
I have a FOXCONN P9657AA-8KS2H motherboard. During boot it does flash a message saying something about JMicron, but it's too quick to read.

Is there any workaround for this?

---

### Post by rsambuca on 2007-02-19
I am not sure about the status of this.  You will have to search the threads.  You might consider the latest Feisty Herd 4 as it uses the 2.6.20 kernel.

Edit:  Try this thread:  [[COLOR="Red"]link[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=234706&highlight=jmicron")

---

### Post by Hamsterman on 2007-02-19
Will do. Thanks in advance!

---

