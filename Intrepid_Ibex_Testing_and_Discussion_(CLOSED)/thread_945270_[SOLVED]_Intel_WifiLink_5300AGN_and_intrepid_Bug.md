---
title: "[SOLVED] Intel WifiLink 5300AGN and intrepid: Bug?"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Fischli on 2008-10-12
Hi everybody

I was testing a Lenovo X200 with a Intel WifiLink 5300AGN with the daily Live-CD image (11.10.2008 ) of Intrepid. The card was recognized during boot and the driver/firmware was loaded but then an error occurred (see dmesg output below).

After that the card interface wlan0 was available, the wifi-led on the notebook was on but iwlist wlan0 scan did not return any results and ifconfig wlan0 up produced another error in the dmesg output.

I also did a 
```
sudo rmmod iwlang && sudo modprobe iwlagn
```
which resulted in the same output in dmesg as after boot.

I tested this both with the 32 and 64 bit versions, same result.

Did anybody get the card working properly? Or could this be a potential bug and should be reported?

dmesg after booting:

```
[ 250.503252] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[ 250.503258] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[ 250.503341] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 250.503380] iwlagn 0000:03:00.0: setting latency timer to 64
[ 250.503429] iwlagn: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[ 250.532152] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 250.541246] phy1: Selected rate control algorithm 'iwl-agn-rs'
[ 254.573157] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 254.575501] firmware: requesting iwlwifi-5000-1.ucode
[ 256.739716] Registered led device: iwl-phy1:radio
[ 256.740319] Registered led device: iwl-phy1:assoc
[ 256.740798] Registered led device: iwl-phy1:RX
[ 256.741262] Registered led device: iwl-phy1:TX
[ 257.240272] iwlagn: Error sending REPLY_ADD_STA: time out after 500ms.
```

iwlist:

```
ubuntu@ubuntu:~$ iwlist wlan0 scan
wlan0 No scan results 
```

ifconfig down/up, dmesg output:

```
[ 645.720676] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 645.750874] Registered led device: iwl-phy1:radio
[ 645.751440] Registered led device: iwl-phy1:assoc
[ 645.751907] Registered led device: iwl-phy1:RX
[ 645.752360] Registered led device: iwl-phy1:TX
[ 645.769197] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

lspci -v

```
03:00.0 Network controller: Intel Corporation Device 4236
Subsystem: Intel Corporation Device 1011
Flags: bus master, fast devsel, latency 0, IRQ 218
Memory at f2500000 (64-bit, non-prefetchable) [size=8K]
Capabilities: [c8] Power Management version 3
Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
Capabilities: [e0] Express Endpoint, MSI 00
Capabilities: [100] Advanced Error Reporting <?>
Capabilities: [140] Device Serial Number XX-XX-XX-XX-XX-XX-XX-XX
Kernel driver in use: iwlagn
Kernel modules: iwlagn
```

lshw -C network

```
*-network               

      description: Ethernet interface

      product: 82567LM Gigabit Network Connection

      vendor: Intel Corporation

      physical id: 19

      bus info: pci@0000:00:19.0

      logical name: eth0

      version: 03

      serial: XX:XX:XX:XX:XX:XX

      size: 10MB/s

      capacity: 1GB/s

      width: 32 bits

      clock: 33MHz


      capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation

      configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=half firmware=1.8-3 ip=192.168.1.15 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=10MB/s

 *-network

      description: Wireless interface

      product: Intel Corporation

      vendor: Intel Corporation

      physical id: 0

      bus info: pci@0000:03:00.0

      logical name: wmaster0

      version: 00

      serial: XX:XX:XX:XX:XX:XX

      width: 64 bits

      clock: 33MHz

      capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless

      configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

 *-network DISABLED

      description: Ethernet interface

      physical id: 2

      logical name: pan0


      serial: XX:XX:XX:XX:XX:XX

      capabilities: ethernet physical

      configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by Fischli on 2008-10-12
