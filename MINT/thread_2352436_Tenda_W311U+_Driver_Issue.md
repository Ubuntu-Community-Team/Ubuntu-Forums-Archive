---
title: "Tenda W311U+ Driver Issue"
date: 2017-02-12
forum: MINT
---

### Post by strat1959 on 2017-02-12
I'm a windows user and new to the whole linux environment(apart from dirstos). so, if you want to help me. please give a detailed one.thanks


I get the following errors when i try to use make command in the driver's directory. I read the instructions, but I can't figure it out which one to change(on the third step). I need someone who's kind enough, to download the driver from my google drive(it's 1MB or from tenda's website if you don't trust it), try to compile the driver and tell me what has been changed if it was successfull - also check the instructions at the end please. I want to define/change gcc and ld paths but I don't know which one to change.


The usb adaptor works and connects to my wireless router, but I need to install it's driver properly, I know that If the wireless NIC's driver wasn't installed properly, It would show it as(for example in my case) : wlxc83a35ca5ee6 rather than it's normal name — I need to use this usb adaptor on softwares like wireshark and etc without any issues.


```
os,gcc & ld info on my pc :
Distributor ID:  LinuxMint
Description:  Linux Mint 18.1 Serena
Release:  18.1
Codename:  serena
gcc (Ubuntu 5.4.0-6ubuntu1~16.04.4) 5.4.0 20160609
GNU ld (GNU Binutils for Ubuntu) 2.26.1


Errors :


/home/strat1959/Desktop/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../sta/sta_cfg.c:4987:85: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
 intf(extra, size, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, _
                                                                     ^
/home/strat1959/Desktop/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux/../../sta/sta_cfg.c:4987:95: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]




Instructions:


1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
   set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
   define the linux kernel source include file path LINUX_SRC
   modify to meet your need.


3> In os/linux/config.mk 
  define the GCC and LD of the target machine
  define the compiler flags CFLAGS
  modify to meet your need.
  ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
     Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
     => #>cd wpa_supplicant-x.x
     => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
  ** Build for being controlled by WpaSupplicant with Ralink Driver
     Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
     => #>cd wpa_supplicant-0.5.7
     => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d


4> $make
  # compile driver source code
  # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
    => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c


5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up


7> unload driver    
    $/sbin/ifconfig ra0 down
  $/sbin/rmmod rt2870sta


```
driver's download link :
[https://drive.google.com/open?id=0B1XDUzK97gjrZVdnTjhKeXFSTGM](https://drive.google.com/open?id=0B1XDUzK97gjrZVdnTjhKeXFSTGM)

---

### Post by wildmanne39 on 2017-02-12
Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

wlxc83a35ca5ee6 is the way usb adapters are named in 16.04 and above so there is nothing wrong with that name.

Are you having other issues with your device besides the name?

---

### Post by jeremy31 on 2017-02-13
*Thread moved to **MINT**.*

---

