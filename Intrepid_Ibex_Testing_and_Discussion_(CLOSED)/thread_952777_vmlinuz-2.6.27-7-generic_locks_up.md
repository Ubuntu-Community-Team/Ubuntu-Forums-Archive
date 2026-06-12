---
title: "vmlinuz-2.6.27-7-generic locks up"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by 0xdeadc0de on 2008-10-19
I appologize if this has been reported already. 
For the curious: The caps lock light does _not_ flash when it locks up.

the title explains it all.. well, okay, no it doesn't.

I can't figure out why, I have troubles with the uvcvideo driver generating a lot of 135 errors on my integrated webcam, so I blacklisted the driver and no more errors pop up in dmesg

But it still locks up - it takes only a few minutes and doesn't seem to matter whether the system is under load or not.

I used to get lockups before 8.04 - due to the c1e bug - which is now fixed. The way to get around those lockups was to use noapic, so I tried that here.. doesn't fix a damn thing. Tried pci=routeirq (due to some forums post that suggested it...) , still locks up.

I'm using intrepid now with vmlinuz-2.6.24-21-generic and it all works.

It's not due to overheating - I watch the sensors they remain WELL within tolerance levels.

It almost always seems to happen while something is interrupting however - a mouse movement, when I type something.

It doesn't lock up immediately, that's the funny thing, it takes about a full second to lock-up.. What I mean by this is the system comes to a slow hault. Example: Last time I was reading dmesg to see if any messages popped up worth interest, nothing. I typed dmesg again after finishing reading line by line the entire damn thing (about 3-5 minutes), I saw it type in dmesg much more slowly than I had typed it, then took a a second to register the newline, then froze without outputting anything (In other words it started to lag behind my keypresses before it locked up)

System background:
HP Dv9010US Laptop

Ran 8.04 since it came out, ran update-manager -d last night to upgrade to 8.10

Specifications (lspci, lsusb):
```

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)        
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) 
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) 
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)




USB:

Bus 002 Device 002: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 001: ID 0000:0000

```

Startup Programs:
```


deadc0de@deadc0de-laptop:~$ ls /etc/rc5.d/
K08vmware                    S11klogd          S20apport              S20nvidia-kernel               S20winbind           S25pulseaudio             S91apache2
README                       S12dbus           S20cpufreqd            S20nvtv                        S20xttpd             S28NetworkManager         S98usplash
S01lokkit                    S14avahi-daemon   S20cpufrequtils        S20powernowd                   S20yate              S30gdm                    S99acpi-support
S01policykit                 S16ssh            S20cups                S20rsync                       S24dhcdbd            S30system-tools-backends  S99laptop-mode
S05loadcpufreq               S17mysql-ndb-mgm  S20dkms_autoinstaller  S20speech-dispatcher           S24hal               S89anacron                S99rc.local
S05vbesave                   S18mysql-ndb      S20gdomap              S20vboxdrv                     S25bluetooth         S89atd                    S99rmnologin
S10acpid                     S19autofs         S20hotkey-setup        S20vboxnet                     S25landscape-client  S89cron
S10sysklogd                  S19mysql          S20kvm                 S20virtualbox-ose              S25mdadm             S90binfmt-support
S10xserver-xorg-input-wacom  S20apmd           S20nullmailer          S20virtualbox-ose-guest-utils  S25powersaved        S90vmware

```


Other drivers:
Nvidia binary driver 177.80
Ndiswrapper and a broadcom bcm4413 windows driver




The update went fairly smooth although it ran into problems with menu.lst and I ended up copying the new entires from the maintainers copy over to the existing menu.lst and keeping it when updating the kernel, said it failed, but then it seemed to work anyway..

I'd post lsmod too, but I'm running in the old kernel so I can't really..


Also - side note - network manager seems to like to get stuck on "Requesting network address from SSID", then disconnect, then try again. It usually helps to just right click on it, disable wireless, do it again to enable wireless, then it usually connects to my AP.

Other than the lockups with the latest kernel, I like it.

---

### Post by 0xdeadc0de on 2008-10-20
More information! It's not a kernel panic causing this. I booted up to the newest kernel, went to a console instead of xorg, and sat and watched it for 5 minutes or so and I get:

Bug: Soft Lock - Cpu#0 stuck for 61s! [11179]
Bug: Soft Lock - Cpu#0 stuck for 61s! [11179]
 every 61 seconds..

Also - when it soft locks in xorg the keyboard won't respond at all, when in the terminal I can still turn the caps light on and off - and before it locked up I was still able to partially type things in but when I hit enter it would beep at me, then I hit delete it would delete 5 charactors instead of one, just really odd behavior. I was able to use up/down arrows to go through the command history but couldn't hit enter launch any command, then after a few moments the arrow keys stopped working too and all I could do was watch the message pop up and hit the caps key to turn on/off the light. Control+alt+delete didn't reboot, forced it off. Didn't try sysreq magic.


now I'm using 2.6.24-21-generic, and it works fine.

I see other people are having this problem as well - thanks to google, I'm glad I'm not the only one. I havn't seen any suggested solutions yet - and the incarnation of the version of this bug I've found applies to intel chipsets: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/214814](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/214814) 
all mine are nvidia/amd :|

Any suggestions other than wait for the next kernel release? Options I could try?

---

### Post by 0xdeadc0de on 2008-10-20
:lolflag::guitar:

[https://bugs.launchpad.net/ubuntu/+bug/286371](https://bugs.launchpad.net/ubuntu/+bug/286371)

Well, not completely, I can't clear my cache out to keep performance up and power waste down.. But it no longer soft-locks.

---