Two more things that I observed:
[LIST]
[*]The led which should indicate wireless activity, never flashes
[*]When I use the network manager to try to connect to an access point the dmesg error "ADDRCONF(NETDEV_UP): wlan0: link is not ready" does not appear anymore. But the network manager is also unable to scan for networks :-(
[/LIST]

Any help is appreciated!

---

### Post by pytheas22 on 2008-10-12
What is the PCI ID for your wireless card (if you don't know, please post here the output of 'lspci -nn')?

I thought I read yesterday of someone whose 5300 card did work on Intrepid with all of the latest updates applied.  Does it help if you apply all the updates, then reboot?

This device is definitely supposed to have support in Intrepid, both 32 and 64-bit.

---

### Post by Fischli on 2008-10-13
Thanks for your answer.

I think the PCI ID is 4236, but see the output of lspci -nn below. I also applied all updates and restarted.

Problem is still there.

lspci -nn output:

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:03.0 Communication controller [0780]: Intel Corporation Mobile 4 Series Chipset MEI Controller [8086:2a44] (rev 07)
00:03.2 IDE interface [0101]: Intel Corporation Mobile 4 Series Chipset PT IDER Controller [8086:2a46] (rev 07)
00:03.3 Serial controller [0700]: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection [8086:2a47] (rev 07)
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
03:00.0 Network controller [0280]: Intel Corporation Device [8086:4236]
```

---

### Post by pytheas22 on 2008-10-13
Yes, your PCI ID is 8086:4236.  Unfortunately, you appear to be the first person in the world to try to use this card on Ubuntu--if you google '8086:4236 ubuntu' the only result is this thread!

I know that there are other 5300 chipsets that should work on Intrepid, and your chipset is also supposed to be supported by iwlwifi.  So it's just a matter of working through whatever issues are preventing it from working.

You might want to take a look at this [Debian wiki]("http://wiki.debian.org/iwlwifi"); it has some suggestions for troubleshooting the card.

Unfortunately I'm really at a total loss to find any more information on this.  I would definitely recommend that you file a bug report at launchpad, since this does not seem to be an issue that anyone is addressing, probably because almost no one has this wireless card yet.  If you don't know how to do that, I can point you in the right direction.

---

### Post by klein on 2008-10-13
That's strange, I've got an X200 with a Intel Wireless 5300 card too, and it's worked perfectly out of the box ever since I installed one of the early Intrepid x64 alphas.

Anything I can do to help you out?  It may be silly, but is your wireless switch off?  (Left side forward)  I sometimes toggle it accidentally with my leg.  It should show a little green strip when on.

---

### Post by pytheas22 on 2008-10-13
klein: what's the PCI ID of your wireless card?  If you don't know, what is the output of the 'lspci -nn' command?

---

### Post by klein on 2008-10-13
The very same (you'd hope so; we have the same laptop):

03:00.0 Network controller [0280]: Intel Corporation Device [8086:4236]

---

### Post by pytheas22 on 2008-10-13
Well, that puts a new perspective on this.  Thanks for pointing it out.  I wonder which builds of the driver and kernel you're using and how they compare to those of the original poster.  What is the output of:
```

modinfo iwlagn
lshw -C Network
uname -a
```

Fischli, please post the same information.  Perhaps it's just a matter of updating (or possibly regressing) something to get it to work.  Also, of course, as klein mentioned, make sure that your wireless card is turned on.

---

### Post by klein on 2008-10-13
I'm sorry to say that it's worked with every 2.6.27 kernel I've used, including the current.  In fact, it was so reliable that I was able to get through the e1000e scare completely unaffected.  Here's uname -a:

Linux agamemnon 2.6.27-7-generic #1 SMP Fri Oct 10 03:55:01 UTC 2008 x86_64 GNU/Linux

Here's modinfo iwlagn:

filename:       /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2008 Intel Corporation
version:        1.3.27ks
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
srcversion:     D2AECFCE21BDB49D6298264
alias:          pci:v00008086d0000423Asv*sd*bc*sc*i*
alias:          pci:v00008086d00004237sv*sd*bc*sc*i*
alias:          pci:v00008086d00004236sv*sd*bc*sc*i*
alias:          pci:v00008086d00004235sv*sd*bc*sc*i*
alias:          pci:v00008086d00004232sv*sd*bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,cfg80211,mac80211
vermagic:       2.6.27-7-generic SMP mod_unload modversions 
parm:           disable50:manually disable the 50XX radio (default 0 [radio on]) (int)
parm:           swcrypto50:using software crypto engine (default 0 [hardware])
(bool)
parm:           debug50:50XX debug output mask (int)
parm:           queues_num50:number of hw queues in 50xx series (int)
parm:           qos_enable50:enable all 50XX QoS functionality (int)
parm:           11n_disable50:disable 50XX 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (int)
parm:           fw_restart50:restart firmware in case of error (int)
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart4965:restart firmware in case of error (int)

And here's sudo lshw -C Network:

  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:16:07:04:ac
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.8-3 ip=128.30.31.107 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=1GB/s
  *-network
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:b3:ac:da
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=128.30.5.111 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5a:5c:cd:fe:47:ba
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Fischli on 2008-10-14
Ok, strange that it works for some (all?) people except me. 
For the record: I installed XP and there the card works, so no hardware problem I guess.

uname -a is the same as for klein (except of course the host name):

```
Linux hemera-intrepid 2.6.27-7-generic #1 SMP Fri Oct 10 03:55:01 UTC 2008 x86_64 GNU/Linux 
```

modinfo iwlagn is EXACTLY the same as for klein (I used diff):

```

filename: /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
alias: iwl4965
license: GPL
author: Copyright(c) 2003-2008 Intel Corporation
version: 1.3.27ks
description: Intel(R) Wireless WiFi Link AGN driver for Linux
firmware: iwlwifi-4965-2.ucode
srcversion: D2AECFCE21BDB49D6298264
alias: pci:v00008086d0000423Asv*sd*bc*sc*i*
alias: pci:v00008086d00004237sv*sd*bc*sc*i*
alias: pci:v00008086d00004236sv*sd*bc*sc*i*
alias: pci:v00008086d00004235sv*sd*bc*sc*i*
alias: pci:v00008086d00004232sv*sd*bc*sc*i*
alias: pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias: pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias: pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias: pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias: pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias: pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias: pci:v00008086d00004230sv*sd*bc*sc*i*
alias: pci:v00008086d00004229sv*sd*bc*sc*i*
depends: iwlcore,cfg80211,mac80211
vermagic: 2.6.27-7-generic SMP mod_unload modversions
parm: disable50:manually disable the 50XX radio (default 0 [radio on]) (int)
parm: swcrypto50:using software crypto engine (default 0 [hardware]) 
(bool)
parm: debug50:50XX debug output mask (int)
parm: queues_num50:number of hw queues in 50xx series (int)
parm: qos_enable50:enable all 50XX QoS functionality (int)
parm: 11n_disable50:disable 50XX 11n functionality (int)
parm: amsdu_size_8K50:enable 8K amsdu size in 50XX series (int)
parm: fw_restart50:restart firmware in case of error (int)
parm: antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm: disable:manually disable the radio (default 0 [radio on]) (int)
parm: swcrypto:using crypto in software (default 0 [hardware]) (int)
parm: debug:debug output mask (int)
parm: disable_hw_scan:disable hardware scanning (default 0) (int)
parm: queues_num:number of hw queues. (int)
parm: qos_enable:enable all QoS functionality (int)
parm: 11n_disable:disable 11n functionality (int)
parm: amsdu_size_8K:enable 8K amsdu size (int)
parm: fw_restart4965:restart firmware in case of error (int)

```

For my lshw -C network output see my original post. The output there was also very similar to the output of klein. The only difference was that he had an IP address for the wireless network and I don't. 
@klein: I assume you get your IP from your access point.

```

< configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
---
> configuration: broadcast=yes driver=iwlagn ip=128.30.5.111 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

```

> **pytheas22 said:**
> ... I would definitely recommend that you file a bug report at launchpad...
If you don't know how to do that, I can point you in the right direction.

Ok, I will do that but I would be thankful if you could help with that (at least give me some pointers where to find information about how to do that, what information to include and so on). Thanks in advance.

---

### Post by Fischli on 2008-10-14
A few notes about the kill switch and the LED:
- Kill switch is off
- The LED for wifi is on but never flashes (also not when I scan for networks)
- When I turn the kill switch on the led goes of and dmesg says:
```
Kill switch must be turned off for wireless networking to work
```
when I turn the kill switch off, the LED goes on again

I think this behaviour is correct and is not causing the problem.

Any more ideas?

---

### Post by Fischli on 2008-10-14
:):):):):)

Problem solved. See below.

All access points I tested are using Channel 12 (2467Mhz) to communicate (I don't know why but it's like that). 

I did a iwlist wlan0 channel and only got 11 channels (in the 2.4Ghz spectrum) including nb. 11 with 2462Mhz. 

I changed the channel to 11 for the access point I have administrative rights and voilà it works.

Thanks for your help and sorry for pointing you in the wrong direction! 

=> But this of course raises another question: Why is the card not able to use channel 12 (I think it's called "Extended Channel Mode")? Does anybody know howto enable this? Under Windows the card worked right after installation with access points using channel 12.

---

### Post by pytheas22 on 2008-10-14
hmmm, that's strange, but I'm glad to hear that you figured it out--I was quite worried because it didn't seem to be making much sense that it worked great for klein but not at all for you.

I found this [bug report]("https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/227643") that seems to describe the issue you're having.  There's a workaround mentioned at the bottom that you could try; apparently you just need to reload the wireless driver and tell it that it's in the EU (and not the United States, where I think you're still not supposed to use channel 12, lest you interrupt the government's attempts to spy on you, etc.).

If that doesn't help or you don't think that this bug is the same as yours, you could file a new bug report, either with Ubuntu or (probably better because it's probably their issue more than Ubuntu's) the intellinuxwireless.org people.

---

### Post by Fischli on 2008-10-14
The workaround worked :-)

After I put the options into the config file, the additional channels were shown (when typing iwlist wlan0 channel).

Thanks a lot!!!

---

### Post by jsvaughan on 2008-10-25
Thank goodness I found this.  I had exactly the same problem on a Thinkpad X301, the only difference being that my Wifi was running on channel 13.  Good spot!

---

### Post by cmcginty on 2008-10-28
> **Fischli said:**
> A few notes about the kill switch and the LED:
- When I turn the kill switch on the led goes of and dmesg says:
```
Kill switch must be turned off for wireless networking to work
```
when I turn the kill switch off, the LED goes on again

Can you explain how you turn the "kill switch" on/off?

---

### Post by pytheas22 on 2008-10-28
> Can you explain how you turn the "kill switch" on/off?

The kill switch is used to enable or disable the radio of your wireless card (mostly for the purpose of saving energy when you're running on battery and don't want the wireless).  Usually it's either a physical button on the laptop or a key combination (like function+F2).  Does that help you to figure it out?

Note that not all laptops have wifi kill switches (my five-year-old Dell doesn't), but most newer ones should.  Some machines will also have an option in BIOS regarding how the radio should be controlled, so you can look there if all else fails.

---

### Post by rduran on 2008-10-29
Muchas gracias yo tenia el mismo problema con mi portatil dell m1530. Tenia el canal 13 en la wifi del router.

Chapooo

---

