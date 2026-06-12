---
title: "GNU/Linux doesn't recognize integrated wireless card"
date: 2014-05-18
forum: Installation &amp; Upgrades
---

### Post by Ruben_Gonzalo_Sori on 2014-05-18
I've installed Poseidon 4.0 on my chinese netbook (atom processor - RAM 1GB- SSD 16GB) and on the network icon says "not  network devices"

Here is what it shows after lspci and lsusb:

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)


Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 148f:2070 Ralink Technology, Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I think is: "Bus 003 Device 002: ID 148f:2070 Ralink Technology, Corp." but don't know how to get the drivers or what...?
Please help me.

[edit]

this is what it shows when I type ifconfig and iwconfig:
[ifconfig]
lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:54 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:54 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:16105 (16.1 KB)  TX bytes:16105 (16.1 KB)

[iwconfig]
lo        no wireless extensions.

vboxnet0  no wireless extensions.

---

### Post by QIII on 2014-05-21
Duplicate of ubuntuforums.org/showthread.php?t=2224890

Closed.

---

