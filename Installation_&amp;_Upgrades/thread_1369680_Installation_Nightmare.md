---
title: "Installation Nightmare"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by owenisred on 2010-01-01
Hi everyone,

Encountering several problems with ubuntu. I have managed to burn iso to cd - I decided to bot ubuntu off the cd, I have been struggling with a couple of problems all to no avail. I have heard ubuntu is pretty damn good, and I was quite enthusiastic about it. But if I can't get this sorted... :(

Oh I should also say I have never used a command line and I have not a clue about xorg or whatever you call it. 

anyway my first problem is Display settings. I can go to System > Preferences > Display, and the largest I can set my resolution to is 800*640 and the monitor is unknown...?

Problem number 2 - the ubuntu software centre is not working... Applications > USC > Could not launch Ubuntu Software Centre..

Problem 3 - In the bar at the top of the screen beside time and date etc, "Crash report detected" keeps popping up?

Problem 4 my @ and " keys have swapped places??? also my Pounds sign (I live in UK) has been replaced with # while # has been replaced with \ 

Please help guys this is driving me crazy - I have been working for a couple of hours on it but nothing makes the slightest bit of difference. I will probably have some more problems soon to be honest - but your help with the above problems would be honestly fantastic,

Cheers,
Owen.

edit: Yea I cant install flash player to watch videos on youtube? 

Applications > Acessories > Terminal will not bring anything up anyway! 

