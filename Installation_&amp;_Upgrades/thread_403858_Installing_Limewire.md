---
title: "Installing Limewire"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by ErusGuleilmus on 2007-04-07
I read the guide on how to install Limewire off of [http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_Gnutella_Client_.28LimeWire.29](http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_Gnutella_Client_.28LimeWire.29) .

---

### Post by ErusGuleilmus on 2007-04-07
I read the guide on how to install Limewire off of [http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_Gnutella_Client_.28LimeWire.29](http://easylinux.info/wiki/Ubuntu#How_to_install_P2P_Gnutella_Client_.28LimeWire.29) .
I copy and pasted this code to the terminal:

wget -c [http://easylinux.info/uploads/LimeWireOther.zip](http://easylinux.info/uploads/LimeWireOther.zip)
sudo unzip -u LimeWireOther.zip -d /opt/
sudo chown -R root:root /opt/LimeWire/
sudo gedit /usr/bin/runLime.sh

It downloaded the file just fine, but after it was downloading, it asked for may password. I typed in my password, and yes I was typing it in correctly, but it just says that my password is incorrect. Again, I was typing in the password that I use in the login screen. Any help would be greatly appreciated.

---

### Post by spin2cool on 2007-04-07
Is there a question here?  if you're trying to install it, I'd use automatix ([www.getautomatix.com](www.getautomatix.com)) to install FrostWire, the open-source version that connects to the same network.

---

### Post by solar george on 2007-04-07
You would probably be best installing one the limewire-type/compatible clients from the ubuntu repos, a quick search here or on google should find a few.

---

### Post by ErusGuleilmus on 2007-04-07
Sorry, It didnt include the second half of the post for some reason. But thank you, that worked.

---

### Post by bapoumba on 2007-04-07
@ ErusGuleilmus: merged your threads, as both had answers in them.

---

