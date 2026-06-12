---
title: "installing network adapter driver."
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by hlekat on 2008-06-10
i have problem with my onboard network adapter. i tried many thinks but it did not work out. i download the official driver of the network adapter.

the motherboard is asus p5g - mx
the network adapter : attansic technology corp l2 100mbit ethernet adapter rev a0.
and the driver : [http://dlsvr02.asus.com/pub/ASUS/lan/Attansic/Attansic_L2_Linux.rar](http://dlsvr02.asus.com/pub/ASUS/lan/Attansic/Attansic_L2_Linux.rar)

i have some difficulty to setup the driver.
i suppose i have to use the Makefile which is in the src folder but i don't know how to do it.

can anyone help me ? thanks

---

### Post by hal10000 on 2008-06-10
Maybe you don't have to compile and install a driver ba your own, because it is already provided by ubuntu.

Try (on a command line):
> lsmod | grep atl2
if you get an answer, then your network module driver is already loaded and you can configure it with your network manager.
If you don't get an answer, then try to load it manually with the command [COLOR="Red"]sudo modprobe atl2[/COLOR]. If it works, then you will get no answer, only if something went wrong, modprobe will complain. You can verify if the driver is loaded by doing again [COLOR="Red"]lsmod | grep atl[/COLOR] and if it is ok. configure it with network-manager.
If this doesn't work, then you may post the output of the following commands:

1. lspci -nn
2. sudo lshw -C network
3. ifconfig

---

