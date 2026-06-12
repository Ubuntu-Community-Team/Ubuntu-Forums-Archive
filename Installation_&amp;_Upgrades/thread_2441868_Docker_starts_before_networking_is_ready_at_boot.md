---
title: "Docker starts before networking is ready at boot"
date: 2020-04-27
forum: Installation &amp; Upgrades
---

### Post by shutupfry on 2020-04-27
I'm trying to configure a Pi4 to run Ubuntu 18.04 and a bunch of docker containers with most of the persistent storage needed located on my nas via nfs shares. I've got everything working so far except that when I reboot the system, none of the containers with nfs volumes are able to start (/var/log/syslog shows "network is unreachable" for the container volumes). I've tried a lot of different solutions I've found and none of them seem to work. I'm a little bit new to systemd, but from what I can tell it doesn't seem to honor the networking dependencies defined. Please help!

---

### Post by lvm on 2020-04-27
Add/change "After=network-online.target" to /lib/systemd/system/docker.service. Note that this file may be overwritten by future updates, there is an update-safe mechanism using systemctl but I am fuzzy about details here.

---

### Post by shutupfry on 2020-04-27
The default file already contains "After=network-online.target firewalld.service containerd.service" and it doesn't work.

---

### Post by shutupfry on 2020-04-30
I finally solved this. I had to edit the network configuration file for eth0 in /etc/netplan/ and remove the "optional: yes" entry. Now it all works. I also still have "After=nfs-client.target" entered in "systemctl edit docker.service"

---

