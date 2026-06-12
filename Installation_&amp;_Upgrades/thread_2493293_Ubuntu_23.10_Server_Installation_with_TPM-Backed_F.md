---
title: "Ubuntu 23.10 Server Installation with TPM-Backed FDE?"
date: 2023-12-09
forum: Installation &amp; Upgrades
---

### Post by corvuseng on 2023-12-09
Is it possible to install 23.10 Server with the TPM-backed Full Disk Encryption feature yet?

---

### Post by MAFoElffen on 2023-12-09
Sort of... Install from the Ubuntu Desktop installer with those installer options.

After the install finishes, and reboots, after booting... Press the keys <Cntrl><Alt><F4>... Login with your credentials...
```

sudo apt update
sudo apt remove --purge ubuntu-desktop
sudo apt install ubuntu-server

```
Edit the netplan yaml file from /etc/netplan/ and replace the renderer from Network Manager to networkd. Make any other changes. Save and exit
```

sudo systemctl stop NetworkManager
sudo systemctl disable NetworkManager
sudo systemctl mask NetworkManager
sudo systemctl enable systemd-networkd
sudo systemctl enable systemd-networkd
sudo systemctl start systemd-networkd
sudo netplan generate
sudo netplan apply

```
And there you go.

OR... From the 23.10 Server edition Installer LiveUSB, you go go over to a system prompt from the Help button, and do it all manauly. The how to do it is well ducmented, and you can do a better job, by creating the LUKS containers, setting your own passphrases, and enrolling the key to the TPM, while adding your own secondary recovery keys in the keyslots, add a keyfile for any other added LUKS partitions (like home or data) and avoid the bug report I have file on the installer for that install option: [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2039741](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2039741)

With that installer's partitioner, it is volume manager and filesystem aware, so you can then exit the system prompt, back to the installer, use "other" to get to the partitioner, where you can connect the mounts to where you want them, then continue the installation.

Either way.

---

### Post by corvuseng on 2023-12-09
Thanks.  Will give this a try.

---

