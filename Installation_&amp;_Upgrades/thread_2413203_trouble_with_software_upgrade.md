---
title: "trouble with software upgrade"
date: 2019-02-22
forum: Installation &amp; Upgrades
---

### Post by coley9225 on 2019-02-22
Let me start by saying I'm a noob at linux based os. I finally got lubuntu 18.04 installed. I used software updater to download and install all updates. It was going fine until it was setting up grub, and it froze there. I waited 45 minutes and it never made a new log entry( I'm assuming what I see it doing is a log). I finally cancelled the install and had to do a hard shutdown. I'm wondering if this has anything to do with my original install issues, and did the other updates were actually installed. I did a screenshot of the window, but now I can't find it, and don't know how to access the log are how to post it. In the future, is there a way to the upgrades without upgrading the grub so I don't have this issue again. Thanks in advance for any help I can get.

---

### Post by TheFu on 2019-02-25
Unfortunately, I don't think any one can provide concrete help since no concrete data was provided.

"software upgrade" can mean multiple different things. Please clarify.

Any hardware you can share?  Laptop or desktop? Brand, model?

Often, stuck installs are due to GPU issues.  Which GPU driver was being used?  GPL or proprietary?

Log files are stored under /var/log/ ...  boot from a live-flash boot drive and find that storage on the other disk, look for the boot.log or install.log, if this is a new install.  While you are at it, install inxi, and run **inxi -Fz** - that's an easy way to provide system information to us here.  Here's mine:
```
$ inxi -Fz
System:    Host: cb35 Kernel: 4.15.0-45-generic x86_64 (64 bit)
           Desktop: Openbox 3.6.1 Distro: Ubuntu 16.04 xenial
Machine:   System: GOOGLE (portable) product: Gandof v: 1.0
           Mobo: GOOGLE model: Gandof v: 1.0
           Bios: coreboot v: MrChromebox date: 02/04/2018
CPU:       Dual core Intel Core i3-5015U (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 2100 MHz 1: 921 MHz 2: 1110 MHz 3: 1563 MHz
           4: 1303 MHz
Graphics:  Card: Intel HD Graphics 5500
           Display Server: X.Org 1.19.6 drivers: (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.02hz
           GLX Renderer: Mesa DRI Intel HD Graphics 5500 (Broadwell GT2)
           GLX Version: 3.0 Mesa 18.0.5
Audio:     Card-1 Intel Wildcat Point-LP High Definition Audio Controller
           driver: snd_hda_intel
           Card-2 Intel Broadwell-U Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-45-generic
Network:   Card: Intel Wireless 7260 driver: iwlwifi
           IF: wlp1s0 state: down mac: <filter>
Drives:    HDD Total Size: 60.0GB (78.8% used)
           ID-1: /dev/sda model: SB_M2_SSD size: 60.0GB
Partition: ID-1: / size: 51G used: 41G (85%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 473M used: 144M (32%) fs: ext2 dev: /dev/sda2
           ID-3: swap-1 size: 4.16GB used: 0.06GB (1%) fs: swap dev: /dev/dm-2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 204 Uptime: 18:31 Memory: 2270.5/3814.7MB
           Client: Shell (bash) inxi: 2.2.35 
```
See how the unique aspects of the machine are stripped out? My point is that I'm not asking for any secret data.

---

### Post by coley9225 on 2019-03-01
As I said, I'm a noob, but I think this is what you were looking for. By software upgrade, I meant I used the software updater included with lubuntu. And to clarify 1 item, my original install issue was install always hangs up at installing grub2 package. I could boot to grub prompt, then set root, vmlinuz, and initrd, and boot to my lubuntu install on my hard drive, but for some reason that's not working either now. I can only but to live usb. I can see my lubuntu and windows partitions, and view the files so they are intact, I just lost my efi partition. I've try to reinstall grub, and run boot-repair, but nothing is working. I see your using a Lenovo, so I know my computer should run Lubuntu, and I'm probably missing something simple(noob mistake..lol).


```
lubuntu@lubuntu:~$ inxi -Fz
System:    Host: lubuntu Kernel: 4.15.0-29-generic x86_64 bits: 64
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: LENOVO product: 80XR v: Lenovo ideapad 320-15IAP serial: N/A
           Mobo: LENOVO model: LNVNB161216 v: SDK0J40700 WIN serial: N/A
           UEFI: LENOVO v: 5RCN36WW date: 08/06/2018
Battery    BAT0: charge: 22.7 Wh 76.0% condition: 29.9/30.0 Wh (100%)
CPU:       Dual core Intel Celeron N3350 (-MCP-) cache: 1024 KB
           clock speeds: max: 2400 MHz 1: 938 MHz 2: 852 MHz
Graphics:  Card: Intel Device 5a85
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@59.97hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 500 (Broxton 2x6)
           version: 4.5 Mesa 18.0.5
Audio:     Card Intel Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-29-generic
Network:   Card-1: Realtek RTL8101/2/6E PCIE Fast/Gigabit Ethernet controller
           driver: r8169
           IF: enp2s0 state: down mac: <filter>
           Card-2: Realtek RTL8821AE 802.11ac PCIe Wireless Network Adapter
           driver: rtl8821ae
           IF: wlp3s0 state: up mac: <filter>
Drives:    HDD Total Size: 1031.1GB (1.0% used)
           ID-1: /dev/sda model: ST1000LM035 size: 1000.2GB
           ID-2: USB /dev/sdb model: DataTraveler_3.0 size: 30.9GB
Partition: ID-1: / size: 1.9G used: 231M (13%) fs: overlay dev: N/A
           ID-2: swap-1 size: 0.99GB used: 0.00GB (0%)
           fs: swap dev: /dev/zram0
           ID-3: swap-2 size: 0.99GB used: 0.00GB (0%)
           fs: swap dev: /dev/zram1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 37.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 145 Uptime: 1:10 Memory: 1806.2/3769.3MB
           Client: Shell (bash) inxi: 2.3.56 
lubuntu@lubuntu:~$ 
```

Any suggestions will be greatly appreciated, just remember I'm new to this so some things my need to be explained in detail, like adding lines to  install, and things like that. Thanks for any help I can get.

---