Open office does not work :(:(:(

Niether does gnometris - but robots does lol 

Thanks again,
Owen.

---

### Post by mr clark25 on 2010-01-01
if you dont have anything to save on that computer, i would re-install ubuntu.

for the keyboard problem, you probably left it on "usa" layout. when you reinstall, select the layout for UK.

if the terminal doesn't work, that will really limit you.

i would re-install and see if that helps. boot from the cd and check it for errors. if it finds any, you need to make another cd, and possibly download the .iso again.

---

### Post by owenisred on 2010-01-01
hey thanks for getting back - I have done as you said - and it has fixed a LOT of things. First my keys are the correct way around, Software centre is working, I can install updates like flash player, open office is fine, more importantly Terminal is good again.

Really my only problem now is the display settings, I ran a video system test, 2nd question was 
> 
This display is using the following resolution:
800 x 600
Is this acceptable for your display?but the 4th one said
> 
The following screens and video modes have been detected on your system:

Screen 0: minimum 320 x 200, current 800 x 600, maximum 2048 x 2048
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3* 
   640x480        59.9

Is this correct?maximum 2048 x 2048 which is correct. But still in display 640 x 800 is the highest one I can get

Any idea how I can fix it?

Thanks,
Owen.

Edit: Appearance settings dont work either :(

---

### Post by SecretCode on 2010-01-01
Can you click on System > Admin > Hardware Drivers, and does it suggest any?

---

### Post by owenisred on 2010-01-01
none sadly :(

> No proprietry drives are in use in this system

---

### Post by tachuela on 2010-01-01
'Hardware Drivers' usually suggest one that you can install.

---

### Post by mr clark25 on 2010-01-01
here is someone having a similar problem: [http://ubuntuforums.org/showthread.php?t=1364460](http://ubuntuforums.org/showthread.php?t=1364460)

he/she got it to work with the directions/commands mentioned. i think this will solve your problem.

---

### Post by owenisred on 2010-01-01
im getting nothing - system > Admin > Hardware Drivers

> No proprietary drives are in use in this system 			 		

and a blank page..

---

### Post by tachuela on 2010-01-01
[http://i956.photobucket.com/albums/ae49/Tachuela_01/HardwareDrivers.jpg](http://i956.photobucket.com/albums/ae49/Tachuela_01/HardwareDrivers.jpg)

---

### Post by owenisred on 2010-01-01
I don't have any writing there where all the Nvidia things are. What do you suggest I do?

---

### Post by deathbyswiftwind on 2010-01-01
you could install envy-ng from the repo and have it install your nvidia driver for you.

---

### Post by Bartender on 2010-01-01
owen -
Could you please open a terminal
Applications > Accessories > Terminal

and type 

```
lspci
```

into the terminal, then hit Enter?  I've read thru this thread twice, and don't see anything indicating you *have* an nVidia chipset.  Wondering if the assumption got made along the way and now you're running with it...

The above code should produce a list of parts detected on the PCI bus, and one of those should be your graphics chipset.  Copy/paste the output into a new post please.

For instance, here's mine:

```
bpbar@bpbar-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation E7525 Memory Controller Hub (rev 09)
00:00.1 Class ff00: Intel Corporation E7525/E7520 Error Reporting Registers (rev 09)
00:02.0 PCI bridge: Intel Corporation E7525/E7520/E7320 PCI Express Port A (rev 09)
00:03.0 PCI bridge: Intel Corporation E7525/E7520/E7320 PCI Express Port A1 (rev 09)
00:04.0 PCI bridge: Intel Corporation E7525/E7520 PCI Express Port B (rev 09)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge A
01:00.2 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge B
03:0e.0 Ethernet controller: Intel Corporation 82545GM Gigabit Ethernet Controller (rev 04)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
bpbar@bpbar-desktop:~$ 

```

See the last device detected?  That's what we're looking for.  If it's an onboard chipset, the device may be in the first few lines.  Actually, you can delete all other lines and just paste in the "VGA compatible controller".

---

### Post by owenisred on 2010-01-01
Bartender - Useful? just a mess of numbers and letters to me :)

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 Communication controller: Conexant Systems, Inc. Device 2702 (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

Thanks

---

### Post by Nearl86 on 2010-01-01
I'm not a genius when it comes down to Ubuntu or anything but every time I do a fresh install I need to do an update or at least update my package list to get any of the drivers to show in SYSTEM>ADMINISTRATION>HARDWARE DRIVERS try that and hopefully it helps.

---

### Post by owenisred on 2010-01-01
thanks - already tried that tho - no drivers come up :(

---

### Post by Nearl86 on 2010-01-01
Try this link it sounds very similar to your problem.

[http://ubuntuforums.org/showthread.php?t=1158571](http://ubuntuforums.org/showthread.php?t=1158571)

---

### Post by owenisred on 2010-01-01
thanks - how does one edit xorg.conf...?

---

### Post by ehickman on 2010-01-01
you can edit xorg.conf my typing in a terminal:

gksudo gedit /etc/X11/xorg.conf 

it will ask for a password because you will be using root/ admin privileges to edit xorg.conf

---

### Post by ehickman on 2010-01-01
you can edit xorg.conf my typing in a terminal:

gksudo gedit /etc/X11/xorg.conf 

it will ask for a password because you will be using root/ admin privileges to edit xorg.conf

---

### Post by ywh842005 on 2010-01-01
your os is ubuntu 9.10 right?
there is no /etc/X11/xorg.conf cause xorg.conf in ubuntu 9.10 doesn't exist
so if you want to edit, you have to create a new one by run
> sudo /etc/X11/xorg.conf
the xorg.conf file will be use if it created.

---

### Post by ywh842005 on 2010-01-01
sorry the command line should be 


```
sudo nano /etc/X11/xorg.conf
```

you may want to google some info about xorg.conf

---

### Post by owenisred on 2010-01-01
OK - guys i could actually cry now I have spent all day at this lol 

I THINK i have got into xorg.conf I have instructions to do this

Code:
 	Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection 
You'll need to replace aa-dd with the values for **your** monitor. 		                   		  		  		 		 			 				__________________

How?

Thanks,
Owen.

---

### Post by Nearl86 on 2010-01-01
Try the directions in this link. 

[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

After which use this command "gksudo gedit /etc/X11/xorg.conf" without the quotation marks and a window should pop up with all the stuff containing aa-dd etc.  replace the things you need to and push save after wards restart your computer and see if that has any effect.

---

### Post by Nearl86 on 2010-01-01
And sorry if it takes me a bit to reply im raeserching as im going along

---

### Post by Bartender on 2010-01-01
> **owenisred said:**
> 

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)



Yeah, owen, you did fine.  You don't have an nVidia graphics chipset, so that was a dead-end for you anyway.  Your graphics chipset is onboard Intel 82845.

So you want to google answers for "ubuntu intel 82845" or just "ubuntu intel 845".  

I'm on dial-up so not going to spend a lot of time on this, but it looks like there are a LOT of people talking about these problems.  If you've got some spare cash you might want to drop a basic nVidia card into your PC and go get the nVidia proprietary drivers.

---

