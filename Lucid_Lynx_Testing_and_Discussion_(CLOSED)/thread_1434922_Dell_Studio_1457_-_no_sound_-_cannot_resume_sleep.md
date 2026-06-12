---
title: "Dell Studio 1457 - no sound - cannot resume sleep"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by myddewji13 on 2010-03-20
Hi guys, 

The lucid beta looks good and I love it overall. However I was wondering if anyone knows how to get my sound working. Below is lspci output:

```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
[COLOR="Red"]00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)[/COLOR]
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
02:00.1 Audio device: ATI Technologies Inc RV710/730
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
06:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
```

Also, the machine cannot resume from sleep (REISUB trick does not work to shut comp down, have to hold down power button). Sleep isn't too bad right now (but I hope its fixed for the final release) but getting audio would be really nice...

---

### Post by myddewji13 on 2010-03-20
UPDATE:

Got the sound working using the following fix from here: [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/93857]("https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/93857")

The instuctions are as follows:
```
solution for realtek codec 665

remove alsa-base and alsa-utils

install driver of the realtek Linux driver (2.6) 5.14rc2
http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false

extract alsa-driver, alsa-lib, alsa-utils

alsa-driver:
$./configure --with-cards=hda-intel --with-card-options=hda-codec-realtek
$make
#make install

alsa-lib:
$./configure
$make
#make install

alsa-utils (dependencies ncurse, gettext):
$./configure
$make
#make install

run command alsaconf e reboot system.

hug,
```
I started off by removing alsa-base and alsa utils by running the command:
```
sudo apt-get remove alsa-base alsa-utils 
```
I couldn't get alsa-utils to configure (couldnt get ncurses etc,,) and so I just typed in 'sudo apt-get install alsa-utils'. I also didn't run alsaconf...but on reboot I had sound.(headphones and mic work too :D )  

Now for the sleep issue....help anyone?

---

### Post by myddewji13 on 2010-03-21
Update:
Sleep seems to be related to the ATI drivers. I installed the fglrx (ubuntu3) version but cannot enable compiz anymore. However, the computer sleeps fine and now wakes up...will continue to try getting this working

PS
my wireless refuses to work every other boot..weird...

---

### Post by myddewji13 on 2010-03-21
Sleep fixed with new ATI drivers :D

---

