---
title: "Post-install problem with wifi Atheros AR5212"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by alm on 2007-01-16
Hi.
After updating to Edgy (having same problems) the wifi stoped working.
Then, after a clean Edgy install it DID WORK for a few minutes and then died.
The funny thing is that when I boot from the edgy installing CD it WORKS great.

I am starting to desperate !


lspci:

00:00.0 Host bridge: ATI Technologies Inc R200 AGP Bridge [Mobility Radeon 7000 IGP] (rev 05)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 1
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility 7000 IGP
02:04.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
------------------------------------------

iwconfig:

lo no wireless extensions.

eth0 no wireless extensions.

wifi0 no wireless extensions.

ath0 IEEE 802.11b ESSID:""
Mode:Managed Channel:0 Access Point: Not-Associated
Bit Rate:0 kb/s Tx-Power:0 dBm Sensitivity=0/3
Retryff RTS thrff Fragment thrff
Power Managementff
Link Quality=0/94 Signal level=-95 dBm Noise level=-95 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.

------------------------------------------
sudo iwlist ath0 scanning

ath0 Interface doesn't support scanning : Invalid argument

(when booting from the edgy Installing CD the scanning goes ok !)

---

### Post by Stochastic on 2007-01-27
Hey, I've got an Atheros AR5212 802.11abg NIC (rev 01) wireless card too and I couldn't get it running in Edgy at all.  It relies on the Madwifi driver so start researching that, some posts claim that if you install the linux-restricted-modules-$(uname -r) package things start working.

---

### Post by mrojas73 on 2007-02-03
> **Stochastic said:**
> Hey, I've got an Atheros AR5212 802.11abg NIC (rev 01) wireless card too and I couldn't get it running in Edgy at all.  It relies on the Madwifi driver so start researching that, some posts claim that if you install the linux-restricted-modules-$(uname -r) package things start working.
Hi Stochastic, I just tried your solution on my updated Edgy system and it worked like a charm!

Thank you very much.

---

### Post by Syr0 on 2007-02-05
I'm having problems with my wireless card of the same model and brand, and I have the restricted modules installed!

It used to work all the time when I first installed Edgy, but now it only works for about 20 minutes when I leave my Toshiba Portege A100 laptop turned off for an extended period of time.

Madwifi is installed, and when the wireless card quits life, the system completely lags up and the mouse goes at what can be exaggerated as 2 fps.

Help?

---

### Post by dannyboy79 on 2007-02-08
this issue is solved if you update madwifi-ng to r2081 per this link. [http://madwifi.org/ticket/1016](http://madwifi.org/ticket/1016). look at the post dated 02/06/07.

---

### Post by NBeanbag on 2007-03-04
How do I update to madwifi r2081?

I've reinstalled linux-restricted modules (2.6.17.7-11.2) and my WG511T network card doesn't work. My network card sometimes connects, but most of the time it will have one light blink and ath0 doesn't show up in the System>Administration>Networking window. Other times it will connect briefly, lag my computer and then revert back to blinking a single light. 

Could it be because my home network uses WEP encryption? Its strange because it was working fine for a month now. It just stopped working two days ago.

---

