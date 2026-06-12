---
title: "configure onboard video: Gigabyte 890GPA-UD3H"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by sbin on 2011-01-28
I just replaced my motherboard with a Gigabyte 890GPA-UD3H. I am happy to report that the OS (Ubuntu 10.04) was smart enough to boot up using the pre-existing software RAID 5 (four disks) and work fine with the new motherboard, CPU, and memory. However, since the new motherboard has a nice onboard display, I removed the PCIe graphics card (which was needed on the old board), and am now trying to configure the OS to use the "OnChipVGA."

This is what lshw produces:
[INDENT]*-display
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:d0000000-dfffffff(prefetchable) ioport:ee00(size=256) memory:fdee0000-fdeeffff memory:fdd00000-fddfffff
[/INDENT]

And here is what I get with startx:
[INDENT]X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux tall 2.6.32-27-server #49-Ubuntu SMP Thu Dec 2 02:05:21 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-27-server root=UUID=f0de34e0-25b0-4631-b764-26f38f16caaa ro
Build Date: 10 November 2010  11:25:53AM
xorg-server 2:1.7.6-2ubuntu7.4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 28 10:46:39 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
WARNING: All config files need .conf: /etc/modprobe.d/bttv, it will be ignored in a future release.
FATAL: Module nvidia not found.
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
[/INDENT]

Any suggestions will be appreciated.

---

### Post by wormyblackburny on 2011-01-28
Try running: 
sudo dpkg-reconfigure xserver-xorg

---

### Post by gordintoronto on 2011-01-28
What was the previous video card? Before you removed it, did you remove its driver? The specs for your motherboard say it has an on-board ATI Radeon HD 4290.

You haven't actually said what the problem is.

---

### Post by sbin on 2011-01-28
I tried the command "dpkg-reconfigure xserver-xorg," as root, and rebooted. However, the display is not served graphically.

The machine will boot up with a graphical interface when the old GeForce 7300GS card is installed in the new motherboard. But I wish to use the onboard graphics chip. I have not removed the old driver, nor have I installed a new one. My guess is that I must install a new driver and kernel module, but I don't even know where to begin that process. I would imagine that the onboard display would be automatically detected and configured for a GUI on a fresh install, but I really don't wish to bother with that.

---

### Post by PRC09 on 2011-01-28
You can try putting the old card back in and reboot.Then go to System > Admin > Additional drivers and de-activate the existing drivers and then shut-down.Remove the old card and re-start again.Then check for new drivers for your onboard video and see if there are any and if so then activate.....

---

### Post by sbin on 2011-01-29
The BIOS on this system is a bit unusual in that it has a setting to choose whether the video will be delivered via the onboard display or the PCI bus. When it is set to the onboard chip, the result is that the linux kernel only sees that display, as evidenced by my original posting of the output from lshw. With the BIOS set to the PCI bus, the command "lshw" provides this:

[INDENT]*-display
                description: VGA compatible controller
                product: G71 [GeForce 7300 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff(prefetchable) memory:fb000000-fbffffff memory:fc000000-fc01ffff(prefetchable)
[/INDENT]

Thus I believe that the kernel is only aware of one display even when both are physically present. Because of this situation, I don't believe that the GUI tools will work to configure the onboard display, because the proper driver must be associated with the correct hardware.

---

### Post by PRC09 on 2011-01-29
?????  I think the problem is if you dont remove the drivers for the old card first they remain installed and active.When Ubuntu boots it is still trying to and obviously succeeding at booting with the installed driver and is ignoring the onboard settings.Did you try de-activating the Ge-Force.....

---

### Post by sbin on 2011-01-29
Success! I was able to solve the problem through the following steps:
[LIST=1]
[*]Install Nvidia proprietary video driver
[*]Uninstall Nvidia driver
[*]Switch BIOS selection to onboard display
[*]Remove PCIe graphics card and connect VGA cable to onboard display
[*]Reboot
[/LIST]
Thank you all for your help. Ubuntu is awesome.:guitar:

---

