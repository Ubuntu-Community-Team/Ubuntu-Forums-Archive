---
title: "VMware Player Install ERROR"
date: 2006-09-22
forum: Installation &amp; Upgrades
---

### Post by Chazall1 on 2006-09-22
I had the VMware Player installed and working until the new update of the Kernel. I gor an error message stating that the vmmon was not installed. I removed the VMware player and reinstalled it. I am getting this Errom message, "Configuring bridge network for vmnet0
configuring a NAT network for vmnet8
Probing for an unusual private subnet.......
The subnet 192.168.41.0/255.255.255.0 appears to be used.
Configuring a host-only network for vmnet1.
Probing for an unusual private subnet
Subnet 172.161.147.1/255.255.255.0 appears to be used
Starting VMware services:
Virtual mach monitor              Failed
Virtual ethernet                  Failed
invoke-rc.d: initscript vmware-player, action start failed.
dpkg: error processing vmware-player (--configure)
E: Sub-process /usr/bin/dpkg returned an error exit status 1
A package failed to install.

I have tried loading this several times, Can anyone assist me in getting the VMware-Player to function??????

Thanks

---

### Post by evilpig on 2006-10-02
This exact same thing happened to me today... 

> Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.60.0/255.255.255.0 appears to be unused.

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.166.0/255.255.255.0 appears to be unused.

Starting VMware services:
   Virtual machine monitor                                       failed
   Virtual ethernet                                              failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by diggity on 2006-10-02
Make sure you have the vmware-player-kernel-modules for your kernel version. The linux kernel headers don't seem to work.

---

