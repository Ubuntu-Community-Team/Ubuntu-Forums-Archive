---
title: "copy the files that make a good environment to a NAS"
date: 2016-10-20
forum: Installation &amp; Upgrades
---

### Post by LaoziSailor on 2016-10-20
I have an Acer Aspire 1360 laptop that had UbuntuStudio 8.04 Hardy LTS installed and I could not get the EOLUpgrades to work for me. 
OK, no big deal and decided to go for Ubuntu Studio 16 and found that during the installation the messages and screen shows were displayed in 1024x768.
Then after booting the new system I was stuck with a 640x480 that partially showed the screen on available real estate.
I attempted many suggestions  (over 8,351 results from "resolution") with xrandr and others to no avail and decided to go to vanilla with Xenial Xerus 16.04.1 LTS and had the same issue, the only resolution was 640x480.
Then I decided to "try Ubuntu Studio without installing" and was successful in getting the options I want, see screen captures
- [Ubuntu Studio without installing]("https://i.stack.imgur.com/Y98mF.jpg")
- [Ubuntu 5 resolutions]("https://i.stack.imgur.com/SMCYZ.jpg")

The question then is, WHICH files required do I copy for that environment to an accessible NAS such that on completion of a successful install I can copy from the NAS back to the laptop?

Thanks!

---

### Post by TheFu on 2016-10-20
Resolution is determined at run time now.  In the old days, we could override those settings in the xorg.conf file, but that seems to be problematic these days. I've seen reports of xorg.conf being removed (somehow).

The best troubleshooting will come with information about the exact hardware involved.  Which video card and driver(s) are being used?  **sudo lshw -C video** will tell us. Please post the exact output - copy/paste is best - and use code tags so things line up.  If you want, run that command in the working and non-working config to look for differences.

---

### Post by LaoziSailor on 2016-10-20
Thanks for the reply **TheFu**

> **TheFu said:**
> Resolution is determined at run time now.  In the old days, we could override those settings in the xorg.conf file, but that seems to be problematic these days. I've seen reports of xorg.conf being removed (somehow).

The best troubleshooting will come with information about the exact hardware involved.  Which video card and driver(s) are being used?  **sudo lshw -C video** will tell us. Please post the exact output - copy/paste is best - and use code tags so things line up.  If you want, run that command in the working and non-working config to look for differences.

