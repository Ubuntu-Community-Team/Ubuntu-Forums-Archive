---
title: "Installing Adobe flash?"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by Andrew.McCoy on 2010-11-02
I have been trying to Install Adobe flash on Ubuntu 10.10, when the window pops up and tells me about the third party source, I try to download, however after it starts to download it flashes the loading sign and then nothing happens. It goes back to the third party source announcement. Help?

---

### Post by TBABill on 2010-11-02
You are trying to install by clicking a link on the web. That's not how it works in Linux distributions. The best way is to go into Synaptic and install the package "ubuntu-restricted-extras", which will install flash and a host of other codecs necessary to enjoy the online environment. You may also want to install Sun Java (click search in the repo and install the sun java plugin) to enjoy every website appropriately. The restricted extras package installs open source java and, while it is good, Sun Java can handle the sites where open java fails.
 
If you do not want to install via Synaptic, in case you are unfamiliar with it, you can also open a terminal window and just type: ```
sudo apt-get install ubuntu-restricted-extras
``` Then just enter your password and let the system take care of the rest.
 
Post back if you need clarification.

---

### Post by oldos2er on 2010-11-02
Or use [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by Andrew.McCoy on 2010-11-03
Thanks to both of you! I got everything working properly.

---

