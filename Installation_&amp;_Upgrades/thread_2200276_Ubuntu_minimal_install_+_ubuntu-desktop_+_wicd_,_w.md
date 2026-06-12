---
title: "Ubuntu minimal install + ubuntu-desktop + wicd , wicd doesnt show a notif. icon"
date: 2014-01-18
forum: Installation &amp; Upgrades
---

### Post by Krist Blomme on 2014-01-18
I have done a Ubuntu 12.04 minimal install

I did not install additional packages during he install .

After reboot I did :
sudo apt-get --no-install-recommends install  dconf-tools indicator-datetime indicator-power indicator-session indicator-sound pavucontrol **ubuntu-desktop** unity-lens-applications unity-lens-files **wicd** zeitgeist

When I restart the computer connected with eth0 , wicd shows  no icon in the notification area .
I can start wicd manually and connect to wireless networks.

If I reboot without eth0 , during boot it keeps waiting for a network connection , it does not connect wireless .

How can I enable wicd during boot ?
How can I get the wicd icon in the notification area ?

---

### Post by varunendra on 2014-01-18
As far as I know, wicd does not offer any notification icon. For that you may wish to switch to NM instead (sudo apt-get install network-manager-gnome).

---

### Post by Krist Blomme on 2014-01-19
1- waiting or network was solved by editing /etc/network/interfaces as follows

cat /etc/network/inerfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

commenting the eth0 part that is 

2- getting the wicd icon

this was solved by using dconf 

>desktop>unity>panel
addinng the Wicd notification :

['JavaEmbeddedFrame', 'Wine', 'Update-notifier', 'Wicd']

---

