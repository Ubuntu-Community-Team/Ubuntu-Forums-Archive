---
title: "ATI Radeon X1650 ubuntu 7.10"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by m.e.danko on 2007-11-27
Hello all, I've just managed to convince a friend of mine to dual boot his computer and to start using ubuntu with compiz etc.. he'd also like to play windows games using Cedega, wine etc... but I am having some really weird things happen when I try to boot ubuntu 7.10.

The problem being, I cannot manage to get the display working, no matter what I try. He has a ATI Sapphire X1650 PCI-Express graphics card and when I boot ubuntu, the screen keeps flickering and displaying weird old school type pattens, then eventually a message appears and says there was a problem with the graphics and it starts in like a safe mode (bullet proof X) or something, and we're left with a crappy 800x600 display using the VESA driver. - Now no one is going to manage to use compiz with that.

I tried installing the fglrx driver by enabling it through the restricted driver utility and when the computer reboots, no display at all, but can get a command prompt. 

I also tried installing the official ATI graphics driver, same problem as described above.

The last thing i tried was to install the driver through envy, and again same problem.

Any help would be really greatly appreciated, many thanks Martin. BTW I have tried searching the forums and googling the problems, but no one it seems is have the same type of problems.

---

### Post by Supreme1012 on 2007-11-27
Im having the same problem. 

My system

