---
title: "Intrepid opinion and problems"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by toasterboy1 on 2008-10-06
System: Compaq Presario V6133cl
Video: Nvidia GeForce Go 6150
Wireless: BCM4311 connected to WPA access point
Kernel: 2.6.27-4-generic

System booted after install from CD. Originally tried dist-upgrade from Hardy with major problems. Once booted wireless did not work. 

Fixed wireless by uninstalling network-manager and doing the following from root (sudo bash)
```

apt-get install ndiswrapper-utils-1.9 cabextract
echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
echo "blacklist ssb" >> /etc/modprobe.d/blacklist
echo "blacklist b43" >> /etc/modprobe.d/blacklist
echo "blacklist wl" >> /etc/modprobe.d/blacklist
echo "alias wlan0 ndiswrapper" >> /etc/modprobe.d/ndiswrapper
echo "alias wlan0 ndiswrapper" >> /etc/modprobe.conf
echo "ndiswrapper" >> /etc/modules
mkdir /root/wireless_driver
cd /root/wireless_driver/
wget http://ftp.us.dell.com/network/R151517.EXE
unzip -a R151517.EXE
cd DRIVER
ndiswrapper -i bcmwl5.inf
modprobe ndiswrapper
```

Installed wicd and for some weird reason had to edit /etc/network/interfaces and /etc/resolv.conf before it would work.
Wirelesss would not connect using kernel 2.6.27-5-generic.

Nvidia driver 177.76 installed with Envyng kde would not boot with kernel 2.6.27-5-generic even after reinstalling driver. Seems ok with 2.6.27-4-generic.

Get program crash notifications often about python2.5.
Also alt+f1 stopped working after I changed to classic menu. Anyone with suggestions about that?
Anyone been able to get gramps running? I get core dump.
Also why when I add programs to favorites do they get a gear for an icon and not the one from the menu.

Over all a big change but still like it seems a bit faster than hardy.

---

### Post by toasterboy1 on 2008-10-07
I guess no gold on the wireless even after working yesterday after numerous reboots. I started it this morning and it refuses to connect to the wireless. Wicd log says something about possible wpa_supplication authentication failed.

---

### Post by Minus0 on 2008-10-07
Check "Hardware Drivers" from the System->Administration menu.  I had drivers in there, but I had to add the module wl to the /etc/modules to make it start up every time i boot.  This should remove the need to use ndiswrapper and make wpa work consistently.  

Also, while this is for Hardy, you can check out [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218) which shows a method of getting it working with drivers (instead of ndiswrapper).  4311 should be supported by both methods.  Good luck.

---

### Post by toasterboy1 on 2008-10-07
Wireless and video working in kernel 2.6.27-5-generic. Forgot you have to uninstall video driver in envyng and then reinstall in the new kernel. As for the wireless found and old post about creating a wireless-network.sh script that restarts the /etc/init.d/networking. Created the script and added it to the pre-connection script section in wicd. Seems to be working today after a handful of reboots.

---

### Post by deflagmator on 2008-10-07
One big problem 

[https://bugs.launchpad.net/ubuntu/+bug/279693]("https://bugs.launchpad.net/ubuntu/+bug/279693")

I had the same problem with last debian lenny. May be the problem is the maxtor hard disk  the sata controler driver.

I had no problems with any 6.06....to 8.04.1 but it seems that something has changed in this last kernel. 2.6.27-6

Any solution?:(

---

### Post by Minus0 on 2008-10-07
> **deflagmator said:**
> One big problem 

[https://bugs.launchpad.net/ubuntu/+bug/279693]("https://bugs.launchpad.net/ubuntu/+bug/279693")

I had the same problem with last debian lenny. May be the problem is the maxtor hard disk  the sata controler driver.

I had no problems with any 6.06....to 8.04.1 but it seems that something has changed in this last kernel. 2.6.27-6

Any solution?:(

Did 2.6.27-5 work fine for you?  What was the last good working kernel?  And are you able to pull it up in grub still?  And are you able to take a look at the syslog and see if there are any errors?

---

