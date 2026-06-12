---
title: "Unable to install ZTE AC 8710 on ubuntu 9.10"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by wish519_subhedar on 2009-12-09
[LEFT][B]Hi,
i  am using  the 9.10 version of ubuntu and trying to install reliance net connect broadband + ZTE AC 8710 card. I was following the instructions given on the forum as follows:--
[/B]
1. connect your modem. after a while it shows up as a cd rom drive and you'll see the desktop icon. 
   now open terminal and give the command "lsusb". a list will come up showing all the connected devices. 
find something like this "Bus 004 Device 003: ID 19d2:fff6". here fff6 is the device id. all we have to do is to change it from fff6 to fff1. for this we need a package called "usb_modeswitch". 
 
2. [http://www.draisberghof.de/usb_modes...-1.0.5.tar.bz2]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch-1.0.5.tar.bz2") 
this is the link to download. get it anyhow(by using windows or using mobile broadband or from another computer).then extract it in a directory accessible by linux. 
3. now open terminal and get root privilage.(to do this type "sudo su" and press enter. you will be prompted for password. type it. it will be invisible, but don't worry. just type and press enter. you should see the command line ending with #. that means you got the privilage.) 
4. now go to the directory in which you extracted the usb_modeswitch from terminal with root privilage. 
5. give the command "make". 
6. then give the command "make install". 
7. the package will be installed.
8. now a file will be created naming "usb_modeswitch.conf" in the directory "/etc". now you have to edit this file with root privilage.
9. to do this give the command in terminal "sudo gedit /etc/usb_modeswitch.conf"
10.this file will be opened in gedit text editor. now scroll below and find your device. it will be displayed like this:
    
    # ZTE MF622 (aka "Onda MDC502HS")
    #
    # Contributor: andylog

    ;DefaultVendor=  0x19d2
    ;DefaultProduct= 0x2000

    ;TargetVendor=   0x19d2
    ;TargetProduct=  0x0002

    # only for reference and 0.x versions
    # MessageEndpoint=0x04

   ;MessageContent="55534243f8f993882000000080000a850  10101180101010101000000000000"

11.find your device and delete the semicolon signs of lines starting with ";"(simply unquote). it should look like this:

   # ZTE MF622 (aka "Onda MDC502HS")
   #
   # Contributor: andylog

   DefaultVendor=  0x19d2
   DefaultProduct= 0x2000

   TargetVendor=   0x19d2
   TargetProduct=  0x0002

   # only for reference and 0.x versions
   # MessageEndpoint=0x04

   MessageContent="55534243f8f993882000000080000a8501  0101180101010101000000000000"
12.save the file.
13.give the command "usb_modeswitch" with root privilage.
14.after the execution give command "lsusb". you will see that the device id has been changed from "fff6"
   to "fff1".
15.the 1st stage is complete. now Give parameters to kernel for identification of the modem. to do this
give the command "modprobe usbserial vendor=<vendor id> product=<product id>" (just type the target vendor id and target product id from usb_modeswitch)
16.you must have "libusb" installed.if not then get a temp net connection and run "sudo apt-get install libusb-dev" with root privilage.if u face any problem then update packeges and try again.now use wvdialconf to configure internet.to do this you have to install the package named "wvdial"
you can try downloading from another computer but i tried and failed. so i used my mobile to get the net connection in my linux and gave the command in terminal "sudo apt-get install wvdial". the package will be installed. a file named "wvdial.conf" will be created in "/etc".
17.to activate give command "wvdialconf /etc/wvdial.conf".
18.now you have to edit the file "wvdial.conf". to do this give command "sudo gedit /etc/wvdial.conf"
19.when the file opens in gedit Enter the following Details.
20.Phone=#777
   username=<phone number>
   password=<phone number>
   and don't forget to delete the semicolons of the above lines.
21.now you are done. run the command "wvdial" in terminal with root privilage. your internet connection will be established.
   (N.B.-the network icon will not show any active connection. but that will be no problem.)

[B]However now my datacard is not showing on the desktop itself which is happening only after following the instructions mentioned above. 
if i give the command "lsusb"  [/B]the terminal shows the following:--
[B]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 005: ID 19d2:fff1 ONDA Communication S.p.A.

When i give the command usb_modeswitch the terminal shows the following :--

* usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for target devices ...
 Found devices in target mode or class (1)
Looking for default devices ...
 No default device found. Is it connected? Bye.

Can anybody please help on the same thanks!

[/B][/LEFT]

---

