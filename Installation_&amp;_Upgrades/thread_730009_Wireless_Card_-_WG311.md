---
title: "Wireless Card - WG311"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by Touch.Code on 2008-03-20
Hi all,

I am having problems with my Netgear WG311 wireless card. Currently I am on XP posting as otherwise Linux has no way of connecting to the internet, meaning I cannot apt-get anything.

Any help?

Thanks,
James

P.S, I still have no luck with my other topic, so I will have to do this on the Live CD :)

---

### Post by Jammy4041 on 2008-03-20
You could try visiting the Ubuntu wiki for some more help:

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

I hope this helps.

---

### Post by Touch.Code on 2008-03-20
Thanks, James! I shall go back and try them now :)

---

### Post by wolfen69 on 2008-03-20
if that doesnt work, try the Hardy Heron live cd. i have a usb network "stick" that wouldnt work in gutsy, but works in hardy.

---

### Post by Touch.Code on 2008-03-20
OK, well I have a bit of a problem.

I have installed the drivers :) but, instead of displaying:
> 
ndiswrapper -l 
mrv8335 : driver installed
          device (11AB:1FAA) present

It only displays:
> 
ndiswrapper -l 
mrv8335 : driver installed, hardware present

So now I am supposed to run lspci -n and look through the list of by devid. I go through each of them running:
> 
ndiswrapper -a devid mrv8335 
ndiswrapper -l

But I still only see the hardware is present.

What do I do now? If I can get the internet working, I am sticking to Linux!

Thanks,
James

---

### Post by Touch.Code on 2008-03-20
By the way, these are the exact details of my card.

WG311GE
WG311v3

---

### Post by dstew on 2008-03-20
If your card now appears in the System --> Administration --> Network menu, it is working, and it just needs to be configured. Note that that guide is for a Feisty Live CD system, which is different from what you are using.

---

### Post by Touch.Code on 2008-03-20
No it doesn't :(

Which is Feisty? I have Ubuntu 7.10 Live CD, it's not installed yet though, well it is and isn't. However I was trying these commands from a Live CD.

---

### Post by Touch.Code on 2008-03-20
And some other things that may be useful:

Output from lspci | grep Marvell
01:08.0
88w8335

---

### Post by dstew on 2008-03-20
7.10 is Gutsy, which is what you have. So, you do not have a hard-disk installation? You are only using the Live CD? Anyway, post the output of ```
iwconfig
```

---

### Post by Touch.Code on 2008-03-20
I have installed it, just lost Grub (My own fault, but later I shall try and get it back :))

Ok:
lo, no wireless extensions
eth0, no wireless extensions

---

### Post by dstew on 2008-03-20
I guess I don't know what you are trying to do. Do you want to recover your hard disk installation (re-install grub)? Do you want to get your wireless card working in the Live CD system (a somewhat pointless exercise)? From your last post, it is clear that you do not have the wireless driver installed. We will have to start from the beginning. Post the output of ```
lspci
```

---

### Post by Touch.Code on 2008-03-20
At the moment, I need the internet, if it works on Live will it word on installed?

When I have the internet I shall fix my install and then do the internet as well.

> 
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:07.0 Communication controller: PCTel Inc HSP MicroModem 56 (rev 01)
01:08.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)


---

### Post by dstew on 2008-03-20
Do you have a wired connection to the internet that you can use to update Ubuntu? How are you posting right now?

If you are connected by wire, update your Ubuntu using System --> Accessories --> Update Manager. Then, check in the Restricted Driver Manager to see if you got a driver for your card. If not, you will probably have to use ndiswrapper.

[Here ]("http://ubuntuforums.org/showthread.php?t=449049&highlight=enpwi-g")is a thread showing how one person got a Marvell card to work using ndiswrapper.  The important thing is that you get the correct driver. Usually, you can get the WIndows driver from the manufacturer's web site. [Here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") are general ndiswrapper instructions for Ubuntu.

EDIT: [Here]("http://www.encore-usa.com/download/driver/ENLWI-G_Driver_Utility_98SE-ME-2000-XP.zip") is the driver .zip file you need. Extract it, and you should have a folder called V1.10 on your desktop (or in your home folder if you extracted it to there). On the command line, change to the Windows XP directory of the folder:```
 cd Desktop/V1.10/DRIVER/Windows\ XP
```You should be able to see the .inf and .sys files that ndiswrapper needs:```
~/Desktop/V1.10/DRIVER/Windows XP$ ls -l
total 288
-r--r--r-- 1 dad dad      0 2005-03-08 07:40 Mrv8000c.cat
-r--r--r-- 1 dad dad  21341 2005-04-06 18:50 Mrv8000c.inf
-r--r--r-- 1 dad dad 265984 2005-02-22 16:00 Mrv8000c.sys
```Then, install the driver into ndiswrapper:```
sudo ndiswrapper -i Mrv8000c.inf
```Check if it is installed:```
ndiswrapper -l
```

---

### Post by Touch.Code on 2008-03-21
Well, I installed Linux again over the previous installation. I plugged myself into the router, but it wouldn't connect. I think I need to remove my wireless card in before it works.

---

### Post by Touch.Code on 2008-03-21
Would I be able to install my wireless program for Windows under Wine and then use Firefox under Wine to make it work?

---

### Post by teryowen on 2008-03-21
Connect to the intrenet using a cable that should be priority once you're connected make sure to update everything and check out restricted drivers as there will probably be an answer there.

---

### Post by Touch.Code on 2008-03-21
I can't. I have been trying all day. My router just doesn't seem to pick up my PC. I think I need to remove my wireless card beforehand.

---

### Post by teryowen on 2008-03-21
perhaps your network card not the wireless one the wired one isnt turned on. Make sure its on by doing this

sudo ifconfig eth0 up

replace eth0 with what ever your device may be.

As well what you might want to try is connect your computer and then reboot. have you tried this?

---

### Post by Touch.Code on 2008-03-21
I have tried both of them. Nothing.

For clarification, I am using a Netgear WG311v3 (Rev3) PCI Card.

---

### Post by Touch.Code on 2008-03-21
Now I have installed ndsgtk and installed drivers in a GUI. I now run ndiswrapper -l and it says:

mrv8335 driver installed
device (11ab:1FAA) present

Now I type in iwconfig, but I still don't see wlan0

---

### Post by dstew on 2008-03-21
What do you see when you type in iwconfig? Post the output to the forum. Your wireless card may not be designated wlan0. It could be eth0. My wireless card is ath0.

---

### Post by Touch.Code on 2008-03-22
I found I had another Netgear PCI card, a WGn311 I think, I plugged it in and instant connection! I am now posting off of Ubuntu!

Thanks for all the help you gave me!

James

---

### Post by notidefix on 2008-06-03
[http://www.jimbo7.com/wiki/index.php?title=WG311v3](http://www.jimbo7.com/wiki/index.php?title=WG311v3)


cannot remember if that's the driver I used (there's a few you can download), but the process described worked for me

---

