---
title: "xserver upgrade problem"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by tombeard on 2010-07-12
Blind leading the blind, I am trying to help a friend over the phone. He just upgraded to Lucid and his X window resolution is messed up. We ran sudo dpkg-reconfigure xserver-xorg but it just returns to the command prompt after a few seconds. xorg.conf was empty.Tried to reinstall xserver-xorg and got

E: dahdi-dkms: subprocess installed post-installation script returned error exit status 10
E: dahdi-linux: dependency problems - leaving unconfigured
E: oss4-dkms: subprocess installed post-installation script returned error exit status 1

He says he got errors about ATI drivers missing so we reinstalled those via synaptic.

Any ideas where to go from here? I am hampered by lack of access to his computer and mine has nvidia so I can't test everything on my machine.

---

### Post by ajgreeny on 2010-07-12
Find out which ATI card first.  Tell him that ```
lspci
``` in terminal will show what is in the machine.  We can then attempt to sort out which driver is needed and how to install it, but it may be as simple as going to **System ->Administration ->Hardware Drivers** and seeing if any are available there.

Try that now; it may do all that is needed.

By the way, there is no xorg.conf any more by default as the system will normally be able to detect and set up xorg with no action on the user's part.  If you have to make an xorg.conf file to get things running properly, it is read and acted on at the start of an x session.  I have to use one running Lucid on my computer with an old ATI 9200SE card, in order to get a better refresh rate.

The old "sudo dpkg-reconfigure xserver-xorg" command you tried has been deprecated for a couple of years now, and as you found, does absolutely nothing.

---

### Post by tombeard on 2010-07-12
We looked up his laptop on line, a Toshiba Satellite, which comes with an Intel 4500M graphics chip. lspci confirms with

> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series 
> > Chipset Integrated Graphics Controller (rev 07)
> > 00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset 
> > Integrated Graphics Controller (rev 07)

He has removed the ATI software via Synaptic.

He says he does not have System > Administration > Hardware Drivers in his menu. 

Is there another way to load the drivers?

---

### Post by ajgreeny on 2010-07-13
Which version of Ubuntu is it?

---

### Post by tombeard on 2010-07-14
gwh@gwh-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

We have installed jockey-gtk, awaiting results.

I appreciate your time and patience. Thank you.

---

### Post by chudder on 2010-07-18
I'm getting the: **oss4-dkms: subprocess installed post-installation script returned error exit status 10** error I lost sound, but I fixed it by reinstalling ALSA, thanks to the forums.  I just hope I don't lose it again.

---

### Post by chudder on 2010-07-18
```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

It doesn't look like I have anything ATI.

What might be the problem?

Thanks

PS: i don't know if I explained this well but basically, a few days ago I lost sound and whenever I'm upgrading through synaptic or terminal, it always gives an error that has to do with the above mentioned error I posted.

What's causing this?

---

