---
title: "New ubuntu install havin probs with wireless."
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by babybash on 2008-02-19
Hi my new laptop arrive today and it came with vista pre loaded (yuk) i have decided to to install ubuntu 7.10 and it seemst have only 1 prob!!
The laptop is wireless and bluetooth enabled now i checked the wireless before i installe linux and it worked fine but after i installed it i cant connect wireless mycomp knowledge is limited i really could do with a little help as my main pc is also running linux with a minor hitch ( i have opened a new topic for the main pc) please please could you help on the wireless situatuion as im not sure how to sort it and i really dont want to run vista it makes my laptop run soooooooo slow its unreal!!
Thankyou in advance.

---

### Post by Partyboi2 on 2008-02-19
Open a terminal Applications>Accessoiries>Terminal
and type
```
lspci
```
post the output here and someone will probably be able to point you in the right direction. If you can post all of it then post the lines that list your wireless

---

### Post by babybash on 2008-02-19
anthony@anthony-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
anthony@anthony-laptop:~$ 
Ok i hope someone can sypher some sense out of this.....
Thanks in advance.

---

### Post by Partyboi2 on 2008-02-19
try [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") how-to. 
This is your wireless info: 
Broadcom Corporation BCM4310 USB Controller (rev 01)

---

### Post by babybash on 2008-02-19
Ok i think ive done it wrong but im not sure wher it keeps telling me that somthing is missing?? ive posted the whole lot so far but in the last few lines its there and also further up i assumed that i would install that bit later, How wrong was i lol.
anthony@anthony-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
anthony@anthony-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ndiswrapper-common
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed
  ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/52.7kB of archives.
After unpacking 238kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media Change: Please insert the disc labelled
 ‘Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)’
in the drive ‘/cdrom/’ and press enter

Selecting previously deselected package ndiswrapper-common.
(Reading database ... 88932 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.43-1ubuntu2_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb) ...
Setting up ndiswrapper-common (1.43-1ubuntu2) ...
Setting up ndiswrapper-utils-1.9 (1.43-1ubuntu2) ...
anthony@anthony-laptop:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
anthony@anthony-laptop:~/bcm43xx$ 
anthony@anthony-laptop:~/bcm43xx$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cabextract
anthony@anthony-laptop:~/bcm43xx$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cabextract
anthony@anthony-laptop:~/bcm43xx$ wget [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)
--15:07:59--  [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)
           => `sp33008.exe'
Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp33001-33500 ... done.
==> PASV ... done.    ==> RETR sp33008.exe ... done.

    [                                                  <=>                                                             ] 4,318,656     15.12K/s             

15:13:00 (14.12 KB/s) - `sp33008.exe' saved [4318656]

anthony@anthony-laptop:~/bcm43xx$ cabextract sp33008.exe
The program 'cabextract' is currently not installed.  You can install it by typing:
sudo apt-get install cabextract
You will have to enable component called 'universe'
bash: cabextract: command not found
anthony@anthony-laptop:~/bcm43xx$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cabextract
anthony@anthony-laptop:~/bcm43xx$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cabextract
anthony@anthony-laptop:~/bcm43xx$

---

### Post by fujikofujio on 2008-02-19
I was able to make a dell 1300 usb wifi adapter and 2 different linksys usb adapters work by following this steps on ubuntu 7.10 and 8.04

1. install ndiswrapper-common, ndiswrapper-utils, ndisgtk

sudo apt-get install ndiswrapper-common ndisgtk ndiswrapper-utils-1.9

2. Try to download the driver for the device from the manufacturers website or if you have the driver discs from the manufacturer that will work too.

3. Extract the driver, should have something like
file.cat
file.sys
file.inf

Not necessarily like that but sometimes its close.

4. Then go to System> Administration> Windows Wireless Drivers

5. Click install new driver, browse the location of the inf file and select it.

If everything goes well it should say that hardware is present and you should be able to use the network manager on the system tray to connect to your wifi.

---

### Post by babybash on 2008-02-19
Hi thanks for the help, Im currently running through the process with another also very kind person and i dont want to start doin one thing then start doing somthin else i will try what you have shown me if we cant work it out the other way. I want to try and keep my system as clean as possible as my laptop isnt that powerfull.

---

### Post by Partyboi2 on 2008-02-19
You need to enable the repo to install cabextract.
If you have the laptop wired to the  internet while you are doing this, you need to go to Software Sources (System>Admin>Software Sources) On the first tab tick all of them except source code and under "Installable from cd-rom/dvd" untick the cdrom box. Then on the 3rd tab (updates) make sure all of them are checked. Then close and try installing cabextract again
```
sudo apt-get install cabextract
``` then continue on from there. If you do not have a working wired connecction with ubuntu you can download the package from [here]("http://packages.ubuntu.com/gutsy/cabextract") from windows and transfer it over and install it by double clicking

---

### Post by babybash on 2008-02-20
Ahhhhhhh it still wont work..
I followed the insrutions you gave and it installed a few updates, then i continued to trying to install the drivers etc, I rebooted at the end still nothin so i tryed the procedure again. aim just about to reboot so ive put this post in so you can see what i have done, Thankyou for your help.
anthony@anthony-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
anthony@anthony-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anthony@anthony-laptop:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
mkdir: cannot create directory `/home/anthony/bcm43xx': File exists
anthony@anthony-laptop:~/bcm43xx$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cabextract is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
anthony@anthony-laptop:~/bcm43xx$ wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
--11:08:12--  [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
           => `sp34152.exe'
Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp34001-34500 ... done.
==> PASV ... done.    ==> RETR sp34152.exe ... done.

    [                                                                                                       <=>       ] 4,494,456    215.61K/s             

11:08:36 (207.95 KB/s) - `sp34152.exe' saved [4494456]

anthony@anthony-laptop:~/bcm43xx$ cabextract sp34152.exe
Extracting cabinet: sp34152.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp34152.cva

All done, no errors.
anthony@anthony-laptop:~/bcm43xx$ 
anthony@anthony-laptop:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
anthony@anthony-laptop:~/bcm43xx$ ndiswrapper -l
bcmwl5 : driver installed
anthony@anthony-laptop:~/bcm43xx$ sudo depmod -a
anthony@anthony-laptop:~/bcm43xx$ sudo modprobe ndiswrapper
anthony@anthony-laptop:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
anthony@anthony-laptop:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

anthony@anthony-laptop:~/bcm43xx$ sudo ndiswrapper -m
module configuration already contains alias directive

anthony@anthony-laptop:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
anthony@anthony-laptop:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0
anthony@anthony-laptop:~/bcm43xx$

---

### Post by babybash on 2008-02-20
Well ive followed all the steps and i still cant get it to work i tried 2a and also 2b on the link ive followed it including the section on still not working, who would have thought this could be so hard :lolflag:

---

### Post by Partyboi2 on 2008-02-20
whats the output to this command
```
lshw -C network
```

---

### Post by babybash on 2008-02-21
Hi here is the details.
anthony@anthony-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3a:80:9a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=192.168.1.65 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
anthony@anthony-laptop:~$

---

### Post by dstew on 2008-02-21
It looks like your driver is installed, you just need to configure the wireless network. You can probably use the System --> Administration --> Networking graphical interface.

---

### Post by babybash on 2008-02-21
Hi sorry i dont have a networkin graphical interphase option and i dont know how to do it, im a complete novice to linux!!!
I do have network, and network tools option but i still dont know what im doin!!!!!:(

---

### Post by babybash on 2008-02-21
Hi ive re started this thread in the correct topic area as i have realised it was in the wrong place.
Thankyou for all the help so far.

---

