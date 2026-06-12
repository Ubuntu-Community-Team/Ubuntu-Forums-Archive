---
title: "Netplan and VLAN"
date: 2019-06-25
forum: Installation &amp; Upgrades
---

### Post by zsun7 on 2019-06-25
Ubuntu server 18.04.2 LTS Bionic - on vmware

Hello,

Sorry i'm rookie , i need to put the EN160 network card in the **VLAN10 TAG** with NETPLAN.
But it does not work ..


  IP: 192.168.44.96/24
  Gateway : 192.168.44.254
  VLAN10 TAGGED



  # This file describes the network interfaces available on your system
  # For more information, see netplan(5).
  
> 
network:

    version: 2
    renderer: networkd
    ethernets:
      enp0s3:
  #      dhcp4: yes
      ens160:
   #     dhcp4: no
   
  vlans:
  vlan.10:
  id : 10
  link: ens160
  dhcp4: no
  address: [192.168.44.96/24]
  gateway: 192.168.44.254
  nameservers: zs.local


   
  
Do you have an idea?

Best regards

Paul.

---

### Post by TheFu on 2019-06-25
The indentation is all off, netplan is YAML which cares very much about indentation consistency.
Perhaps you need _code tags_ to show it here correctly?  Can't see anything without proper indentation.
[https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168) explains how.

---

