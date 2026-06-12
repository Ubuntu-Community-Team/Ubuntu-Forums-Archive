---
title: "Installing Ubuntu on a laptop for sale"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by foxy123 on 2011-08-07
I'd like to try to sell my old laptop. Although it's unlikely that somebody would like to buy and even more unlikely that this person would like to have Xubuntu on it I still want to do a clean install. The only question is how should I configure the user name. I mean if a buyer would like to keep Xubuntu but change the name how it is done? What do you have when you for example buying a Dell laptop with Ubuntu pre-installed?

---

### Post by jmszr on 2011-08-07
foxy123,

I believe the alternate install version gives you the option to do an OEM install. That will allow the end-user to input their own user name and password: [http://cdimage.ubuntu.com/xubuntu/releases/lucid/release/](http://cdimage.ubuntu.com/xubuntu/releases/lucid/release/). You will need to add xubuntu-desktop to the alternate install's cli only install.
This is for Ubuntu but it will give you the idea: [https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview) .

Or, you could just do a regular install: [http://www.xubuntu.org/get#lucid](http://www.xubuntu.org/get#lucid) and have them change the password and user name: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword).

Edit: I used 10.04 as best for a person new to (X)Ubuntu. You might decide otherwise, of course.

Hope that helps.

---

### Post by foxy123 on 2011-08-07
Just for those who might be interested in this laptop, it is an old NEC Versa M400 with 768Mb memory:
```
~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
08:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0a:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
0a:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
0a:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
0a:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
0a:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

```

Oh, I have already found the answer: OEM mode.

---

### Post by foxy123 on 2011-08-07
> **jmszr said:**
> foxy123,

I believe the alternate install version gives you the option to do an OEM install. That will allow the end-user to input their own user name and password: [http://cdimage.ubuntu.com/xubuntu/releases/lucid/release/](http://cdimage.ubuntu.com/xubuntu/releases/lucid/release/). You will need to add xubuntu-desktop to the alternate install's cli only install.

Or, you could just do a regular install: [http://www.xubuntu.org/get#lucid](http://www.xubuntu.org/get#lucid) and have them change the password and user name: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword).

Hope that helps.

Oh, thanks a lot. I did not know about password reset.

---

