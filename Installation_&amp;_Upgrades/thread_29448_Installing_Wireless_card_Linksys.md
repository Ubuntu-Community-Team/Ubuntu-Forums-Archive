---
title: "Installing Wireless card Linksys"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by tessa on 2005-04-24
Hallo 

I've just installaed ubuntu  \\:D/  and now i have the problem that follows

i have a wireless card LINKSYS WPC54G

the system does not detect the card during the installation

than i've tryied to go to

[http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.3532963119/](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-07.3532963119/)

but doesn't work

How can  install my wireless card?  ](*,) 

ty

Tessa

---

### Post by impman89 on 2005-04-24
get ndiswrapper (google it)

then get the windows drivers for the card and do this

ndiswrapper -i driver.inf
modprobe ndiswrapper

then configure using iwconfig or the network GNOME utility and then one last step to start on boot up

ndiswrapper -m

good luck

---

### Post by greenwom on 2005-04-24
When I download the drivers I get a .exe file.

Will Ubuntu's archive manger be able to extract the file? (properly)

---

### Post by ozoneflyer on 2005-04-25
Run the .exe on your windows machine. It will extract the drivers for you. Copy the .sys driver file over to the linux box.

---

### Post by bquark on 2005-04-25
I have WPC54G and I have been researching this. There are at least three different chipsets used in various versions of the card. I have v2 which uses the ACX100 chipset. Ubuntu loaded the correct open source driver, but I had to go into the networking control and tell that it was configured. I then activated it and it worked fine. 

However, when I tried it with WEP on it did not work. The website for the [ACX100 driver](http://acx100.sourceforge.net) reports that it does not yet work with WEP.

---

### Post by poofyhairguy on 2005-04-25
[QUOTE=tessa]
How can  install my wireless card?  ](*,) 

ty

Tessa[/QUOTE]


Ndiswrapper. Its the only way. It sucks....but its the only way.

(well actually its not. In the exact same situation I sold my card on ebay and got a card that works out the box instead)

Here is the thread to tell you how to do it.

[http://www.ubuntuforums.org/showthread.php?t=25683&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=25683&page=1&pp=10)

Many people have had success.

---

### Post by Dillius on 2005-05-01
I'm having problems with the same card. I've been working with Ndiswrapper, and it says that I have the proper driver from the INF file, and says it matches the hardware. However, when I modprob it, it never adds wlan0 as an interface. 

In my actual hardware managers, this card shows up as:

In lspci: 
0000:02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

In the gnome device manager it shows as:
ACX 111 54Mbps Wireless Interface

Also, how do I access these tools from gnome? I've had to log into kde in order to access any wireless tools.

---

### Post by Dillius on 2005-05-02
One strange thing I noticed, though I don't know if it is of any relevance or not, is that whenever I modprobe ndiswrapper, then check lsmod, it lists ndiswrapper as being a part of usbcore. However, this is not a usb wireless adapter. Could that have something to do with the problem?

---