I will attempt your specific video display the next time I boot up, it is quite time intensive on such an old machine.
This I had as I was gathering more information before your reply:
```

ubuntu-studio@ubuntu-studio:~$ sudo xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768      61.00* 
   800x600       61.00  
   720x576        0.00  
   720x480        0.00  
   640x480       60.00  
ubuntu-studio@ubuntu-studio:~$ sudo lshw -short
H/W path        Device      Class          Description
======================================================
                            system         Aspire 1360
/0                          bus            Aspire 1360
/0/0                        memory         111KiB BIOS
/0/4                        processor      Mobile AMD Sempron(tm) Processor 2800
/0/4/8                      memory         128KiB L1 cache
/0/4/9                      memory         256KiB L2 cache
/0/21                       memory         512MiB System Memory
/0/21/0                     memory         256MiB DIMM DRAM Synchronous
/0/21/1                     memory         256MiB DIMM DRAM Synchronous
/0/100                      bridge         K8M800 Host Bridge
/0/100/1                    bridge         VT8237/8251 PCI bridge [K8M890/K8T800
/0/100/1/0                  display        K8M800/K8N800/K8N800A [S3 UniChrome P
/0/100/a                    network        IPN 2220 802.11g
/0/100/b                    bridge         PCI7420 CardBus Controller
/0/100/b.1                  bridge         PCI7420 CardBus Controller
/0/100/b.2                  bus            PCI7x20 1394a-2000 OHCI Two-Port PHY/
/0/100/10                   bus            VT82xx/62xx UHCI USB 1.1 Controller
/0/100/10/1     usb2        bus            UHCI Host Controller
/0/100/10.1                 bus            VT82xx/62xx UHCI USB 1.1 Controller
/0/100/10.1/1   usb3        bus            UHCI Host Controller
/0/100/10.2                 bus            VT82xx/62xx UHCI USB 1.1 Controller
/0/100/10.2/1   usb4        bus            UHCI Host Controller
/0/100/10.3                 bus            USB 2.0
/0/100/10.3/1   usb1        bus            EHCI Host Controller
/0/100/11                   bridge         VT8235 ISA Bridge
/0/100/11.1                 storage        VT82C586A/B/VT82C686/A/B/VT823x/A/C P
/0/100/11.5                 multimedia     VT8233/A/8235/8237 AC97 Audio Control
/0/100/11.6                 communication  AC'97 Modem Controller
/0/100/12       enp0s18     network        VT6102/VT6103 [Rhine-II]
/0/101                      bridge         K8M800 Host Bridge
/0/102                      bridge         K8M800 Host Bridge
/0/103                      bridge         K8M800 Host Bridge
/0/104                      bridge         K8M800 Host Bridge
/0/105                      bridge         K8M800 Host Bridge
/0/106                      bridge         K8 [Athlon64/Opteron] HyperTransport 
/0/107                      bridge         K8 [Athlon64/Opteron] Address Map
/0/108                      bridge         K8 [Athlon64/Opteron] DRAM Controller
/0/109                      bridge         K8 [Athlon64/Opteron] Miscellaneous C
/0/1            scsi0       storage        
/0/1/0.0.0      /dev/sda    disk           100GB Hitachi HTS54121
/0/1/0.0.0/1    /dev/sda1   volume         487MiB Linux filesystem partition
/0/1/0.0.0/2    /dev/sda2   volume         92GiB Extended partition
/0/1/0.0.0/2/5  /dev/sda5   volume         92GiB Linux LVM Physical Volume parti
/0/2            scsi1       storage        
/0/2/0.0.0      /dev/cdrom  disk           UJDA760 DVD/CDRW
/0/2/0.0.0/0    /dev/cdrom  disk           
/0/2/0.0.0/0/1              volume         2677MiB Hidden HPFS/NTFS partition
ubuntu-studio@ubuntu-studio:~$ 
```

---

### Post by LaoziSailor on 2016-10-21
> **TheFu said:**
> ...snip
The best troubleshooting will come with information about the exact hardware involved.  Which video card and driver(s) are being used?  **sudo lshw -C video** will tell us. Please post the exact output - copy/paste is best - and use code tags so things line up.  If you want, run that command in the working and non-working config to look for differences.

```
han@han-Aspire-1360:~$ sudo lshw -C display
[sudo] password for han: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: latency=64 mingnt=2
       resources: memory:f0000000-f3ffffff memory:d1000000-d1ffffff

han@han-Aspire-1360:~$ sudo lshw -C video
[sudo] password for han: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: latency=64 mingnt=2
       resources: memory:f0000000-f3ffffff memory:d1000000-d1ffffff


```

---

### Post by LaoziSailor on 2016-10-22
This is a MAJOR success so far:
```

gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout '0' && gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-battery-timeout '0'
```

you see, I have to keep bed rest as much as possible when I am not in my wheelchair and I drill through a [realVNC.com]("http://www.realvnc.com")  (I  use the free versions) client in my laptop to a realVNC server running on Vista, from where I have a VNC client to the Linux realVNC server on the laptop where I am having the problems!

Having the Ubuntu laptop stay on keeps me from having to jump into my wheelchair to turn the power back on, boot, restart the VNC server, etc. :D

BTW, I found that in [http://askubuntu.com/questions/47311/how-do-i-disable-my-system-from-going-to-sleep]("http://askubuntu.com/questions/47311/how-do-i-disable-my-system-from-going-to-sleep")

---

