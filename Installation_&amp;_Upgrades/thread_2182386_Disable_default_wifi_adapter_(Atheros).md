---
title: "Disable default wifi adapter (Atheros)"
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by Sagnik_Sinha on 2013-10-21
My default Wifi adapter that was inbuilt in my laptop, i.e Atheros ARP9285 Wireless Network Adapter(PCI Express) suffered some damage recently and started malfunctioning or rather functioning inconsistently. So, I purchased a Netgear WNA3100M USB Network Adapter. Now I want to make this my default adapter, after removing the driver for the Atheros device. How do I accomplish this? I don't want to go down at the hardware level... Just if I could remove the driver so that the device won't be detected anymore. Thanks!

---

### Post by varunendra on 2013-10-23
Welcome to the forums Sagnik !

Assuming your Netgear adapter is already working and you don't need help with that, just blacklist the ath9k driver so it doesn't load at startup -
```
echo "blacklist ath9k" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
..then reboot and the driver won't be loaded anymore. Your card will still be detected by the system, but won't be activated. As an additional step, you may also delete (or move) the udev rules file, although I'm not sure if the new auto-generated file will contain the atheros card entry or not, but it is definitely not going to harm anything -
```
sudo mv /etc/udev/rules.d/70-persistent-net.rules 70-persistent-net.rules.bak
```
This will move the file to your home directory as "70-persistent-net.rules.bak". It will be automatically regenerated at

---

