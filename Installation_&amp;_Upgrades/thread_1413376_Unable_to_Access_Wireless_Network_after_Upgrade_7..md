---
title: "Unable to Access Wireless Network after Upgrade 7.10 -&gt; 8.04"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by KentonS on 2010-02-22
I just finished upgrading from 7.10 to 8.04 on my ASUS laptop. Everything went well, and after rebooting I was able to connect to the network just fine. (I'm using Wicd as my network manager, because I have static IP addresses for the machines in my house, and the version of network-manager in 7.10 didn't support static IP addresses.)

Anyway... Then I screwed up. Attempting to follow the instructions in the Hardy Ubuntu Guide regarding installation of Envy, I copied and pasted the command to install restricted drivers (sudo apt-get install linux-restricted-modules-server). Then, before changing "-server" to "-generic" I stupidly hit <Enter>. Everything installed, and I was told to reboot. Realizing my error, I checked to see whether I could do anything to recover from it. Not wanting to remove the module before rebooting, just in case that might screw something up, I decided to reboot, then uninstall the -server drivers. After I rebooted, I had no network. Wicd reports No wireless networks found. I removed the -server module via Synaptic. Synaptic shows the -generic module is installed.

Now what? Did installing the -server module cause this? What can I do to recover? I have access to the Internet with other PCs in my house, if needed. I also have the Ubuntu 8.04.3 Live CD. I would greatly appreciate any help anyone can provide. I would REALLY like to repair this without having to do a clean install, if possible.

Thanks in advance for any help anyone can offer,
Kenton S

---

