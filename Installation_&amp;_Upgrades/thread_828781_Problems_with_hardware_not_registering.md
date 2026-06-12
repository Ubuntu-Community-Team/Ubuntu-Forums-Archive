---
title: "Problems with hardware not registering"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by Stolea on 2008-06-14
I got an AMD64/3000 on a Gigabyte GA-K8NSC-939 Motherboard with 2 gig ram, a ATI 9550 128mb Video card, 200G Sata for Ubuntu and 320G Sata for WinXp. The hardware works fine with XP, but under Ubuntu I have odd problems with drivers either not installing or not working.
I use Ubuntu 64bit 8.04 with the current patches. Could the fact that I can't get the ATI video driver or my UPS driver to recognize the relevant hardware. I tried other USB devices and they seem to work, but for some reason my UPS does not register.
Could it be that it is the 64bit version doesn't like the drivers???
Can anyone shed some light on this?

---

### Post by iaculallad on 2008-06-14
For unknown devices, you may want to run:

```
sudo update-pciids
```

---

### Post by Stolea on 2008-06-14
I did and this is the reply:

[COLOR="Blue"]--18:30:05--  [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 132,875 (130K) [text/plain]

100%[====================================>] 132,875       88.38K/s             

18:30:07 (88.13 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [132875/132875]

Done.
                                                                               
Broadcast Message from nut@shop                                                
        (somewhere) at 18:33 ...                                               
                                                                               
UPS mgeups@localhost is unavailable[/COLOR]

For some reason my UPS is not recognized. Any ideas?

---

### Post by iaculallad on 2008-06-14
Could you try posting the output of:

```
lspci
```

---

### Post by Stolea on 2008-06-14
This is the output:

[COLOR="Blue"]peter@shop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
02:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
02:07.1 Input device controller: Creative Labs SB Audigy LS Game Port
02:08.0 Modem: PCTel Inc HSP56 MicroModem (rev 04)
02:0b.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)[/COLOR]

---

### Post by iaculallad on 2008-06-14
It does not even display as an unknown device on lspci :confused::confused: Let's try to wait for other member's suggestions.

---

### Post by Stolea on 2008-06-14
I wonder if its something that has to do with this being the 64bit version???? Its like the UPS simply doesn't exist.
Got my network working though in a fashion. I now can use Places - Network to see my Office computer. But still no drives untill I manually enter the name of the drive after smb:///office/..... It then recognizes the drive and mount s it no worries. I added 
# //192.168.0.2/office /media/ibmpeers cifs credentials=~/.smbcredentials,dmask=777,fmask=777  0  0
//192.168.0.2/office_d /media/ofice_d cifs credentials=~/.smbcredentials,dmask=777,fmask=777  0  0

to the fstab file. But it doesn't automount. Must still be something missing.

All in all I think Ubuntu rocks!! :)

---

### Post by Stolea on 2008-06-15
Addendum:
I just set up the 32 bit version of Ubuntu 8.04 on a 40gig IDE on the same computer. The graphics now work properly with the ATI card and the UPS installed without any worries first try. My network even behaves itself, well almost.
It would appear that the 64bit version has still got some issues around drivers and/or peripheral devices.
There certainly is a difference in speed, but not enough to get exited about. This could also be effected by the type of disk, i.e. IDE or SATA.
Would this be just my perception, or is this based on fact?

---

