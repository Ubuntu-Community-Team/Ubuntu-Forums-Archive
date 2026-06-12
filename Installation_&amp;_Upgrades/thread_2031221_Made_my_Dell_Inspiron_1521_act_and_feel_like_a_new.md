---
title: "Made my Dell Inspiron 1521 act and feel like a new computer."
date: 2012-07-21
forum: Installation &amp; Upgrades
---

### Post by irv on 2012-07-21
Made my Dell Inspiron 1521 act and feel like a new computer.

These are the steps I took to do this:
Step #1: Started out by backing up all my data files and making a list of all installed Apps.
Step #2: Downloaded Ubuntu 12.04 64 bit.
Step #3: Ran Unetbooin and made a bootable USB stick.
Step #4: Just got a new 180gig SSD so I installed in the laptop
Step #5: I plug in a Network cable into the laptop because Ubuntu 12.04 does not see my Broadcom 4311 card on install.
Step #6: Booted from the newly created USB stick and installed OS.
Step #7: After it is done you need to restart the computer and remove the USB stick. After rebooted I did all the updates. 
Step #8: Now here is the tricky part. Getting the wifi working. Do not load drivers with “Additional Drivers” utilities.   Follow these steps.
	> Step #1:  Make sure you have “dkms” installed by typing this command in a terminal:
	```
sudo apt-get install dkms
``` 
	Step #2:  uninstall “bcmwl-kernel-source”
	```
sudo apt-get  remove bcmwl-kernel-source
```
	Step #3:  Install “firmware-b43-installer” package
	```
sudo apt-get install firmware-b43-installer
```
	Step #4: Install “b43-fwcutter” package
	```
sudo apt-get install b43-fwcutter
```
	Step #5: Type in a terminal
 	```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|	orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```

	This was the out put:
	
	[QUOTE]blacklist ath_pci
	blacklist eth1394
	# replaced by p54pci
	blacklist prism54
	# replaced by b43 and ssb.
	blacklist bcm43xx
	blacklist uart6850
	blacklist twl4030_wdt
[/QUOTE]
Step #9 At this point you need to unplug the network cable and restart. After the boot is complete select the wireless connection that is available from the network icon in the top right corner of the desktop.
Step #10: Reinstall all your backup files and reinstall all your apps.

From the old to the new:
The Old setup: 500 gig SATA HD with 3 OS's. 
The New setup: 180 gig SSD with 1 OS.
Boot time: Old, over a minute. New, 20 seconds.
The Old took several seconds to open apps, the New, they open instantly.
Just for the record this speed up on this older laptop only cost me $149 for the new 180 gig SSD. plus a few hours of my time.

---

