---
title: "Having problems with wireless internet."
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by Crabaroni on 2011-03-16
When I firsts installed Ubuntu 10.04, and tried to hook it up to my wireless network it noticed my connection and accepted my password, but did not connect. My wireless card doesn't have linux drivers installed. I found the correct drivers, but I am unsure of the correct way to install them in Windows so they work in Ubuntu. I am currently dual booting Windows 7 and Ubuntu. All and any help is appreciated.

---

### Post by walt.smith1960 on 2011-03-16
If I read your post correctly, you cannot install wireless drivers in Windows and expect them to work in Linux. A good start would be to post the output of the command 'lspci'. This will tell everyone what chipset your wireless device uses. It should look something like this:
```
 

lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MC Gigabit Network Connection (rev 03)
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
**03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)**
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b6)

```

If you're using a USB adapter, you can use the command 'lsusb' in the same manner.  You may also read about NDISwrapper.  That sometimes enables using Windows 2000/XP drivers(not Vista/Win7 drivers) on a Linux install.  Most regard NDISwrapper as a last resort if you can't find native Linux software. You might also have better success posting in the 'networking and wireless' forum.

---

### Post by Crabaroni on 2011-03-17
My Communication Controller is an Intel Corporation Cougar Point HECI Controller #1 (rev 04)

My Network Controller is a RaLink RT3090 Wireless 802.11n 1T/1R PCI

My Ethernet Controller is an Intel Corporation 82579V Gigabit Network Connection (rev 04)

These are the only things that seemed relevant that the terminal output gave me. If I were to install the drivers where in Windows would I put them so they worked in Ubuntu?

---

### Post by Crabaroni on 2011-03-17
I found this thread [http://ubuntuforums.org/showthread.php?t=1314747](http://ubuntuforums.org/showthread.php?t=1314747), and they say a certain download worked for them. Should I download it, and where would I put it in windows? I don't know how to install firmware.

---

### Post by lkraemer on 2011-03-17
I searched the forum, and found this information at:
[http://ubuntuforums.org/showthread.php?t=1490123&page=2](http://ubuntuforums.org/showthread.php?t=1490123&page=2)

So I'd try using this guide:
[http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/](http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/)

lk

---

### Post by Crabaroni on 2011-03-17
> **lkraemer said:**
> I searched the forum, and found this information at:
[http://ubuntuforums.org/showthread.php?t=1490123&page=2](http://ubuntuforums.org/showthread.php?t=1490123&page=2)

So I'd try using this guide:
[http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/](http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/)

lk
  Thanks for the links, but if I download these packages and patches in windows how do i access them in Ubuntu. Sorry for the newbie questions this is my firsts time with Linux.

---

### Post by grahammechanical on 2011-03-17
May I say a few things?

1) Windows and Ubuntu are separate operating systems. They do not interact with each other. Ubuntu cannot use drivers installed in windows. Ubuntu needs a special program to use wireless drivers designed for Windows. This program is called NDSwrapper. Ubuntu has wireless drivers designed for Ubuntu. If these type of drivers are available it is better to use them.

2) You say

> tried to hook it up to my wireless network it noticed my connection and accepted my password, but did not connect. 

If network manager noticed your connection then this means that you already have the necessary drivers installed.

2) The network manager utility will accept any password that you enter. That does not mean that it is the correct password. If it is not the correct password then the attempt to connect will fail.

4) The correct password is not your log-in password but the wireless key or pass phrase that is on the bottom of the modem/router. It may also be called WPA-PSK.

5) WPA-PSK is the type of encryption use on the modem/router. There are other types of encryption such as WEP. If network manager is using the wrong type of encryption then the connection will fail even though the pass phrase is correct.

You may know these things already but we need to eliminate them if we are to give advice.

Regards.

---

### Post by Crabaroni on 2011-03-17
I know about ndiswrapper, but i cannot download anything on Ubuntu because I have not internet connection, so I'm wondering how do I get drivers on windows to work in Ubuntu with out ndiswrapper. I checked my password with my network manager, and made sure of the encryption type he is using and the password still won't work.

---

### Post by ZigBlazer on 2011-03-17
Very similar problem here.  When I first loaded ubuntu I had no problems connecting to wireless internet.  The more I use it the less it wants to connect.  I installed the wireless radar program, which didn't help, and now I removed it and the menu no longer shows a wireless option.  Running XP I can still get on the internet no problem to check the forums.

So if anyone has found anything to fix this, let me know.  Or if you know how I can get the wireless option back on the connection menu at the top, without ubuntu being connected to the internet, because I don't have an ethernet connection to try.  At least when I had a wireless option to enable it would find my network, it just wouldn't connect to it half the time.

---

### Post by kagerato on 2011-03-18
> **Crabaroni said:**
> I know about ndiswrapper, but i cannot download anything on Ubuntu because I have not internet connection, so I'm wondering how do I get drivers on windows to work in Ubuntu with out ndiswrapper.

While you could transfer the files via removable storage or some other method, that's unlikely to be your problem.  If NetworkManager does anything at all, you already have a native driver.

Running `iwconfig` in a terminal should confirm this.  (If you see wlan0, that's a wireless network device.)

Other people have had issues with precisely the same chip.  The problems had little to nothing to do with the driver.  See [http://ubuntuforums.org/showthread.php?t=1490123](http://ubuntuforums.org/showthread.php?t=1490123) for an example.

---

### Post by lkraemer on 2011-03-18
Crabaroni,
The best thing to do is go to a friends house where you can get to an
Ethernet connection with a patch cable.  Then start the process of following
the guide.  That should fix your wireless.

Other than that your option would be to use Dialup.  That's about it as far
as I know.  You really need an Ethernet connection to get all the files,
as Dialup will take forever.


lk

---

### Post by Crabaroni on 2011-03-18
I'm not understanding what is going on in that thread. I tried:
```
sudo mkdir -p /etc/Wireless/RT2860STA/
 sudo touch /etc/Wireless/RT2860STA/RT2860STA.dat
 sudo service network-manager restart
```
But the terminal said the command is invalid for some reason. This is getting really frustrating I've scoured the internet for hours.

---

### Post by Crabaroni on 2011-03-19
So I made the empty  directory,.dat file, and I even found the drivers for the actual chip. The internet still won't work, I try to sudo service network-manager restart but nothing happens.

---

