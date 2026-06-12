---
title: "Intel HD 4400 4th Gen display issues"
date: 2015-04-02
forum: Installation &amp; Upgrades
---

### Post by gcgamerz on 2015-04-02
Hi Guys,


I have recently upgraded my corporate laptop to a Dell E5440 with the I5-4310U.
The install went without any problems as it always has done.


However, I no find myself in a very strange situation where both monitors that are connected to my docking station are displaying my desktop but only one is being detected in the displays option.
So the problem I have now that my displays are being mirrored without the mirrored option being selected.


I have verified that the display is definitly not showing
========================================
output of ```
xrandr:


Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 32767 x 32767
eDP1 connected (normal left inverted right x axis y axis)
   1366x768       60.0 +   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DP1 connected primary 1600x1200+0+0 (normal left inverted right x axis y axis) 367mm x 275mm
   1600x1200      60.0*+
   3200x1200      60.0  
   2560x1024      60.0  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```
========================================
Output of ```
inxi -Fx


Machine:   System: Dell (portable) product: Latitude E5440 version: 01
           Mobo: Dell model: 0TTRNR version: A00 Bios: Dell version: A06 date: 05/01/2014
CPU:       Dual core Intel Core i5-4310U CPU (-HT-MCP-) cache: 3072 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10376.1 
           Clock Speeds: 1: 754.00 MHz 2: 754.00 MHz 3: 1100.00 MHz 4: 754.00 MHz
Graphics:  Card: Intel Haswell-ULT Integrated Graphics Controller bus-ID: 00:02.0 
           X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1600x1200@60.0hz 
           GLX Renderer: Mesa DRI Intel Haswell Mobile GLX Version: 3.0 Mesa 10.1.3 Direct Rendering: Yes
Audio:     Card-1: Intel Lynx Point-LP HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2: Intel Haswell-ULT HD Audio Controller driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture ver: k3.13.0-37-generic
Network:   Card-1: Intel Ethernet Connection I218-LM driver: e1000e ver: 2.3.2-k port: f080 bus-ID: 00:19.0
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: 34:e6:d7:04:d5:ba
           Card-2: Intel Wireless 7260 driver: iwlwifi ver: in-tree: bus-ID: 02:00.0
           IF: wlan0 state: down mac: 80:19:34:6f:27:a5
Drives:    HDD Total Size: 320.1GB (5.2% used) 1: id: /dev/sda model: TOSHIBA_MQ01ACF0 size: 320.1GB 
Partition: ID: / size: 286G used: 16G (6%) fs: ext4 ID: /boot size: 236M used: 45M (20%) fs: ext2 
           ID: swap-1 size: 8.49GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 25.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 218 Uptime: 34 min Memory: 2499.9/7891.0MB Runlevel: 2 Gcc sys: 4.8.2 Client: Shell inxi: 1.8.4 
```


========================================


I really need some assistance here in trying to figure out why only one display is being detected and why linux mint is mirroring the display if there is only one monitor detected?


--------------------------------------------
Update 1: 


Updated to Linux kernel 3.16.0-30 no Success
Updated to Linux kernel 3.16.0-31 no Success
Updated to Linux kernel 3.16.0-33 no Success


The display is still not being detected as it should be. Also attempted to install the Intel HD package for Ubuntu but even after changing the information about the distro to Ubuntu still getting the error distro not supported when installing.

---

### Post by oldfred on 2015-04-02
Post this:
 sudo lshw | grep -A 11 display

Is this an Ultrabook that also has the nVidia chip?


 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

---

### Post by gcgamerz on 2015-04-02
No not an ultrabook with Nvidia.
Only has the HD4400 gen 4 i5.

I have found a few forum post which state that more people are having issues with the haswell based Intel HD GPU. 

I will post my updates tomorrow.

---

### Post by Vladlenin5000 on 2015-04-02
The docking station's 3 video outputs are actually just one.

---

### Post by gcgamerz on 2015-04-03
Yes I know that but in every other distro the are being detected as seperate monitors and now all of a sudden they are not.

---

### Post by oldfred on 2015-04-03
It is my understanding that there is only one Intel open source driver. There may be development or beta drivers available. Or the very newest may only be in the very newest release of Ubuntu.
And it is not just the Intel driver, but kernel & other support software that must be the very newest versions.
What version of driver did other installs use?

While beta and you may still get breakage or you then are a tester, have you tried the daily 15.04. It will be final by end of April.

---

