---
title: "Proble with my wireless connection"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by Yotta15 on 2012-05-26
Hello,

My laptop doesn't detect wireless connection :(

I followed the instructionthat I found in ([http://ubuntuforums.org/showthread.php?t=1593717](http://ubuntuforums.org/showthread.php?t=1593717))  :
sudo apt-get --purge remove firmware-b43-installer
sudo apt-get --purge remove dkms
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo reboot

when installing the bcmwl-kernel-source I had this fata error :
[COLOR=Blue][B][In file included from /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/shared/linux_osl.c:19:
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/include/linuxver.h:23: fatal error: linux/autoconf.h: Aucun fichier ou dossier de ce type
compilation terminated.
make[1]: *** [/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/shared/linux_osl.o] Erreur 1
make: *** [_module_/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build] Erreur 2
make: quittant le répertoire « /usr/src/linux-headers-2.6.35-22-generic »][/B][/COLOR]

[COLOR=Black]Can you help me plzzzz :confused: 

best regards 
[/COLOR]

---

### Post by Bucky Ball on 2012-05-26
Welcome. Run this in a terminal:

```
sudo lshw -C network
```That will show the card and if you have drivers installed. Have you plugged in and gotten online with an ethernet cable, gotten updates then checked 'Additional Drivers'? If not, do that and post back the result of that command I gave.

If the update doesn't work, install 'b43-fwcutter' and 'firmware-b43-installer' then reboot. (You don't say what release you are using so install these with Synaptic Package Manager or Software Centre.)

Most Broadcom work 'out of the box' nowadays so don't try anything else until you have done the above else you may make things more complicated than need be. ;)

---

### Post by Yotta15 on 2012-05-26
Hi ,,

Thank you for your help :p
I runs the command 
sudo lshw -C networkIt shows this lines : [COLOR=Blue]
*-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f8000000-f8003fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:fc:49:1f
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=sb v2.17 ip=192.168.1.7 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:49 memory:fc100000-fc10ffff[/COLOR]


[COLOR=Black]In fact I installed ubuntu 10.10 in Dell studio 1555..
I Also cheeked additional pilot  and I  fount that the driver for wireless connection"package contains Broadcom 802.11 Linux STA wireless"  is off . But I tried to activate it . I had this error "SystemError: installArchives() failed" 

I also installed [/COLOR]'b43-fwcutter' and 'firmware-b43-installer'  ==> same pb with wireless connection :(

---

### Post by Yotta15 on 2012-05-26
in fat when I try to install b43-fwcutte , I got this error 

E: bcmwl-kernel-source: le sous-processus script post-installation installé a retourné une erreur de sortie d'état 10

did you have idea about this ??

---

### Post by Bucky Ball on 2012-05-26
Can you get online with a cable and get updates?

---

### Post by Yotta15 on 2012-06-05
> **Bucky Ball said:**
> Can you get online with a cable and get updates?

Hello,

Yes I can get online with cable but which tasks should I do ??? What did you mean by "get updates" ??

---

### Post by Bucky Ball on 2012-06-05
Open update manager, with the cable in, check for updates.

Go to 'Additional Drivers' and see if you have the B43 driver in there. 

Right click the network icon and see if your wireless network shows up. Do any wireless networks show? Also make sure 'Enable Wireless' is ticked.

After installing the B43 driver, if it is there, you may need to restart to get it happening.

---

