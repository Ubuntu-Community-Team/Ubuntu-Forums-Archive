---
title: "Wifi Installation problems"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by Studiologe on 2011-08-20
Hello All-together,
I'm new to the Ubuntu world and new to this Forum, so first of all I wanna say Hi to everyone!
I highly appreciate everyonce help and consideration for actually taking the time to read my post and helping me out.
Thanks in advance for any support!!!

I'm using a Ubuntu 10.x distro and I recently bought myself a new
wifi adaptor. The NextG Yagi, but I have severe problems installing it and understanding the Instructions which are not well written.

On the CD there is following Folder structure with files:
Linux/Firmware/RT2870_Firmware_V22.zip
Linux/2010_0709_RT2870_Linux_STA_v2.4.0.1.tar.bz2
Linux/2011_0107_RT3070_RT3370_Linux_STA_v2.5.0.1_DPO.tar.bz2

I tried to install the more recent recent tar.bz2 file contents.
After unzipping this tarball i tried to understand the instructions in the README file (see attachment)

Here are the instructions from the file attached:
======================================================
Build Instructions: 
====================
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
=======================================================
1) Is clear, got that
2) What do i have to do here? Go into the file and replace every MODE with STA and every TARGET with LINUX? (File is attached and renamed to .txt)
3) What's this? I usually use wicd and then I choose my wireless network and connect, so which build option should I choose and then how
would I have to proceed? (I guess just execute the commands shown, once I know which build option I need?)
4) Just make and if I get that error execute the patch.... command right?
5) just copy that file I guess...
====== Do I always have to do the following steps? Once I want to use it and once I'm done using it, or can I automate this? ========
6) Here's the trouble, how do I find which kernel I have? And does IP stand for IP-Address here? I usually get my IP via DHCP... and what's inet?
ra0 is I believe the wifi adaptor
7) ifconfig ra0 down (No questions)
   rmmod rt2870sta, what does this do??


I hope I gave you enough information and that hopefully somebody will be so genorous and spend his time explaining my
questions to give me some more confident with my brand new OS :) 
Thanks

---

### Post by steve11911 on 2011-08-22
Welcome to the forum.

From the readme.txt and part of your post I ASSUME you would like to install the ralink wireless driver 2870 on ubuntu 10.x.

This page should help:

[http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html](http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html)

If on the other hand if you actually want to set up  The NextG Yagi...(ok)then:

[http://forums.whirlpool.net.au/forum-replies.cfm?t=1655939](http://forums.whirlpool.net.au/forum-replies.cfm?t=1655939)

---

