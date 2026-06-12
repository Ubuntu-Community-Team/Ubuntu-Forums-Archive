---
title: "Can't seem to set network to static.... WHY???"
date: 2016-11-03
forum: Installation &amp; Upgrades
---

### Post by JoelParke on 2016-11-03
I have been attempting to set my server to static internet instead of dynamic. 
First checked and found that NetworkManager -> has managed = false.
Attempted to us System Settings/Network/Options... BUT naturally you can set everything... BUT SAVE is always grayed out... since why would anyone want to change it????? and there doesn't seem to be anyway to unlock it.
So I tried. editing /etc/network/interfaces and changed to:
```
auto lo
iface lo inet loopback
iface eth0 inet static
 address 192.168.1.90
 netmask 255.255.255.0
 network 192.168.1.0
 broadcast 192.168.1.255
 gateway 192.168.1.1
 dns-nameservers 8.8.8.8, 8.8.4.4

```
But when I did: 
```
sudo ifdown eth0 && sudo ifup eth0
```
If says: 'Unknown interface eth0'
SO I did a 'ipconfig -a' and see:
```
enp0s31f6: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.250  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 2601:283:8180:875:5ddf:3a7a:5dcd:69ef  prefixlen 64  scopeid 0x0<global>
        inet6 2601:283:8180:875:c2ea:5298:afe2:2893  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::1c64:6657:ad6a:e548  prefixlen 64  scopeid 0x20<link>
        ether 2c:56:dc:3a:32:b1  txqueuelen 1000  (Ethernet)
        RX packets 98790  bytes 23709194 (23.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 95453  bytes 12533576 (12.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xdf300000-df320000  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 187985  bytes 342230713 (342.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 187985  bytes 342230713 (342.2 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
And again: changing to enp0s31f6 instead of eth0 does the same thing!!!
Now I wish I never upgraded to 16.10 from 16.04.
First the upgrade crashed and I had to rebuild from a backup from 1 month back.
And that crashed.  So I had to reinstall 16.10, which lost all my setting and packages.
Then I reinstalled all the packages... and now I can't set to a static IP address.
WHY is this so hard!
Any help would be greatly appreciated.

Shouldn't I just be able to set static through the System Settings/Network/Options dialog???????

---

### Post by JoelParke on 2016-11-03
As I continued to hit my head against the wall.... I eventually removed all the settings I put into /etc/network/interfaces. and rebooted a few times...
THEN I was able to set static using the System Settings/network/Options... 
SO I would guess that if it doesn't like something, it just fails silently!!!! (like that is a good thing)
So now all is working as expected.  
BUT perhaps someone could verify that /etc/network/interfaces does nothing??? and can't be edited.  
Since it didn't change when I set a static ip address for the internet using the gui interface and the network is now set to a static ip and nothing in this file has changed!!!!
JUST a word to those that run down this rabbit whole.

---

### Post by kevdog on 2016-11-03
Ok

Take a deep breath, everything is fine

Take a look at this post -- It might help you change things back to eth0.
[http://askubuntu.com/questions/767786/changing-network-interfaces-name-ubuntu-16-04](http://askubuntu.com/questions/767786/changing-network-interfaces-name-ubuntu-16-04)

---

