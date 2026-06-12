---
title: "Most recent updates broke wifi?"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by spotdog14 on 2009-04-01
Alright, I just got my new laptop (Dell XPS Studio 13) and installed Ubuntu 64bit and did all the updates and then rebooted and can no longer connect to my WAP, I can still in Vista so I think something might be screwy, anyone have any ideas?

The card that it uses is a Dell 1515 Wireless N Mini-Card. 

Thanks for any help you might give me.

---

### Post by mariner09 on 2009-04-02
You might want to enable backports in synaptic and make sure you add backports for your kernel flavor.  Do you know what chipset the Dell wireless is?

---

### Post by novafluxx on 2009-04-02
I have an Inspiron 1318 myself, and the same Wifi card, no issues here. Seriously though, try powercycling your wireless access point [router/modem]. I had the opposite issue, where it wouldn't connect in Windows, but would in Ubuntu.

I powercycled and wala...success.

If worse comes to worse, delete the saved wireless connection and recreate it.

---

### Post by spotdog14 on 2009-04-02
> **novafluxx said:**
> I have an Inspiron 1318 myself, and the same Wifi card, no issues here. Seriously though, try powercycling your wireless access point [router/modem]. I had the opposite issue, where it wouldn't connect in Windows, but would in Ubuntu.

I powercycled and wala...success.

If worse comes to worse, delete the saved wireless connection and recreate it.

I think I found the problem, instead of using the US Ubuntu mirror for updates I was using the fastest and it looks like that mirrir did not have any updates for anything....

So I am at work right now plugged into ethernet and doing a lot of updates so we will see how that goes.

I did power cycle the AP a few times and the card, it would just sit there and kept asking for the encryption key.

Thanks though guys for the advice, I will keep you informed if this fixed it. Also I am not sure what the chipset in the wifi device is, I have read that its Atheos and Broadcom so im not really sure.

---

### Post by Reiger on 2009-04-02
If it is a PCI device: lspci should tell. If it is an USB device: lsusb. Of course you can try sudo lshw -C network to find out as well.

---

### Post by spotdog14 on 2009-04-02
> **Reiger said:**
> If it is a PCI device: lspci should tell. If it is an USB device: lsusb. Of course you can try sudo lshw -C network to find out as well.

```

00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
01:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:07.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9200M GS (rev a1)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 9400M G (rev b1)
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

Its really strange, after I did the updates I restarted and it worked fine, then I did some other things and had to restart and now it is in its endless loop of trying to connect asking for key not connecting, etc. 

Anywho thats where I am right now.

---

### Post by spotdog14 on 2009-04-02
> **novafluxx said:**
> I have an Inspiron 1318 myself, and the same Wifi card, no issues here. Seriously though, try powercycling your wireless access point [router/modem]. I had the opposite issue, where it wouldn't connect in Windows, but would in Ubuntu.

I powercycled and wala...success.

If worse comes to worse, delete the saved wireless connection and recreate it.

Did network manager get updated or something? What version are you using.

And what is the name of the driver I would look for in synaptic?

Thanks!

Also I know the encryption keys are handled by the gnome-keyring thingy, but when I fire up the Passwords and Encryption Keys (I think that is where I would access it) I get a message at the bottom saying "the gnome-keyring daemon is not running." 

Would that have something to do with it?

---

### Post by spotdog14 on 2009-04-02
Alright I have figured it out....

Every now and then the gnome-keyring-daemon does not start or does not start correctly which causes me to not be able to connect to my encrypted wifi networks. I reinstalled the above package and hopefully it will solve the problem.

---

### Post by tad1073 on 2009-04-02
I am having similar issues with wireless connection.

```
description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: wmaster0
       version: 01
       serial: 00:21:91:06:37:28
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.0.102 latency=168 
       module=ath9k multicast=yes wireless=IEEE 802.11bgn
```I used the work-around that was suggested and it works but I should not have to use it.

> **novafluxx said:**
> 

If worse comes to worse, delete the saved wireless connection and recreate it.

I have reported bugs to Network Manager through bugzilla but have not checked if it has been addressed.

---

### Post by spotdog14 on 2009-04-02
> **tad1073 said:**
> I am having similar issues with wireless connection.

```
description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: wmaster0
       version: 01
       serial: 00:21:91:06:37:28
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.0.102 latency=168 
       module=ath9k multicast=yes wireless=IEEE 802.11bgn
```I used the work-around that was suggested and it works but I should not have to use it.



I have reported bugs to Network Manager through bugzilla but have not checked if it has been addressed.

Which workaround were you referring to? 

My problem was that gnome-keyring-daemon was not starting with the system which made it impossible to connect to an encrypted network. I reinstalled the package and so far after 5 reboots it as been fine.

---

### Post by tad1073 on 2009-04-02
The one I quoted from Novaflux.

It is in my post.

---

