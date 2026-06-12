---
title: "Wifi usb adapter wont work under 64bit"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by yomnym on 2010-03-06
I need some help getting my Rosewill RNX-N1 usb wifi adapter to work in ubuntu.. what can i do, please help.  I really wanna get started with unbuntu but with no internet is a bit hard.  Thanks a lot for your help.

---

### Post by yomnym on 2010-03-06
guys come on, a little help here, i'be searched online and got the latest rt2870 drivers, i cant get anything to run decently.  I need your help, i have at hand the above mentioned USB adapter and a D-link DWA-140.  Any help would really save me some head aches.  Thanks a lot.

---

### Post by gordintoronto on 2010-03-07
You might be aware that Rosewill is Newegg's house brand for devices manufactured by other companies.  To find out what your wireless adapter really is, run this command in Accesories/Terminal:
lsusb

According to this web page:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB)

the D-Link adapter should "just work." The driver is built-in with Linux.

That means, when you boot up with the D-Link installed, you can right-click on the networking icon near the top-right of your screen, next to the volume control. Select Edit Connections. Select the Wireless tab and the Add button, provide the SSID of your router, the encryption type and password, and it should connect.

---

### Post by yomnym on 2010-03-07
Well i went ahead and tried with the Dlink being that its supposed to be more compatible or "work" with 9.10.  The network manager does recognize the WLAN but it just didn't recognized any networks, i had to install the drivers for the RT2870 chipset which is what the D link 140 uses, [this ]("http://www.apfelkraut.org/2009/02/howto-wlan-ralink-rt2870-usb-stick-kubuntu-810/")was what got me through, then reboot and everything worked.  I really appreciate your reply.

---

### Post by yomnym on 2010-03-11
```
   	 	 	 	 	 	  [SIZE=2]1.) First thing is to prepare the system for the driver compilation. Therefore it is needed to install certain tools and the headers of the running kernel:[/SIZE]
 


     [SIZE=2]* sudo apt-get install build-essential linux-headers-`uname -r`[/SIZE]
 


 [SIZE=2]2.) Now the source for the Linux driver needs to be downloaded from the Linux support page of Ralink Technology.[/SIZE]
 


     [SIZE=2]* Download this package (alternative mirror):[/SIZE]
       [SIZE=2]wget [/SIZE][[COLOR=#0000ff][SIZE=2]_http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1EQTVMekV5THpFMUwyUnZkMjVzYjJGa05UYzBNVFExTkRNNU5TNWllakk5UFQxU1ZESTROekJmVEdsdWRYaFRWRUZmVmpJdU15NHdMakF1ZEdGeUxuUmhjZz09Qw%3D%3D_[/SIZE][/COLOR]]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1EQTVMekV5THpFMUwyUnZkMjVzYjJGa05UYzBNVFExTkRNNU5TNWllakk5UFQxU1ZESTROekJmVEdsdWRYaFRWRUZmVmpJdU15NHdMakF1ZEdGeUxuUmhjZz09Qw%3D%3D")
     [SIZE=2]* Extract it somewhere:[/SIZE]
       [SIZE=2]tar xvfj RT2870_LinuxSTA_V2.3.0.0.tar.tar.bz2[/SIZE]
 


 [SIZE=2]3.) Now the support of wpa_supplicant should be enabled in the file os/linux/config.mk of the driver package.[/SIZE]
 


     [SIZE=2]* Open the file with your favorite text editor, for example GNU Emacs:[/SIZE]
       [SIZE=2]emacs os/linux/config.mk[/SIZE]
     [SIZE=2]* Change the following attributes from “no (=n)”:[/SIZE]
 


           [SIZE=2]# Support Wpa_Supplicant[/SIZE]
           [SIZE=2]HAS_WPA_SUPPLICANT=n[/SIZE]
 


           [SIZE=2]# Support Native WpaSupplicant for Network Maganger[/SIZE]
           [SIZE=2]HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n[/SIZE]
 


       … [SIZE=2]to value “yes (=y)”:[/SIZE]
 


           [SIZE=2]# Support Wpa_Supplicant[/SIZE]
           [SIZE=2]HAS_WPA_SUPPLICANT=y[/SIZE]
 


           [SIZE=2]# Support Native WpaSupplicant for Network Maganger[/SIZE]
           [SIZE=2]HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y[/SIZE]
 


 [SIZE=2]4.) Afterwards the driver needs to be build and installed. Make sure to execute both commands in the root of the driver package and with superuser privileges:[/SIZE]
 


     [SIZE=2]* sudo make[/SIZE]
     [SIZE=2]* sudo make install[/SIZE]
 


 [SIZE=2]5.) Last thing is to add this driver to /etc/modules so that it is loaded automatically every time the system is rebooted.[/SIZE]
 


     [SIZE=2]* Open the file with your favorite text editor, for example GNU Emacs:[/SIZE]
       [SIZE=2]emacs /etc/modules[/SIZE]
     [SIZE=2]* Add the following line:[/SIZE]
       [SIZE=2]rt2870sta[/SIZE]
 


       [SIZE=2](others reported that they had only success by adding “alias ra0 rt2870sta“) [/SIZE] 
 


 [SIZE=2]6.) If you do not want to reboot your machine, you should execute the following two lines with superuser privileges to load the driver and to integrate it in your networking configuration:[/SIZE]
 


     [SIZE=2]* sudo modprobe rt2870sta[/SIZE]
     [SIZE=2]* sudo /etc/init.d/networking restart[/SIZE]
 
```

---

