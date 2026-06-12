---
title: "Ubuntu doesn't see my SATA devices"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by AustinMatherne on 2008-09-16
I built a new computer on the Intel P45 platform.  Problem is, when I try to install Ubuntu, I get a menu with a selection of SATA drivers because it can't find a hard drive.  The SATA controller is a Intel ICH10R.

It also can't connect to the network with the embedded NIC. The NIC is a Realtek RTL8111C.

Thanks,
~ Austin
P.S. OpenSUSE 11.0 installs just fine.

---

### Post by AustinMatherne on 2008-09-16
Well, it would appear I need the 2.6.26 kernel for my Ethernet controller to work.

Is it possible to add an updated kernel to the Ubuntu 8.04, 64 bit alternate install CD?

Thanks,
~ Austin

---

### Post by AustinMatherne on 2008-09-16
I'm gathering from the lack of responses, that this is just another thing to add on to the long list of incompatibility's with Ubuntu...  Or am I wrong?

---

### Post by manishtech on 2008-09-16
First lets us know whether your NIC is detected or not.
While running in LiveCD mode, goto terminal and type this command
```
lspci| grep -i ethernet
```

---

### Post by AustinMatherne on 2008-09-16
```
lspci| grep -i ethernet
```

Outputs

```
03:00.0 Ethernet controller: Realtek Semiconductor Co... Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

---

### Post by gregphil on 2008-09-16
This is probably not your problem, but it slowed me down trying to install ubuntu for a few hours:
 
On my ASUS motherboard, ubuntu was not "seeing" the SATA drives, but did see the IDE drive.   After much research I found it ws necessary to go into the BIOS and (get this) add each of the SATA disks to a separate "RAID array", even though I was not using them as a RAID array.  Also note that I needed to create a separate RAID "array" for each SATA disk and only put one (1) disk in each "array".  As strange as this sounds I was desperate, so I tried it and it worked.
 
Once I did this the motherbaord BIOS was willing to report the SATA disks existed to ubuntu and ubuntu was willing to use them, install, and boot from them.
 
As I said this is probably not your problem, but you might look around in the BIOS and see if you need to do anything to "enable" SATA support.
 
Good Luck.

---

### Post by AustinMatherne on 2008-09-17
I reinstalled Windows XP, enabled Wake on LAN for the NIC, and the Ethernet controller works.

I went into the BIOS and changed the SATA#1 Configuration from IDE to AHCI.  So everything seems to be working fine.  Now, I just need to cross my fingers and hope the audio over HDMI for my 4870 works.


Thanks,
~ Austin

---

### Post by AustinMatherne on 2008-09-17
> **AustinMatherne said:**
> I reinstalled Windows XP, enabled Wake on LAN for the NIC, and the Ethernet controller works.

Well... It was working, until I had to reboot.

Any ideas?

Thanks,
~ Austin
P.S.  Can someone move this over to "Networking & Wireless"?

---

