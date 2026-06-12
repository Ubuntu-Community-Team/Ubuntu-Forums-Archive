---
title: "Wireless is not showing-HHHHHelllllllllp"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2007-12-19
Hello firstly great forum
as I am new to Linux I have been a frequent customer to it.
I have been struggle now over a week to fix my Acer laptop wireless.
The problem is when I install ubuntu from cd it worked very very well, then I took ti to my work, then used the wired connection, since that my wireless has desapeared, I have follow the this instruction bellow, but still not working.

reewebs.com/ronserver/bcm43xx.tar.gz

1) Blacklist bcm43xx driver
Open a Terminal window
Type "sudo gedit /etc/modprobe.d/blacklist"
At the bottom add the lines
# get rid of the default kernel drivers
blacklist bcm43xx

2) Make sure network interfaces file is correct
Type "sudo gedit /etc/network/interfaces"
Remove all comments ('#') that you see so that all devices are handled by the default network manager.
I would reboot here and make sure the wireless light goes out

3) Install ndiswrapper
Put in Ubuntu CD. Open Synaptic Package Manager (ClickSystem -> Administration -> Synaptic Package Manager),search for ndiswrapper-utils, and install it.You could also type "sudo apt-get install ndiswrapper-utils (IF you are not using ubuntu then make sure you have ndiswrapper-utils somhow installed)

4) Conigure ndiswrapper
Open terminal and navigate the folder where your drivers are."cd Desktop/bcm43xx"
Type "sudo ndiswrapper -i oem3.inf"Then type "sudo ndiswrapper -m"
Type "sudo gedit /etc/modprobe.d/ndiswrapper"Change the one line in that file to read "alias eth1 ndiswrapper"

Now you should reboot so all the drivers load.

Once you reboot the wireless light on your laptop should be lit. If it worked, you should be able to click the Network Manager icon in the top right. It will probably show a disconnected connection because the wired lan is not plugged in.
Left click it and select the wireless card from the drop down menu.
Click Configure
Click Wireless Connection, then Properties. Here just enter your network information. If you're using an unprotected network you should only have to type yout SSID.

Click OK and you should now be connected! If a green signal meter and connected network icon appear in the upper right you'll know it worked.
__________________
Desktop: AMD Sempron 3300, 1gb, 160gb, nVidia 5500, Ubuntu 7.10

---

### Post by Pumalite on 2007-12-19
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

