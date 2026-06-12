---
title: "Configuring Dual Ethernet with UEC 10.4"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by mcaughey on 2010-08-09
I have installed Unbuntu 10.4 Cloud Server.  I have two servers:
  Front End Server (clound-fe):
  [FONT=Symbol]·         [/FONT]2 Dual Core 32 bit Xeon processors (They do not support Virtualization)
  [FONT=Symbol]·         [/FONT]2 Ethernet Ports
  [FONT=&quot]o   [/FONT]eth0 – used for public connectivity (100 Mbit)
  [FONT=Wingdings]§  [/FONT]IP Address 192.168.3.30
  [FONT=Wingdings]§  [/FONT]Network 192.168.3.0
  [FONT=Wingdings]§  [/FONT]Netmask 255.255.255.0
  [FONT=Wingdings]§  [/FONT]Gateway 192.168.3.1
  [FONT=&quot]o   [/FONT]eth1 – used for public connectivity  (Gigabit Lan)
  [FONT=Wingdings]§  [/FONT]IP Address 192.168.4.30
  [FONT=Wingdings]§  [/FONT]Network 192.168.4.0
  [FONT=Wingdings]§  [/FONT]Netmask 255.255.255.0
  [FONT=Symbol]·         [/FONT]I loaded everything except the node controller
  [FONT=Symbol]·         [/FONT]I set up the cluster  (cloud-nine) so that is will use the IP Range it will use 192.168.3.100 – 192.168.3.250
  Node Controller (cloud-nc-1)
  [FONT=Symbol]·         [/FONT]4 Dual Core 64 bit Xeon Hyper-Threading processors that do support Virtualization
  [FONT=Symbol]·         [/FONT]2 Ethernet Ports
  [FONT=&quot]o   [/FONT]eth0 – used for public connectivity (100 Mbit)
  [FONT=Wingdings]§  [/FONT]IP Address 192.168.3.31
  [FONT=Wingdings]§  [/FONT]Network 192.168.3.0
  [FONT=Wingdings]§  [/FONT]Netmask 255.255.255.0
  [FONT=Wingdings]§  [/FONT]Gateway 192.168.3.1
  [FONT=&quot]o   [/FONT]eth1 – used for public connectivity  (Gigabit Lan)
  [FONT=Wingdings]§  [/FONT]IP Address 192.168.4.31
  [FONT=Wingdings]§  [/FONT]Network 192.168.4.0
  [FONT=Wingdings]§  [/FONT]Netmask 255.255.255.0
  [FONT=Symbol]·         [/FONT]I told the installation about the cloud-fe server so the list of available components was fewer and I installed them all on this one.
  [FONT=Symbol]·         [/FONT]I didn’t set up a cluster here, Should I have?
   
  I saw that the eth1 was set up to point to the bridge that was configure in the /etc/network/interfaces so I made it static:
  cloud-fe /etc/network/interfaces:
   
  [FONT=&quot]auto lo[/FONT]
  [FONT=&quot]iface lo inet loopback[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]auto eth0[/FONT]
  [FONT=&quot]iface eth0 inet static[/FONT]
  [FONT=&quot]        address 192.168.3.30[/FONT]
  [FONT=&quot]        netmask 255.255.255.0[/FONT]
  [FONT=&quot]        network 192.168.3.0[/FONT]
  [FONT=&quot]        broadcast 192.168.3.255[/FONT]
  [FONT=&quot]        gateway 192.168.3.1[/FONT]
  [FONT=&quot]        dns-nameservers 4.2.2.1 4.2.2.4[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]auto eth1[/FONT]
  [FONT=&quot]iface eth1 inet static[/FONT]
  [FONT=&quot]        address 192.168.4.30[/FONT]
  [FONT=&quot]        netmask 255.255.255.0[/FONT]
  [FONT=&quot]        network 192.168.4.0[/FONT]
  [FONT=&quot]        broadcast 192.168.4.255[/FONT]
   
  cloud-nc-1 /etc/network/interfaces
  [FONT=&quot]auto lo[/FONT]
  [FONT=&quot]iface lo inet loopback[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]auto eth0[/FONT]
  [FONT=&quot]iface eth0 inet static[/FONT]
  [FONT=&quot]        address 192.168.3.31[/FONT]
  [FONT=&quot]        netmask 255.255.255.0[/FONT]
  [FONT=&quot]        network 192.168.3.0[/FONT]
  [FONT=&quot]        broadcast 192.168.3.255[/FONT]
  [FONT=&quot]        gateway 192.168.3.1[/FONT]
  [FONT=&quot]        dns-nameservers 4.2.2.1 4.2.2.4[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]auto eth1[/FONT]
  [FONT=&quot]iface eth1 inet static[/FONT]
  [FONT=&quot]        address 192.168.4.31[/FONT]
  [FONT=&quot]        netmask 255.255.255.0[/FONT]
  [FONT=&quot]        network 192.168.4.0[/FONT]
  [FONT=&quot]        broadcast 192.168.4.255[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Cloud-fe  /etc/eucalyptus/eucalyptus.conf[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# /etc/eucalyptus/eucalyptus.conf[/FONT]
  [FONT=&quot]#[/FONT]
  [FONT=&quot]# These are the Ubuntu Enterprise Cloud's default Eucalyptus parameters.[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# Affects: All[/FONT]
  [FONT=&quot]# See: **NOTE** below[/FONT]
  [FONT=&quot]EUCALYPTUS="/"[/FONT]
  [FONT=&quot]EUCA_USER="eucalyptus"[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# Affects: CLC, Walrus, SC[/FONT]
  [FONT=&quot]DISABLE_DNS="Y"[/FONT]
  [FONT=&quot]DISABLE_ISCSI="Y"[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# Affects: CC, NC[/FONT]
  [FONT=&quot]# See: **NOTE** below[/FONT]
  [FONT=&quot]ENABLE_WS_SECURITY="Y"[/FONT]
  [FONT=&quot]LOGLEVEL="DEBUG"[/FONT]
  [FONT=&quot]VNET_PUBINTERFACE="eth0"[/FONT]
  [FONT=&quot]VNET_PRIVINTERFACE="eth1"[/FONT]
  [FONT=&quot]VNET_MODE="MANAGED-NOVLAN"[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# Affects: CC[/FONT]
  [FONT=&quot]# See: **NOTE** below[/FONT]
  [FONT=&quot]CC_PORT="8774"[/FONT]
  [FONT=&quot]SCHEDPOLICY="ROUNDROBIN"[/FONT]
  [FONT=&quot]POWER_IDLETHRESH="300"[/FONT]
  [FONT=&quot]POWER_WAKETHRESH="300"[/FONT]
  [FONT=&quot]NC_SERVICE="axis2/services/EucalyptusNC"[/FONT]
  [FONT=&quot]VNET_DHCPDAEMON="/usr/sbin/dhcpd3"[/FONT]
  [FONT=&quot]VNET_DHCPUSER="dhcpd"[/FONT]
  [FONT=&quot]NODES=""[/FONT]
  [FONT=&quot]VNET_ADDRSPERNET="32"[/FONT]
  [FONT=&quot]#VNET_SUBNET=""[/FONT]
  [FONT=&quot]#VNET_NETMASK=""[/FONT]
  [FONT=&quot]#VNET_DNS=""[/FONT]
  [FONT=&quot]#VNET_PUBLICIPS=""[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# Affects: NC[/FONT]
  [FONT=&quot]NC_PORT="8775"[/FONT]
  [FONT=&quot]HYPERVISOR="kvm"[/FONT]
  [FONT=&quot]MANUAL_INSTANCES_CLEANUP=0[/FONT]
  [FONT=&quot]VNET_BRIDGE="br0"[/FONT]
  [FONT=&quot]INSTANCE_PATH="/var/lib/eucalyptus/instances/"[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Cloud-nc-1 /etc/eucalyptus/eucalyptus.conf[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# /etc/eucalyptus/eucalyptus.conf[/FONT]
  [FONT=&quot]#[/FONT]
  [FONT=&quot]# These are the Ubuntu Enterprise Cloud's default Eucalyptus parameters.[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# Affects: All[/FONT]
  [FONT=&quot]# See: **NOTE** below[/FONT]
  [FONT=&quot]EUCALYPTUS="/"[/FONT]
  [FONT=&quot]EUCA_USER="eucalyptus"[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# Affects: CLC, Walrus, SC[/FONT]
  [FONT=&quot]DISABLE_DNS="Y"[/FONT]
  [FONT=&quot]DISABLE_ISCSI="Y"[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# Affects: CC, NC[/FONT]
  [FONT=&quot]# See: **NOTE** below[/FONT]
  [FONT=&quot]ENABLE_WS_SECURITY="Y"[/FONT]
  [FONT=&quot]LOGLEVEL="DEBUG"[/FONT]
  [FONT=&quot]VNET_PUBINTERFACE="eth0"[/FONT]
  [FONT=&quot]VNET_PRIVINTERFACE="eth1"[/FONT]
  [FONT=&quot]VNET_MODE="MANAGED-NOVLAN"[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# Affects: CC[/FONT]
  [FONT=&quot]# See: **NOTE** below[/FONT]
  [FONT=&quot]CC_PORT="8774"[/FONT]
  [FONT=&quot]SCHEDPOLICY="ROUNDROBIN"[/FONT]
  [FONT=&quot]POWER_IDLETHRESH="300"[/FONT]
  [FONT=&quot]POWER_WAKETHRESH="300"[/FONT]
  [FONT=&quot]NC_SERVICE="axis2/services/EucalyptusNC"[/FONT]
  [FONT=&quot]VNET_DHCPDAEMON="/usr/sbin/dhcpd3"[/FONT]
  [FONT=&quot]VNET_DHCPUSER="dhcpd"[/FONT]
  [FONT=&quot]NODES=""[/FONT]
  [FONT=&quot]VNET_ADDRSPERNET="32"[/FONT]
  [FONT=&quot]#VNET_SUBNET=""[/FONT]
  [FONT=&quot]#VNET_NETMASK=""[/FONT]
  [FONT=&quot]#VNET_DNS=""[/FONT]
  [FONT=&quot]#VNET_PUBLICIPS=""[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]# Affects: NC[/FONT]
  [FONT=&quot]NC_PORT="8775"[/FONT]
  [FONT=&quot]HYPERVISOR="kvm"[/FONT]
  [FONT=&quot]MANUAL_INSTANCES_CLEANUP=0[/FONT]
  [FONT=&quot]VNET_BRIDGE="br0"[/FONT]
  [FONT=&quot]INSTANCE_PATH="/var/lib/eucalyptus/instances/"[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Now I realize that the reference to the bridge was there for the hypervisor kvm needs to use, or so I think it was.  I removed it.[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Question:[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]1.  [/FONT][FONT=&quot]How should I have configured the interfaces in order to support the hypervisor, one public network eth0 and one private network for the cloud to use? [/FONT]
  [FONT=&quot]2.  [/FONT][FONT=&quot]Do I need to change the configuration in the eucalyptus.conf?  At this point it is stock I have not made any changes.[/FONT]


Thank you in advance,
Michael

---

### Post by mcaughey on 2010-08-10
If I use the following:
[SIZE=2]auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet manual
 
auto br0
iface br0 inet static
     address 192.168.3.30
     network 192.168.3.0
     netmask 255.255.255.0
     broadcast 192.168.3.255
     gateway 192.168.3.1
     bridge_ports eth0
     bridge_stp off
     bridge_fd 0
     bridge_maxwait 0
[/SIZE]
 
Do I need to do the same for eth1?  Do I create a new bridge?  I realize the bridge is for communicating from the VM to the ethernet connection.  If not then what specifically is the value in having a seperate private ethernet connection the cloud?  What do I need to do to make use of it?

---

