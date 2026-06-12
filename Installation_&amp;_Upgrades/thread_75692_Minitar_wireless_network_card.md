---
title: "Minitar wireless network card"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by breezey on 2005-10-14
I just got my Ubuntu CD and want to install it on my computer. I connect to the internet using wireless network card from Minitar. Anyone here can confirm me if my network card will be recognized automatically by Ubuntu?

A while a go I installed Fedora 2 and found it very hard to get my wireless network card installed and finally I just uninstalled Fedora. I really want to try Linux but I always have problem with the internet connection due to unrecognized wireless network card.

My network card does come with Linux driver but it is just hard for me to follow the installation instruction.

---

### Post by breezey on 2005-10-14
Hello... anyone could give me some information?

---

### Post by llamakc on 2005-10-14
[quote=breezey]
My network card does come with Linux driver but it is just hard for me to follow the installation instruction.[/quote]

What do you not understand about the instructions for your card?

Also, please be more specific and tell us which card you have. Some of them appear to work out-of-the-box.

---

### Post by buberfan on 2005-10-14
I also have a Minitar card and can confirm that it works fine with Hoary.  Will be installing Breezy tomorrow but don't anticipate any problems.

Basically you have to compile a module from the source-code that Minitar provide.  The catch is that you can't do this unless you download a few other things first, like the kernel sources, GCC etc.  Do you have an ethernet connection as well?  If so this is doable.  Otherwise you could try Kanotix, which comes with the module already compiled (its called rt2400 I think).

Its getting rather late down under in Melbourne, and I'll be heading to bed soon.  I'll check this thread again tomorrow and see if I can be any more help.:D

---

### Post by buberfan on 2005-10-15
OK, in brief this is how you do it:

You need to download and install (using the package manager) the following packages:  build-essential, linux headers, automake1.9 and GCC3.4  Then you should be able to compile the rt2400 module OK.  To compile, you download the source package from minitar, extract it, open a console in the directory labeled "module" and the type "make", and then "make install".

There are also a couple more steps:

You need to open the file /etc/modprobe.d/aliases and add the following line:

alias ra0 rt2400

then you need to add a line in the file /etc/network/interfaces (you will have a line already about device eth0.  Add a line along similar lines for the device ra0, depending on whether your network uses DHCP or not.

  I've now done this and it works fine under Kubuntu breezy.

---

### Post by breezey on 2005-10-16
Here is the instruction I found in the manual:

> * README
*
* Ralink Tech Inc.
* 
* [http://www.ralinktech.com](http://www.ralinktech.com)
*

=======================================================================
ModelName:
===========
RT2500 b/g 


=======================================================================
Description:
=============
This is a linux device driver for Ralink RT2500 b/g WLAN Card.


=======================================================================
Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later, Fedora Core 1, Suse 8.0,8.1,9.0, 
Mandrake 9.0->10.0, Slackware 9.0,9.1, LinEX-r1, gnuLinEX2004


=======================================================================
Contents:
=============
./2.4.x  : Makefile for kernel 2.4 series
./2.6.x  : Makefile for kernel 2.6 series
./suse   : boot script for suse
*.c	: c files
*.h	: header files


=======================================================================
Build Instructions:  
====================
For 2.4 series kernel:
1) $tar -xvzf RT2500-Linux-STA-x.x.x.x.tar.gz
    go to "./RT2500-Linux-STA-x.x.x.x/Module" directory.  
2) cp ./2.4.x/Makefile .  
3) Use 'chmod' command to change access right of following script files :
   'load', 'unload', 'Configure' 
4) $make config         # config build linux os version
5) $make all            # compile driver source code
6) $load                # load/insmod module(rt2500.o)
7) make install		#
Note: Script functionality:
load            load module to kernel
unload          unload module from kernel
Configure       retrive linux version 


For 2.6 series kernel:
1) cp ./2.6.x/Makefile 
2)  $make -C /path/to/source SUBDIRS=$PWD modules
    Where /path/to/source is the path to the source directory for the (configured and built) target kernel.
3)  run '/sbin/insmod rt2500.ko'  (as root)
        '/sbin/ifconfig ra0 inet YOUR_IP up' 
4) uncomment the line include ./config.mk in Makefile
5) make install

=======================================================================
Features:
==========
   This driver implements basic IEEE802.11. Infrastructure and adhoc mode with open or shared or WPA
   authentication method. WEP-40 and WEP-104, TKIP and AES encryption, 
   
   
=======================================================================
To BUILD UTILITY
====================

1)  go to the "./Utility" directory
2)  run 'qmake -o Makefile raconfig2500.pro'
    If qmake command is not found in your system, you can download the QT tool 
    'qt-x11-free-3.2.1' or later at 
    [http://www.trolltech.com/](http://www.trolltech.com/)
    
    (qmake comes with RedHat 7.3 or later QT Package)    

3)  run 'make" to compile the utility source code.   
4)  After all, an execution file would be generated "RaConfig2500"
    run "RaConfig2500" to config the driver as you want


=======================================================================
CONFIGURATION:  
====================
RT2500 driver can be configured via following interfaces, 
i.e. 1)partial wireless extension command, 2)"iwpriv" command, 3) RaConfig2500

