---
title: "Dell Inspiron 6400 - No network after Ubuntu 13.04 installation"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by tomie on 2013-05-01
I was a happy user of Ubutnu on my laptop Dell Inspiron 6400  until the release of Ubuntu 13.04. After installing 13.04 Ubutnu system is unusable - not detected network card or wifi card (but that's normal, I always have to install packages b43 ...). The problem is also the fact that the notebook can't shutdown, it stays in the shutdown screen.
When the system ran from Live DVD everything runs fine - network card and restart the system. I tried several times to download the DVD image and install from USB or from DVD.

Any ideas?
nejede sí&#357;...
My hardware:
```


cpu:                                                            
                       Genuine Intel(R) CPU           T2400  @ 1.83GHz, 1333 MHz
                       Genuine Intel(R) CPU           T2400  @ 1.83GHz, 1833 MHz
keyboard:
  /dev/input/event3    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      SynPS/2 Synaptics TouchPad
graphics card:
                       ATI Radeon Mobility X1400
sound:
                       Intel 82801G (ICH7 Family) High Definition Audio Controller
storage:
                       Intel 82801GBM/GHM (ICH7 Family) SATA IDE Controller
network:
  eth1                 Dell Inspiron 6400
  wlan0                Dell Wireless 1390 WLAN Mini-Card
network interface:
  wlan0                WLAN network interface
  eth1                 Ethernet network interface
  lo                   Loopback network interface
disk:
  /dev/sda             ST9500420ASG
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda3            Partition
  /dev/sda4            Partition
  /dev/sda5            Partition
cdrom:
  /dev/sr0             TSSTcorp DVD+-RW TS-L632D
usb controller:
                       Intel 82801G (ICH7 Family) USB UHCI Controller #1
                       Intel 82801G (ICH7 Family) USB UHCI Controller #2
                       Intel 82801G (ICH7 Family) USB UHCI Controller #3
                       Intel 82801G (ICH7 Family) USB UHCI Controller #4
                       Intel 82801G (ICH7 Family) USB2 EHCI Controller
bios:
                       BIOS
bridge:
                       Intel Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
                       Intel Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
                       Intel 82801G (ICH7 Family) PCI Express Port 1
                       Intel 82801G (ICH7 Family) PCI Express Port 4
                       Intel 82801 Mobile PCI Bridge
                       Intel 82801GBM (ICH7-M) LPC Interface Bridge
hub:
                       Linux 3.5.0-27-generic uhci_hcd UHCI Host Controller
                       Linux 3.5.0-27-generic uhci_hcd UHCI Host Controller
                       Linux 3.5.0-27-generic uhci_hcd UHCI Host Controller
                       Linux 3.5.0-27-generic ehci_hcd EHCI Host Controller
                       Linux 3.5.0-27-generic uhci_hcd UHCI Host Controller
memory:
                       Main Memory
firewire controller:
                       Ricoh R5C832 IEEE 1394 Controller
bluetooth:
                       Dell BCM2045
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Intel 82801G (ICH7 Family) SMBus Controller
                       Ricoh R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                       Ricoh R5C592 Memory Stick Bus Host Adapter
                       Ricoh xD-Picture Card Controller
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device

```

---

### Post by Grassman20 on 2013-05-01
I'm having the exact same problems with the exact same laptop. I installed Xubuntu 13.04 on my Dell Inspiron e1505 (consumer version of the 6400). I've been running a previous version of Xubuntu without any issues, but now, with the upgrade, I have no network interfaces. No eth0 or anything. Also, when I shut it down, it's stuck on the shut down screen forever, just like you said.

It must be a problem specific to something on this laptop because I installed Kubuntu on a different home-built computer and everything is working great out of the box. [I started a thread about it here]("http://www.linuxquestions.org/questions/ubuntu-63/xubuntu-13-04-no-network-interfaces-4175460242/"), but haven't gotten resolution yet.

---

### Post by mcphja2 on 2013-05-01
Same laptop same problem. Strange that the live version works and the install does not.

---

### Post by Grassman20 on 2013-05-03
I don't know if this is helpful, but since the network interfaces work  from the live CD, but not after install, I decided to run the lspci  command from both sessions.

Here's the ethernet portion of the output of **lspci -nnn -k** on the installed version with no network interfaces:
```
[SIZE=2][FONT=lucida console]03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
        Subsystem: Dell Inspiron 6400 [1028:01af][/FONT][/SIZE]
```

Here's the ethernet portion of the output of **lspci -nnn -k** on the live CD version with functional network interfaces:
```
[SIZE=2][FONT=lucida console]03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
        Subsystem: Dell Inspiron 6400 [1028:01af]
        Kernel driver in use: b44[/FONT][/SIZE]
```

I see the live CD is using kernel driver b44, but it's missing from the actual install. Is there some way to manually install this from a USB drive or something? Seems like it's just a missing driver.

---

### Post by tomie on 2013-05-08
I've found a solution! It's all the bad image fault. Downloading over HTTP makes often damages to the ISO. Torrent is checking the file after download.
After installation from ISO downloaded via torrent network is working correctly and it is able to shutdown as well.

---

### Post by Grassman20 on 2013-05-08
> **tomie said:**
> I've found a solution! It's all the bad image fault. Downloading over HTTP makes often damages to the ISO. Torrent is checking the file after download.
After installation from ISO downloaded via torrent network is working correctly and it is able to shutdown as well.

Well, I'm glad you got it working, but it won't work for me. I downloaded mine via bittorrent and still have the issues. I even downloaded it again and installed again and the issue persists. Oh well, I've moved on to something else. No Xubuntu for me.

---

### Post by tomie on 2013-05-08
Try to run Ubuntu live from DVD, update it and than install. It worked for me twice.

---

### Post by iantaylor01 on 2013-05-08
Having the same problem on Dell Inspiron 640m

I initially took the update from 12.10 via the software center, on restarting I lost all network connections and ubuntu would not shut down.

I then downloaded the ISO and reinstalled from scratch and I got the same issue.

Then installed by booting up via USB stick to desktop first and then selecting install from Launcher - this time it was OK but my network connection may have been loose??
So restarted (removing USB stick) - all was OK, I then took the updates offered by the update manager and selected the wifi restricted driver and then on restart (from updates) I lost all the network connections again and could now see no restricted drivers listed (before I had two - one for wifi and another unknown??)...

Could it be something to do with a faulty update or the restricted wifi driver?

---

### Post by tomie on 2013-05-09
I',m not using restricted drivers for wifi, I'm using b43:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

---

### Post by iantaylor01 on 2013-05-09
The problem I believe is with the wireless driver/package (not the general updates).

If I remove [FONT=Ubuntu Mono]bcmwl-kernel-source:
[/FONT]
sudo apt-get remove bcmwl-kernel-source

Then network connection comes back.I don't know now what to do to get wireless running not using [COLOR=#222222]bcmwl-kernel-source? Anyone any ideas?[/COLOR][FONT=Ubuntu Mono]
[/FONT]

---

### Post by tomie on 2013-05-09
What wifi card do you have? I've got the Dell wireless 1390 WLAN mini-card and the only one way to make it work is to disable driver in additional drivers at Software & Updates dialog (don't know exactly how it is named in EN localization, I'm using CS) and to install the b43 drivers (see above)...
I've got no experience with the bcmwl-kernel-source...

---

### Post by iantaylor01 on 2013-05-09
With the help of this thread this is what I found (and I now have wire and wireless network connections working)

The auto update from 12.10  to 13.04 and when I did a fresh install from a USB ISO download from the main ubuntu site and included "download updates while installing" both left me with no network connect or wireless options.

(when I installed from the USB drive ISO copy and did not select "download updates while installing" it was OK - but then if I selected the "additional driver" broadcom 802.11 STA driver from bcmwl-kernel-source in "software and updates" (or installed from command line) - then on restarting the laptop I lost all network connections and "additional drivers" tab was now blank so I could not disable it).

The loss of network connection for me was resolved by removing the bcmwl-kernel-source:

sudo apt-get remove bcmwl-kernel-source

Then to get the wifi working tomie's line of code above worked:

sudo apt-get install b43-fwcutter firmware-b43-installer

I hope this helps others and thanks for your help tomie

---

### Post by barlandnewhouse on 2013-05-25
I have the Dell Insperion 1501.  Same issue after upgrade.  I did like these folks advised and uninstalled the proprietary drivers for the belkin wireless.  When I did that my wired ethernet started working.   I then installed the drivers the person above recommended.  They must be generic.  When completed my laptop function key to turn the wireless on and off started to work. It wasn't previously. The network icon then became populated with my wireless networking options. 

However, before the upgrade and using the proprietary drivers, my signal strength icon stayed steady.  (my chair is right next to the router) After the upgade and the fix mentioned, I find that my meter fluctuates randomly through the entire range meter (weakest to strongest).  I have not noticed any problems with things working.   

Question:  could this be a result of the 1. Generic Drivers, 2. The skin not working properly and my signal strength is just fine, 3. Some other settings that may need to be changed or tweaked. ???  Or none of the above.

Until it becomes a problem I do not really have an issue with it.  However I thought I should mention it.

On a side note,  I found that my ATI proprietary video drivers no longer exist after the upgrade. Are they not proprietary anymore?  Where did they go?  This is an isssue for me, because 3 out of 5 boots I get buzzing vertical lines filling the screen and I have to reboot to get a working screen.  I found to that if I close the laptop lid and then open it I get the logon for xubuntu.  

Any information would be welcome.

---

### Post by migs73 on 2013-06-03
Thanks folks,

Also sorts the same issues (No networks/no shutdown) on a Dell Inspiron 1501 with the  Broadcom BCM4311 network controller and a BCM4401 Ethernet controller.
I almost re installed 12.04!!!!

Mike

---

### Post by ahallubuntu on 2013-06-03
Anyone with one of these same vintage Dell laptops should consider replacing the Broadcom wireless card with an Intel card - the Intel WiFi Link 5100 card has worked great for me in several Dell laptops, including two 6400's.  (In fact, Ubuntu 12.04 LTS works beautifully on them; I use Gnome Classic (no effects) to get the best performance and don't use Unity.)  I can't speak of the costs in Scotland or elsewhere, but here in the US, one can obtain one of these  Intel wireless cards for about $5 USD shipped (used card).  For the 6400 (and probably the 1501) you need a full-height wireless card (not half-height - the 5100 comes in both sizes), and you want a card that is *NOT* designed for HP/Lenovo/IBM.  That card probably won't work in a Dell laptop.  But any other variation of the 5100 (for Toshiba, Acer, etc.) should work fine.

