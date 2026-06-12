---
title: "Installed - Booted OK - But Not Again"
date: 2012-01-08
forum: Installation &amp; Upgrades
---

### Post by Hipster Doofus on 2012-01-08
Dual booting with windows 7 installed first. Grub is working OK.

After the initial install of ubuntu all went well. I rebooted, chose ubuntu & all I got was a black screen. Waited for a minute or two then used ctrl alt del & the system rebooted.

Tried again, this time it booted up into ubuntu.

Rebooted into ubuntu, again got the black screen, ctrl alt del, rebooted.

Back to ubuntu. This time I get a blinking cursor in the top left & [OK] near the centre of the screen.

Waited again, nothing. Ctrl alt del, & I saw something about 'update' flash on the screen.

Anybody know what's going on?

---

### Post by bluexrider on 2012-01-08
what distro are using? 

11.04, 11.10 or ?

---

### Post by Hipster Doofus on 2012-01-08
11.10. Sorry. Keep forgetting. :D

---

### Post by lincoln32 on 2012-01-08
several things can cause this so 1st boot a live ubuntu disk open a terminal
and type lspci and post the results so we can see what hardware you have.

---

### Post by Hipster Doofus on 2012-01-08
Here you go>

```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Cypress [Radeon HD 5800 Series]
01:00.1 Audio device: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series]
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
06:00.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
07:01.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
07:05.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
07:07.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
07:09.0 PCI bridge: PLX Technology, Inc. PEX 8608 8-lane, 8-Port PCI Express Gen 2 (5.0 GT/s) Switch (rev ba)
08:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
09:00.0 IDE interface: Marvell Technology Group Ltd. Device 914d (rev 10)
0c:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
ubuntu@ubuntu:~$ 
```

---

### Post by lincoln32 on 2012-01-08
I suspect it may be the ati video card but need to do some checking
if you can boot into the installed version go to top right drop down to systems settings then additional drivers and install any availible mean while I will check for other concerns

---

### Post by Hipster Doofus on 2012-01-08
Got back in. Tried to update the driver & it failed.

I used ATI/AMD proprietary FGLRX (post release updates). Told me to check jockey.log which I did & got another error, 'Could not recognize the subtitle format for jockey.log.'

Should I try installing the other ATI diver? The one without the post release updates?

---

### Post by lincoln32 on 2012-01-08
[http://askubuntu.com/questions/79416/black-screen-after-installing-ubuntu-11-10-amd-64-altenate-radeon-graphics-card](http://askubuntu.com/questions/79416/black-screen-after-installing-ubuntu-11-10-amd-64-altenate-radeon-graphics-card)

---

### Post by Hipster Doofus on 2012-01-08
Thanks. Seems to be OK now.

I could not get the information on that link to co-operate so I bit the bullet & chose to install the ATI diver without the post release updates.

This time it installed OK.

One more quick question. When I open a terminal - su. My password does not work. Am I doing something wrong? Still fairly new to the linux world.

---

### Post by lincoln32 on 2012-01-08
correct format is lincoln32@ubuntupc:~$ sudo su 
should return and ask for your password then $ will change to a # but I recommend to stay in user mode and not super user so you can double check before commiting changes:D

---

### Post by Hipster Doofus on 2012-01-08
Excellent. Thanks for your time & help lincoln32 & bluexrider for getting me started. :)__

---

