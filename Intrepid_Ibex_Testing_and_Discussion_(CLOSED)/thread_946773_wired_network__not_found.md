---
title: "wired network  not found"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by devoncatt on 2008-10-13
I installed 8.10 beta on a new partition on my ubuntu 8.04 box. I had problems with login which were easily fixed but networking was a no go,

I went to Network Manager and tried to do either dhcp or static and had no luck . It can't find any Ethernet .
I have  Marvel Group 88E8052 PCI-E Gigabit Rev 20 Ethernet. Network manager wanted the hardware ( MAC) address which I entered ( after getting it on 8.04.)

Absolutely no connection to the internet or even to my router with DHCP or a static  address. Ibex doesn't believe I have any ethernet. It also failed with my built-in wireless. This is a standard ASUS motherboard nothing fancy. Everything else works fine but no networking at all.
Any suggestions?

Devoncatt

---

### Post by devoncatt on 2008-10-13
Some more information
Why would an ethernet connection have a uuid?
How can I kill network manager forever and go with plain old ordinary networking?

Hardware testing shows 
Detecting your network controller(s):

Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)

Is this correct?
Testing your connection to the Internet:

No Internet connection

Are you connected to the Internet?

/etc/init.d/networking restart  gives

/var/cache/hwtest/submission.xml
 * Reconfiguring network interfaces...                                                                                     eth0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.


chelle@salems-lot:~$ sudo cat /etc/NetworkManager/system-connections/"Wired connection 1"

[connection]
id=Wired connection 1
uuid=aa8527a7-294c-4456-95fd-b924c285609e
type=802-3-ethernet
autoconnect=true
timestamp=0

[802-3-ethernet]
speed=0
duplex=full
auto-negotiate=true
mac-address=0;24;243;120;195;48;
mtu=0

[ipv4]
method=auto
ignore-auto-routes=false
ignore-auto-dns=false

---