GIGABYTE GA-MA69GM-S2H AM2 AMD 690G HDMI Micro ATX AMD Motherboard
[http://www.newegg.com/Product/Product.asp?Item=N82E16813128056](http://www.newegg.com/Product/Product.asp?Item=N82E16813128056)

AMD Athlon 64 X2 4600+ Windsor 2.4GHz 2 x 512KB L2 Cache Socket AM2 65W Processor
[http://www.newegg.com/Product/Product.asp?Item=N82E16819103749](http://www.newegg.com/Product/Product.asp?Item=N82E16819103749)

G.SKILL 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory
[http://www.newegg.com/product/product.asp?item=N82E16820231098](http://www.newegg.com/product/product.asp?item=N82E16820231098)

Western Digital Caviar SE WD1600AAJS 160GB 7200 RPM 8MB Cache SATA 3.0Gb/s Hard Drive
[http://www.newegg.com/Product/Product.asp?Item=N82E16822136075](http://www.newegg.com/Product/Product.asp?Item=N82E16822136075)

And Im using my old Emachines Desktop Monitor from my old computer.

Ive been running Ubuntu 7.10 64 bit fine for over a month but recently, within the past week, the graphics driver for fglrx has not been working at all. My previous install it would start but then get stuck at "Loading Local Boot Script (/blah/blah).." it would flash that screen several times and then show a window about graphics being wrong and an option to "configure graphics" or "Continue". But even if I configure the graphics to use the Radeon Fglrx driver that had worked previously, it would say to restart and show the graphics as VESA with maximum resolution of 800x600. I can find no way to get my ATI Radeon x1250 integrated graphics to work.

I did a fresh reinstall to fix the problem if it was something that I had done by accidentally configuring something, but after activating the Graphics Card in the Restricted Drivers Manager and restarting, it showed the same VESA driver and 800x600 resolution being defaulted. I cant use Ubuntu like this, and I need to know how to fix the problem or Ill have to switch back to windows.

---

### Post by Pumalite on 2007-11-27
Update package list and upgrade any packages needed
sudo apt-get update
sudo apt-get dist-upgrade
Install fglrx closed source driver for ATI video cards.
sudo apt-get install xorg-driver-fglrx
Update loaded modules.
sudo depmod -a
Configure /etc/X11/xorg.conf
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Reboot

---

### Post by Supreme1012 on 2007-11-27
ok Im getting errors while doing that.

sudo apt-get update
sudo apt-get dist-upgrade
```
Removed:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Get:1 http://archive.canonical.com gutsy Release.gpg [191B]                                     
Ign http://archive.canonical.com gutsy/partner Translation-en_US            
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US               
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US        
Hit http://archive.canonical.com gutsy Release 
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]  
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US       
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com gutsy-security Release                
Ign http://archive.canonical.com gutsy/partner Packages              
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release 
Hit http://us.archive.ubuntu.com gutsy-updates Release                                    
Hit http://security.ubuntu.com gutsy-security/main Packages                               
Hit http://archive.canonical.com gutsy/partner Packages                                   
Hit http://us.archive.ubuntu.com gutsy/main Packages                 
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Packages
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 4B in 2s (2B/s)  
Reading package lists... Done
Removed:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

sudo apt-get install xorg-driver-fglrx
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

didnt show anything after typing it in
```
Removed:~$ sudo depmod -a
```

```
Removed:~$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.
```

```
Removed:~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0x00007fffd0b729a8 ***
======= Backtrace: =========
/lib/libc.so.6(cfree+0x1b6)[0x2af5dad7d826]
aticonfig[0x4148ed]
aticonfig[0x414849]
aticonfig[0x40c6e5]
aticonfig(XOpenDisplay+0x2bd)[0x402485]
aticonfig(XOpenDisplay+0x141)[0x402309]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2af5dad25b44]
aticonfig(XOpenDisplay+0x62)[0x40222a]
======= Memory map: ========
00400000-00420000 r-xp 00000000 08:01 2851272                            /usr/bin/aticonfig
00520000-00526000 rw-p 00020000 08:01 2851272                            /usr/bin/aticonfig
00526000-00547000 rw-p 00526000 00:00 0                                  [heap]
2af5d9f36000-2af5d9f53000 r-xp 00000000 08:01 7258124                    /lib/ld-2.6.1.so
2af5d9f53000-2af5d9f57000 rw-p 2af5d9f53000 00:00 0 
2af5da152000-2af5da154000 rw-p 0001c000 08:01 7258124                    /lib/ld-2.6.1.so
2af5da154000-2af5da15b000 r-xp 00000000 08:01 2852167                    /usr/lib/libXrandr.so.2.1.0
2af5da15b000-2af5da35a000 ---p 00007000 08:01 2852167                    /usr/lib/libXrandr.so.2.1.0
2af5da35a000-2af5da35b000 rw-p 00006000 08:01 2852167                    /usr/lib/libXrandr.so.2.1.0
2af5da35b000-2af5da364000 r-xp 00000000 08:01 2852169                    /usr/lib/libXrender.so.1.3.0
2af5da364000-2af5da563000 ---p 00009000 08:01 2852169                    /usr/lib/libXrender.so.1.3.0
2af5da563000-2af5da564000 rw-p 00008000 08:01 2852169                    /usr/lib/libXrender.so.1.3.0
2af5da564000-2af5da575000 r-xp 00000000 08:01 2852147                    /usr/lib/libXext.so.6.4.0
2af5da575000-2af5da774000 ---p 00011000 08:01 2852147                    /usr/lib/libXext.so.6.4.0
2af5da774000-2af5da775000 rw-p 00010000 08:01 2852147                    /usr/lib/libXext.so.6.4.0
2af5da775000-2af5da87f000 r-xp 00000000 08:01 2852126                    /usr/lib/libX11.so.6.2.0
2af5da87f000-2af5daa7f000 ---p 0010a000 08:01 2852126                    /usr/lib/libX11.so.6.2.0
2af5daa7f000-2af5daa86000 rw-p 0010a000 08:01 2852126                    /usr/lib/libX11.so.6.2.0
2af5daa86000-2af5daa87000 rw-p 2af5daa86000 00:00 0 
2af5daa87000-2af5dab07000 r-xp 00000000 08:01 7258701                    /lib/libm-2.6.1.so
2af5dab07000-2af5dad06000 ---p 00080000 08:01 7258701                    /lib/libm-2.6.1.so
2af5dad06000-2af5dad08000 rw-p 0007f000 08:01 7258701                    /lib/libm-2.6.1.so
2af5dad08000-2af5dae5a000 r-xp 00000000 08:01 7258624                    /lib/libc-2.6.1.so
2af5dae5a000-2af5db059000 ---p 00152000 08:01 7258624                    /lib/libc-2.6.1.so
2af5db059000-2af5db05c000 r--p 00151000 08:01 7258624                    /lib/libc-2.6.1.so
2af5db05c000-2af5db05e000 rw-p 00154000 08:01 7258624                    /lib/libc-2.6.1.so
2af5db05e000-2af5db063000 rw-p 2af5db05e000 00:00 0 
2af5db063000-2af5db065000 r-xp 00000000 08:01 2852132                    /usr/lib/libXau.so.6.0.0
2af5db065000-2af5db264000 ---p 00002000 08:01 2852132                    /usr/lib/libXau.so.6.0.0
2af5db264000-2af5db265000 rw-p 00001000 08:01 2852132                    /usr/lib/libXau.so.6.0.0
2af5db265000-2af5db266000 rw-p 2af5db265000 00:00 0 
2af5db266000-2af5db26b000 r-xp 00000000 08:01 2852143                    /usr/lib/libXdmcp.so.6.0.0
2af5db26b000-2af5db46a000 ---p 00005000 08:01 2852143                    /usr/lib/libXdmcp.so.6.0.0
2af5db46a000-2af5db46b000 rw-p 00004000 08:01 2852143                    /usr/lib/libXdmcp.so.6.0.0
2af5db46b000-2af5db46d000 r-xp 00000000 08:01 7258627                    /lib/libdl-2.6.1.so
2af5db46d000-2af5db66d000 ---p 00002000 08:01 7258627                    /lib/libdl-2.6.1.so
2af5db66d000-2af5db66f000 rw-p 00002000 08:01 7258627                    /lib/libdl-2.6.1.so
2af5db66f000-2af5db671000 rw-p 2af5db66f000 00:00 0 
2af5db671000-2af5db67e000 r-xp 00000000 08:01 7258178                    /lib/libgcc_s.so.1
2af5db67e000-2af5db87e000 ---p 0000d000 08:01 7258178                    /lib/libgcc_s.so.1
2af5db87e000-2af5db87f000 rw-p 0000d000 08:01 7258178                    /lib/libgcc_s.so.1
7fffd0b5e000-7fffd0b74000 rw-p 7fffd0b5e000 00:00 0                      [stack]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]
Aborted (core dumped)
```

---

### Post by Supreme1012 on 2007-11-27
After rebooting it appears to work well, the resolution is fixed at least, thanks for the help.

EDIT: 

Restricted Drivers Manager:
It shows the ATI accelerated graphics driver as not in use.

Screens and Graphics:
It shows Screen 1
Model: unknown
Resolution: 640x480 at 60 Hz

Graphics Card
VESA Generic VESA-Compliant Video cards

---

