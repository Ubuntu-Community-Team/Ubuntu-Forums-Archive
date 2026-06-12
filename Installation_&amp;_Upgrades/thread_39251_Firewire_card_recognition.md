---
title: "Firewire card recognition"
date: 2005-06-04
forum: Installation &amp; Upgrades
---

### Post by pdc on 2005-06-04
I am new to Ubuntu (and linux); I installed a PCI Firewire card into the computer today; (it only has Ubuntu installed); should the hardware recognition on Ubuntu recognise the card? Or what else should I do? I was interested to try capturing some digital video, using kino, if I can get kino to connect to the camera; it says the IEEE1394 kernel is not installed; I could not identify from synaptic which package I should try to install

---

### Post by mtron on 2005-06-04
if there are drivers for your card it should work out-of-the box.

try 
sudo apt-get install libavc1394-0

---

### Post by kafton on 2005-06-04
You might want to run in a terminal
> lsmod | grep 1394 
to see if the modules ohci1394 and ieee1394 are loaded. If they are not, load them with modprobe and see if firewire works.

---

