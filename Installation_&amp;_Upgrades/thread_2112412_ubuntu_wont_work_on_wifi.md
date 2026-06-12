---
title: "ubuntu wont work on wifi"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by mrjuanfrusciante on 2013-02-04
hi everyone! I'm new on ubuntu and since I installed it i have an issue with my wifi...

I installed ubuntu 12.10 and download the additional drivers for my wifi... the wifi light is on it connects t the wifi signal but won't connect to the internet... It can't be the internet conecction because i'm using it right now with another computer...thanks in advance

---

### Post by superchar42 on 2013-02-04
Are you using WEP or WPA?

---

### Post by mrjuanfrusciante on 2013-02-04
i believe it is wep

---

### Post by ahallubuntu on 2013-02-04
~

---

### Post by mrjuanfrusciante on 2013-02-04
my card is broadcom, I reiinstalled the driver but now the weird thing is wifi doesnt work until I connect my ethernet cable and disconect it..what is wrong? lol

---

### Post by ahallubuntu on 2013-02-04
~

---

### Post by mrjuanfrusciante on 2013-02-04
descripción: Interfaz inalámbrica
       producto: BCM4312 802.11b/g LP-PHY
       fabricante: Broadcom Corporation
       id físico: 0
       información del bus: pci@0000:09:00.0
       nombre lógico: eth1
       versión: 01
       serie: 00:26:82:38:6f:be
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=wl0 driverversion=5.100.82.112 ip=192.168.1.80 latency=0 multicast=yes wireless=IEEE 802.11bg
       recursos: irq:18 memoria:91100000-91103fff
  *-network
       descripción: Ethernet interface
       producto: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:0a:00.0
       nombre lógico: eth0
       versión: 02
       serie: 00:26:22:a4:09:88
       tamaño: 10Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       recursos: irq:44 ioport:2000(size=256) memoria:91010000-91010fff memoria:91000000-9100ffff memoria:91020000-9103ffff
juanaguirre@JuanjAguirrelaptop:~$ rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
juanaguirre@JuanjAguirrelaptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:227  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

---