1)  iwconfig, and iwlist scanning.  
2) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.
3) RT2500 provides API : RaConfig2500, please go to directory ./Utility and refer to how-to-compile.txt

           
=======================================================================
MORE INFORMATION:  
====================
1) Though we allow a configuratino file for ra0 when initializing our modules,
reading a file when installing a modules in linux is not recommended. 
If you want to enable this function, umcomment the line " RTMPReadParametersFromFile(pAd);" 
in rtmp_main.c

NOTE:
   if you use dhcp, add this line in boot script according to your linux distribution.
    BOOTPROTO='dhcp'
    To ease the Default Gateway setting, add the line
    GATEWAY=x.x.x.x 

Will be great if some can give me an "IDIOT" GUIDE to install my network card. Don't assume that I understand to much about that terms such as makefile, make install, etc. I really need an ABC steps to install it. Thanks for your help.

For your info, I have successfully installed UBUNTU Version 5.04 on Intel P4 1.8 GHz as dual boot with Windows XP. Ubuntu recognized and installed my DLINK network card but it did not even recognize my Minitar wireless network card. Unfortunately I cannot use my DLINK network card as the modem is a bit far from the PC and I don't want to run cable from my machine to the modem.

---

### Post by breezey on 2005-10-16
This is what I've done:

[LIST]
[*]I assume that the kernel on my Ubuntu system is 2.6
[*]Copy RT2500-Linux-STA-x.x.x.x.tar.gz file to Home folder
[*]$tar -xvzf RT2500-Linux-STA-x.x.x.x.tar.gz
[*]go to "./RT2500-Linux-STA-x.x.x.x/Module" directory. 
[*]cp ./2.6.x/Makefile .
[*]Then I am lost. I did not now the path to source directory for the targeted kernel.
[/LIST]

---

### Post by buberfan on 2005-10-16
OK: some questions first.

1)  Are you using Kubuntu or Ubuntu?

2)  Can you use the cable connection to download stuff at least until you have set up the minitar card?

I am using Kubuntu, and can try to guide you through this.  But you will need to download some extra stuff if you want to use the Minitar card.

---

### Post by breezey on 2005-10-16
1) I think I use Ubuntu. It runs on GNOME. I install my Ubuntu from the free CD shipped to me.
2) I can't really connect to the Internet using Linux but I can connect to the Internet using Windows so if I need to download anything I can just download it first and put it onto a CD.

---

### Post by breezey on 2005-10-17
Anyone can help me please... :confused:

---

### Post by breezey on 2005-10-19
> 2) $make -C /path/to/source SUBDIRS=$PWD modules
Where /path/to/source is the path to the source directory for the (configured and built) target kernel.
In the case of my Ubuntu 5.04, what is the path to source directory for the (configured and built) target kernel? Thanks for your help. I really want to get my network card running on Linux.

---

### Post by buberfan on 2005-10-19
Sorry for not getting back sooner!  

I'm not sure if you can get this to work unless you can connect via a cable to the internet.  There are some instructions for using the RT2500 module that Minitar uses [here]("//https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo?highlight=%28RT2500%29"):

Let me know how it goes.

---

### Post by buberfan on 2005-10-19
The path to the kernel source directories in Ubuntu is:
/usr/src/linux-whateverkernelversionyouhave

However, on a default install you don't have the kernel source codes and headers there, just a kernel image.  This is why before you can compile the driver for the minitar card you need to install the kernel headers.  The easiest way to do this is to connect online via an ethernet connection and then use either synaptic or the apt-get command to install the kernel-headers package.  As I said above, you will also need to install a few other packages before you can compile the driver: namely build-essentials, automake1.9 and gcc-3.4

---

### Post by breezey on 2005-10-23
Buberfan, after following the instruction on [the link]("https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo?highlight=%28RT2500%29") you gave me, I finally can get my network card working. But from "Installing RaConfig, and using it" part the command lines were not working on my system. I stopped there and my network card works. The only problem is that I have to repeat few command lines everytime I reboot my Ubuntu before I have my network card working. How can I save the configuration so that I don't need to re-execute the command lines?

It could be related to "And What If I Don't Need RaConfig" part, but I was not successful in following the instruction. Any tips? Thanks.

---

### Post by buberfan on 2005-10-23
You don't need Raconfig, but can do the following:
1 edit the file /etc/modprobe.d/aliases and add the line "alias ra0 rt2500" if it isn't already there.  (You will have to do this as superuser or sudo.  Be sure to make a backup copy of the file first)

2 edit the file /etc/network/interfaces similarly.  In the section
"mapping hotplug
	script grep
	map eth0"
add underneath "map ra0"

and then at the end of the file add these lines

"# The wireless interface
iface ra0 inet dhcp"  (this is assuming you use dhcp to dynamically assign your IP address)

See if that helps

---

### Post by breezey on 2005-10-24
[QUOTE=buberfan]
"# The wireless interface
iface ra0 inet dhcp"  (this is assuming you use dhcp to dynamically assign your IP address)
[/QUOTE]
Thanks buberfan, you are very helpful.

I don't use dhcp on my home network. I assign the IP address manually. How does this affect the command that i should add on the file you mentioned above?

---

### Post by buberfan on 2005-10-24
I'm out of my experience range here, but try

"iface wlan0 inet whatever-your-IP-address-is
wireless_essid whatever-your-essid-is, or "any"
wireless_key whatever-your-key-is (or leave this line out if you don't use WEP)
wireless_channel 11 (trial and error here, or leave this line blank)
wireless_mode managed"

---