Dell has service manuals on its website showing you how to replace the wireless card on any laptop.  On the 6400 (aka E1505), you have to remove the keyboard, but that's quite easy.  There are YouTube videos demonstrating how to replace a wireless card and probably one or more showing how to replace it on a 6400.

Don't try to upgrade the wireless card on an HP or Lenovo laptop - those companies "whitelist" their wireless cards, limiting which cards will operate in the laptop.  Dell does not do this, so upgrading a Dell laptop should be easy in most cases.

---

### Post by bijuneyyan on 2013-06-15
> **iantaylor01 said:**
> The loss of network connection for me was resolved by removing the bcmwl-kernel-source:

sudo apt-get remove bcmwl-kernel-source

Then to get the wifi working tomie's line of code above worked:

sudo apt-get install b43-fwcutter firmware-b43-installer

I hope this helps others and thanks for your help tomie

Thanks Taylor and Tomie!
Those two tiny commands worked the best out of my 1505!

Thanks again!

---

### Post by jeh311 on 2013-07-04
on a fresh install of Ubuntu 13.04 on a Dell Inspiron 1521 this code worked for me in the terminal after and update "sudo apt-get install b43-fwcutter firmware-b43-installer". before after i would install wireless i would lose my network completely on the laptop. Thanks very much this really helped me out.

---

### Post by cray5656 on 2013-10-14
I am having the same issue on my sons Insp 6400

After trying to enter any of the above code i get

E: dpkg was interrupted, you must manually run sudo dpkg --configure -a' to correct the problem

I am a noob to ubuntu still so not sure what I have to do now?

---

### Post by zKhtdyX on 2013-10-25
bcmwl-kernel-source blacklists kernel modul b44 in  /etc/modprobe/blacklist-bcm43.conf which is needed for ethernet  controller bcm4401

Please check yourself and vote here: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1244587](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1244587)

---

