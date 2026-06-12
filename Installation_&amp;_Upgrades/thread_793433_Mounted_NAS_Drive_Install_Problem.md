---
title: "Mounted NAS Drive Install Problem"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by DamonChyld on 2008-05-13
I am having an issue reestablishing my NAS connection after a reinstall following my cheat-sheet here:
```


synaptic-package-manager
samba
smbfs

Terminal
sudo gedit /root/.credentials
   username=****
   password=****
sudo chmod 600 /root/.credentials
cd /
sudo mkdir BigDisk
sudo gedit /etc/fstab
   //192.168.0.66/bigdisk /BigDisk cifs credentials=/root/.credentials,rw,auto,uid=dna,gid=dna

sudo ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
sudo ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh
sudo mount -a (or restart)

```
I did my laptop at the same time and am not having any issues with using these steps. If I take off the .credentials and put in my user/pass it will connect, though then I have my login info in fstab and a desktop icon (I am mounting it to /BigDisk so that I can make a shortcut on my top panel and not have to have the icon laying around all the time).

I appreciate any help on this

---

