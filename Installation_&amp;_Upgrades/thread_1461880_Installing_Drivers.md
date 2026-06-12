---
title: "Installing Drivers"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by RKhadder on 2010-04-24
I just installed Ubuntu 9.1 for the first time. Whenever I put in a CD to install drivers nothing happens. I tried to click AUTORUN.EXE but it prompts me to cancle or run or run in terminal. I select run nothing, then I slect run as terminal then nothing also. Then I click on Setup.Exe samething nothing. Is their something I'm doing wrong?
 
Thanks for those who help,
Ramsey

---

### Post by AlexDBall on 2010-04-24
Well, i am supposing you are new to linux. ".exe" files do not run under linux and for sure windows drivers do not work in linux.

Drivers in linux are either compiled into the kernel or loaded as kernel modules.

Search the forums and/or the google for more info!

Hope this helped!

---

### Post by RKhadder on 2010-04-24
Well I did a google search and I couldnt find a kernal for a linksys router. How do I connect to the internet with ubuntu support?

---

### Post by thomas144 on 2010-04-24
If you need a driver for something, I might be able to help. Why did you try to install drivers? What driver(s) did you want to install from the CD? Was a device not working? If you give some more info, I might be able to help you get a device working. :D

---

### Post by thomas144 on 2010-04-24
Sorry. Our posts were at the same time. Are you connected to the internet in Ubuntu right now, and is the way you want to connect in Ubuntu not working?

---

### Post by RKhadder on 2010-04-24
Well I want to connect to the internet so I got a Wireless-G Adapter by Linksys to connect to my modem. Before I can connect my adapter I need to install a CD. SO I did what I said before and I couldnt get anything to install.

---

### Post by thomas144 on 2010-04-24
So, from what I can understand, you can't connect to the Internet in Ubuntu wirelessly. How are you connected right now? Are you in Windows or Ubuntu?

---

### Post by RKhadder on 2010-04-24
Im on my windows computer. My ubuntu desktop is just chillen next to me =P

---

### Post by thomas144 on 2010-04-24
Okay. Now we're getting somewhere. Try turning on your Ubuntu computer and logging in. Open up Firefox, type in a website, (like [www.google.com]("http://www.google.com")) and press Enter. What happens?

---

### Post by RKhadder on 2010-04-24
Typical "Server cant find" error. Note that I have not adjusted any networks things.

---

### Post by thomas144 on 2010-04-24
What manufacturer and model is your Ubuntu computer?

---

### Post by RKhadder on 2010-04-24
Well I created the computer all myself =]. I am using Ubuntu 9.10.

---

### Post by thomas144 on 2010-04-24
I didn't see that coming. But, that doesn't matter too much. What wireless card does it have?

---

### Post by RKhadder on 2010-04-24
mostlikly integrated

---

### Post by thomas144 on 2010-04-24
What we need is the maker and model of the card. Go to Applications> Accessories> Terminal. Type in
```
 
lspci

```
and hit enter. (edit:  The l in lspci is a lowercase L.) Lots of text will come out. If you can, look at it and find the networking portion. What does it say?

---

### Post by RKhadder on 2010-04-24
The only thing I see that relates to networks is ethernet control: realtech semiconductor co.
 
What should I be looking for?

---

### Post by thomas144 on 2010-04-24
Maybe I could see what wireless card you have if you were to show me the output of the command. Can you copy the output of it to Gedit and save it on your computer? Also, could you use a flash drive or something to get it on your Windows computer, and then post here?

---

### Post by RKhadder on 2010-04-24
I have a flash drive but keep in mind Im new so what grudit?

---

### Post by thomas144 on 2010-04-24
Gedit is a text editor (kind of like the Windows program Notepad.) It's located at Applications> Accessories> Gedit. Copy the output of lspci to Gedit, save the file to your flash drive, and the open it up on your Windows computer. If you have any trouble, I'm here to help.

---

### Post by RKhadder on 2010-04-24
[FONT=Courier New][SIZE=3]No command 'lscpi' found, did you mean:
 Command 'lscpu' from package 'util-linux' (main)
 Command 'lspci' from package 'pciutils' (main)
 Command 'lscp' from package 'nilfs2-tools' (universe)
lscpi: command not found
ramsey@ramsey-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Clarkdake DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Clarkdale PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.1 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.2 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1a.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.1 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.2 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller (rev 06)
00:1d.7 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce GTS 250] (rev a2)
03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

 [/SIZE][/FONT]

---

### Post by thomas144 on 2010-04-24
I see what you mean. Maybe we can take a different approach. Go to System> Administration> Hardware Drivers. What do you see?

---

### Post by RKhadder on 2010-04-24
There are no Drivers. It says no drivers found on this system. This brings me back to my first question. I cannot install drivers from cd's. For example my motherboard drivers, or any other drivers for that fact.

