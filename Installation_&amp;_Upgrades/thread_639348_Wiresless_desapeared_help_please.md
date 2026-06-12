---
title: "Wiresless desapeared help please"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2007-12-13
I have installed ubuntu, then use the wireless connection the first day, but yesterday 
I connected it my pc to the internet with wired Connection at my work, when I went  home I couldn't find my wireless, it is not even in the connection setting.
I need a help
Thanks

---

### Post by d0nny2600 on 2007-12-13
Setup a manual configuration from the network Icon.. Set up the appropriate wireless settings. Then save the profile as home. When you connect to the other network save that profile as work etc. When you get back home then just reactivate the home profile you saved previously!

Hope that makes sense.
Regards,
d0nny2600

---

### Post by hoboy on 2007-12-13
> **d0nny2600 said:**
> Setup a manual configuration from the network Icon.. Set up the appropriate wireless settings. Then save the profile as home. When you connect to the other network save that profile as work etc. When you get back home then just reactivate the home profile you saved previously!

Hope that makes sense.
Regards,
d0nny2600 re

Setup a manual configuration from the network Icon is not visible from the icon, how can I

configure it ?
Thanks

---

### Post by d0nny2600 on 2007-12-13
To configure network settings go
System ->Administrations -> Network

Enter your root pass here and configure from there.

Regards,
d0nny2600

---

### Post by hoboy on 2007-12-13
> **d0nny2600 said:**
> To configure network settings go
System ->Administrations -> Network

Enter your root pass here and configure from there.

Regards,
d0nny2600

Sir sorry for my ignorance, but I don't have wireless showed in the settings.
But I have used the wireless facitlies before

---

### Post by d0nny2600 on 2007-12-13
Don't apologize - thats what these forums are for!

Ok. Can you go System -> Preferences and run hardware information.

There should be some info there on your networking interfaces. E.g 10/100 ethernet and WLAN.

Post whether wlan is listed here or not

---

### Post by hoboy on 2007-12-13
> **d0nny2600 said:**
> Don't apologize - thats what these forums are for!

Ok. Can you go System -> Preferences and run hardware information.

There should be some info there on your networking interfaces. E.g 10/100 ethernet and WLAN.

Post whether wlan is listed here or not


Here they are.
Vendor : Unknown
Device : unknown
Bus type pci

Device type "net", "net.80203"
Capabilites net, net.80203

---

### Post by d0nny2600 on 2007-12-13
Ok that means that it is not a hardware issue. Try the following command and see does it output any wireless networks

sudo iwlist scan 

let me know the output

---

### Post by hoboy on 2007-12-13
> **d0nny2600 said:**
> Ok that means that it is not a hardware issue. Try the following command and see does it output any wireless networks

sudo iwlist scan 

let me know the output
Here it is

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by d0nny2600 on 2007-12-13
Ok you can try reinstalling the drivers using the method below. If this works we can try having the Drivers initialized fully on booting up. If your wireless card is different a quick search in google will direct you to the drivers for that device.

This is a how to on how to get the Broadcom 43xx wireless cards working:

freewebs.com/ronserver/bcm43xx.tar.gz

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

---

### Post by samden on 2008-04-21
Thankyou very much d0nny2600 for this excellent, detailed how-to. I have an Acer Aspire 4315 running Ubuntu 7.10, and the wireless connection was working then disappeared completely from Network Settings. I had no idea what to do and was confused by many different posts, but your how-to showed me how to fix it, with some modifications of course. I had to download the correct driver of course, and use ndiswrapper-common rather than ndiswrapper-utils. I don't know where I'd still be without your post.

I hope the original poster was able to fix their problem too.

Thanks heaps.

---

