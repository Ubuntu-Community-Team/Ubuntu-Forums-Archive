---
title: "Intrepid Ibex 8.10 Alpha 5 graphics, VPN,"
date: 2008-09-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nausser on 2008-09-07
I've upgraded to Ibex Alpha 5 and still no luck with the 5 in 1 card reader or windows network browsing. Everything worked fine in Gutsy Gibbon. I was urged to upgrade to Ibex Alpha 5 in regards to my TI 5-in-1 card reader. No previal though. Only more problems to write home about.

To cap the new problems I now have that I didn't have in Gutsy or Hardy.  Working to get my display drivers to work correctly. This is a new one for me. I can't get any desktop effects to work now. It would seem I lost some sort of "3D" support during the upgrade. My Acer has an Intel video card.

When I press my power button, I'm only left with the option of logging off or switching users. No restart or shutdown or suspend. The three that I would use most of all in Hardy. Clicking on my user name in the task-bar gives me these options now except for standby. My Acer "quick launch" buttons on my keyboard had to be re-assigned a couple times before they would work properly to start Firefox and Evolution. I also noticed the mouse pad isn't as good. The "touch scroll" is the most noticeable.

The network viewing problem still persists as well. I can browse a network and see windows work-groups, then computers and when they are opened, I see nothing. I have had no luck with getting my Windows PPTP VPN connection to work either. I have had zero problems with this in the past (Gutsy and Hardy) and use it quite often for work.

That's all for now. I will continue trying to search for solutions to my most important problems first. (VPN, then display)

My config is as follows:

Results of "lspci":

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

Results of "lspci-vvnn" and "dmesg" are attached as txt files.

I know this thread bleeds into other catergories; however, gotta post it up somewhere. 

A big thanks to anyone who is brave enough to make the Ibex Apha 5 upgrade!


Results of

---

### Post by overdrank on 2008-09-07
Hi and welcome, moved to Intrepid Ibex Testing and Discussion  :)

---

### Post by Nullack on 2008-09-08
Yes welcome. Please consider that Intrepid is not a production release, not a beta release either - its an Alpha. You should be expecting problems :) You have an opportunity to help shape Intrepid into a reliable and excellent production release by being involved. Please refer to the link in my sig about contributing to Intrepid.

While it has problems it offers the benefits of having the latest software packages. Many participants like the fun of adventuring through whats new, what works, what doesnt and helping the effort to fix things.

---

### Post by sufyan on 2008-09-17
Hey I am not sure if this is the right place to ask this but the title says intrepid and vpn so here it is. 

OK, now i have a copy of vista installed on the pc so whenever i have to use the Internet on campus I use the cisco vpn client. Never really got around to using ubuntu for internet. 

Now the network connection menu on intrepid has a 'configure vpn setting'. I want to know how to make it work. At home I can not really add any profile or connection settings to it. And I am not sure if i will be able to do that when connected on the campus wireless. So how does this work?

Thank you.

---

### Post by MALEADt on 2008-09-17
> **sufyan said:**
> Hey I am not sure if this is the right place to ask this but the title says intrepid and vpn so here it is. 

OK, now i have a copy of vista installed on the pc so whenever i have to use the Internet on campus I use the cisco vpn client. Never really got around to using ubuntu for internet. 

Now the network connection menu on intrepid has a 'configure vpn setting'. I want to know how to make it work. At home I can not really add any profile or connection settings to it. And I am not sure if i will be able to do that when connected on the campus wireless. So how does this work?

Thank you.

install vpnc & networkmanager-vpnc to enable cisco vpn functionality. use the config profile of the cisco client at windows to fill in everything you need when configuring network manager. if you are provided with a config profile instead of an information sheet containing the passwords, you'll also need to decrypt the passwords from the file (there is an exploit for that floating around the internet, you'll find it).

---