---

### Post by mmalone21 on 2010-04-24
I realize I am jumping in to this a little late I just read through the posts, I am still a little bit un-clear on a few of the details. You say you have a custom build PC, no problem. Have you tested any or all of these hardware components in windows? Also which motherboard make and model do you have as well as your network card. Once I have that info I can check some compatibility databases and provide you with an answer.

---

### Post by l3ecl on 2010-04-24
i posted the same problem in this thread:
[http://ubuntuforums.org/showthread.php?p=9165323#post9165323](http://ubuntuforums.org/showthread.php?p=9165323#post9165323)

maybe the solution there works for you.

---

### Post by RKhadder on 2010-04-24
> **mmalone21 said:**
> I realize I am jumping in to this a little late I just read through the posts, I am still a little bit un-clear on a few of the details. You say you have a custom build PC, no problem. Have you tested any or all of these hardware components in windows? Also which motherboard make and model do you have as well as your network card. Once I have that info I can check some compatibility databases and provide you with an answer.
 
I am using a Gigabyte H55M-UD2H Mini ATX motherboard with GeForce 250 graphics card with 2 gigs of ram with an Intel i3-530 processer along with 450 watts and I do not have the specs on the hard drive but I'm confident I have more then enough.

---

### Post by thomas144 on 2010-04-24
I'm sorry, but I'm not sure where to go from here. This is not a solution, but a workaround. If you don't have to move the computer, and you are near the router, you might be able to connect the the Internet with a wired connection. If you find that practical, you could always do that, at least temporarily. Are you sure your computer even has a wireless card?

---

### Post by RKhadder on 2010-04-24
> **thomas144 said:**
> I'm sorry, but I'm not sure where to go from here. This is not a solution, but a workaround. If you don't have to move the computer, and you are near the router, you might be able to connect the the Internet with a wired connection. If you find that practical, you could always do that, at least temporarily. Are you sure your computer even has a wireless card?
 Well My Ubuntu Comp is in my basement and My main comp is on the first floor, so moving is out of the question. The thing is I'm not sure if it has a nic card.

---

### Post by thomas144 on 2010-04-24
I guess I am out of ideas. I'm sorry I couldn't help you. :( Goodbye.

---

### Post by RKhadder on 2010-04-24
Thanks anyway

---

### Post by taurolyon on 2010-04-24
Do you happen to have a manufacturer & model number on your Wireless card? 

According to your lspci output it doesn't appear to be showing up.

If you're in need of a wireless card, I'm currently using this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833180030](http://www.newegg.com/Product/Product.aspx?Item=N82E16833180030)

and it works right off the bat in Ubuntu!

---

### Post by RKhadder on 2010-04-24
Excellent but which connection does it require, pci? Also, How does it work? Like does it automatically connect to my wireless network or do I need a linsys adapter?
 
Thanks very much.

---

### Post by RKhadder on 2010-04-24
There are alot of bad reviews is there anything else you recomend keep in mind that I have my router on the first flooor and the cpu in the basement.

---

### Post by taurolyon on 2010-04-24
The card I suggested is PCI. Ubuntu will prompt you stating "Wireless networks available" and from there you will just point it at your wireless network and you're online.

---

### Post by taurolyon on 2010-04-24
RE: the newegg reviews.

I personally think the issue is with Encore trying to brand their Windows drivers that they include with the device. The fun part with Ubuntu is you can just Frisbee that thing into the garbage and just toss the card in your machine. Ubuntu will recognize the cards chipset and install the appropriate Realtek drivers.

I've bought 3 of these cards with no issues on each one under Ubuntu.

But.. if you're looking to spend a bit more, shoot for a Linksys card. I've only used their routers, but I've only heard good things about their wireless NICs.

---

### Post by RKhadder on 2010-04-24
Will it even work through floors?

---

### Post by mmalone21 on 2010-04-24
I just looked up the info on your Motherboard and everything seams fine. It does not have built in wireless so I still need info on your wireless card.

---

### Post by RKhadder on 2010-04-24
I do not have a nic card :lolflag:

---

### Post by taurolyon on 2010-04-24
Wifi should work through floors (providing there's not a lot of metal plumbing and electrical wiring running through the floors). I used to keep my router in the basement and had no problems with wireless.

---

### Post by taurolyon on 2010-04-24
> **RKhadder said:**
> I do not have a nic card :lolflag:
NIC = Network Interface Card

All I can really tell you at this point is to get a wireless card for your computer. You might want to post in the [hardware section]("http://ubuntuforums.org/forumdisplay.php?f=332") for suggestions on a good PCI or USB Wireless card that is readily compatible with Ubuntu.

---

