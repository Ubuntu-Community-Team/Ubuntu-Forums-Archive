---
title: "pci problem while booting"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by m-tarek on 2009-09-17
Hi,
I'm using alpha5 and I have problem with booting. when I choose to boot to ubuntu, two lines show up before "starting up" one of them:
```
[0.773359] pci 0000:01:00.0 BAR 6 : no parent found for device [0×fffe0000-0×ffffffff]
```
It's not 100% correct because it last for 5 or 6 seconds then booting proceed.
I have HP Laptop 2.16 core2duo, 3MB cache, 3GB ram and boot time is 30 second!!!! I think it's a problem.
BTW I had some booting problems with jaunty (booting was 50second) but that problem was resolved with karmic.

---

### Post by clivejo on 2009-09-21
Open up a terminal and run the following command, basically lists PCI devices 

```
>lspci
```

Can you post the output?

---

### Post by m-tarek on 2009-09-22
I'm sorry for being late.:oops::oops:
```
tarek@tarek-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)
04:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
```

---

### Post by reijerh on 2009-09-23
Getting the same error message since I upgraded to the development branch yesterday (from 9.04). Also getting other errors that seems to be related to PCI:
> 
09/23/09 05:31:45 pm    kernel    [    0.312891] pci 0000:01:00.0: BAR 6: no parent found for of device [0xfff80000-0xffffffff]
09/23/09 05:31:45 pm    kernel    [    0.313117] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xd0000000-0xcfffffff] <-- this didn't show up on boot, only in the log.
09/23/09 05:31:45 pm    kernel    [    2.449582] e1000e 0000:00:19.0: pci_enable_pcie_error_reporting failed 0xfffffffb
> $ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)                                                                                   
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)                                                                                
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)                                                                                      
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)                                                                                  
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)                                                                                  
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)                                                                                  
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)                                                                                 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)                                                                                       
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)  
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)  
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)  
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96M [Quadro FX 770M] (rev a1)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300
86:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 06)
86:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 25)
86:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 14)
86:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 14)
86:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev bb)
86:09.5 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ff)


---

### Post by pjalegria on 2009-09-30
Same were :lolflag:, any fix?

---

### Post by novafluxx on 2009-09-30
Same problem here, I'm doing a reinstall of the beta tomorrow, so we'll see...

---

### Post by NCLI on 2009-09-30
Same here, seems like a bug...

---

### Post by m-tarek on 2009-10-01
> **NCLI said:**
> Same here, seems like a bug...
Yes I think, anyway I reported it at launchpad but again no fix.
here [[COLOR=Blue]https://bugs.launchpad.net/bugs/432164[/COLOR]]("https://bugs.launchpad.net/bugs/432164")

---

### Post by jonick on 2009-10-02
Hi Guys,

I have also had this problem on Alpha 5, I don't think the problem was there on Alpha 4. However, it is still there on the Beta.

Regards,

Jonick.

---

### Post by novafluxx on 2009-10-02
I wonder if this issue is in anyway related to my issue:

[http://ubuntuforums.org/showthread.php?t=1272184](http://ubuntuforums.org/showthread.php?t=1272184)

---

### Post by pjalegria on 2009-10-05
No fix yet???

---

### Post by VMC on 2009-10-05
Looks like this is what the pci error is referring to:
```
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)
```
I'm not getting that error and I don't have an nVidia chip.

---

### Post by FrancoNero on 2009-10-06
i have this other pci error about not being able to acces one or more USB devices and then terminal-style boot. i've never seen that supposedly fancy usplash stuff... ever...

where's the fix, there's like 20 topics and bug reports for these boot problems alreayd

---

### Post by pjalegria on 2009-10-06
I didnt find any... can you show me?

---

### Post by doudoufr on 2009-10-09
same pb here on a hp laptop :(

---

### Post by pjalegria on 2009-10-09
Fixed...:lolflag: Karmic rocks :guitar:

---

### Post by TrueJournals on 2009-10-09
> **pjalegria said:**
> Fixed...:lolflag: Karmic rocks :guitar:

Careful... While updates today did HIDE the message, the error is still there.  Check your dmesg.  You'll find the errors still occur, just are now hidden.  To quickly check:
```
dmesg | grep "no parent"
```

---

### Post by pjalegria on 2009-10-09
yeh, is true...

---

### Post by m-tarek on 2009-10-11
> **TrueJournals said:**
> Careful... While updates today did HIDE the message, the error is still there.  Check your dmesg.  You'll find the errors still occur, just are now hidden.  To quickly check:
```
dmesg | grep "no parent"
```
Yes, I think they just hide it in the boot. I did a full upgrade and I activate my graphic card, the problem has gone from the boot, but it still there when I run that command.

---

