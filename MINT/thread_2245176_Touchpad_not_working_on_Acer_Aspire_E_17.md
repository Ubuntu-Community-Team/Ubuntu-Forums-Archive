---
title: "Touchpad not working on Acer Aspire E 17"
date: 2014-09-21
forum: MINT
---

### Post by Olafur_Pall on 2014-09-21
I am totally new to Linux and just bought a new computer with windows 8.1 preinstalled. I wanted to install Linux Mint 17 Cinnamon 64 bit as a dual boot system alongside windows since I didn't like windows 8.1 and want to try Linux. I have now successfully installed Linux Mint Cinnamon and it is working fine except that the touchpad on my laptop is not working. I am using an USB mouse to write this and that works fine. The strange thing is, if I boot into windows 8.1 the touchpad works fine.

I tried running the update manager, downloading all the package files and restarting the system but the touchpad still isn't working. 
I have tried the Fn+F7 function on the keyboard that is supposed to switch the touchpad on and off, that didn't change a thing.
I have opened the "Mouse and Touchpad" settings and the touchpad is set to be enabled.
I have tried downloading and removing one by one several of the touchpad packages listed in the Synaptic Package Manager under "Not Installed" and none of that helped.

Despite what changes I have done this is what always comes up when I run the xinput list command:

mint@mint ~ $ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627;                                             id=11    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Gaming Mouse                   id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HD WebCam                                   id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=14    [slave  keyboard (3)]
mint@mint ~ $ 

As you can see the mouse is detected but nothing on this list indicates to me that the touchpad is detected. 


I have searched the Linux Mint forums and the Unbutu forums for solutions for this problem but have not found any. I have spent days trying to solve this and am about to give up because I suspect my computer is just not compatible with Linux. It's a brand new one. The information is below.

The computer I am using is an Acer Aspire E 17. It has this number on the sticker: E5-721-2474 Here is more info:

mint@mint ~ $ inxi -Fxz
System: Host: mint Kernel: 3.13.0-24-generic x86_64 (64 bit, gcc: 4.8.2)
Desktop: Xfce 4.11.6 (Gtk 2.24.23) Distro: Linux Mint 17 Qiana
Machine: System: Acer product: Aspire E5-721 version: 1
Mobo: Acer model: EA70_BE version: Type2 - A01 Board Version Bios: Insyde version: V1.06 date: 06/05/2014
CPU: Quad core AMD E2-6110 APU with AMD Radeon R2 Graphics (-MCP-) cache: 8192 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 11978.3
Clock Speeds: 1: 1000.00 MHz 2: 1000.00 MHz 3: 1000.00 MHz 4: 1000.00 MHz
Graphics: Card: Advanced Micro Devices [AMD/ATI] Mullins [Radeon APU A4-6000 with R2 Graphics] bus-ID: 00:01.0
X.Org: 1.15.1 drivers: ati (unloaded: vesa,radeon) FAILED: fbdev Resolution: 1600x900@77.0hz
GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits) GLX Version: 2.1 Mesa 10.1.0 Direct Rendering: Yes
Audio: Card-1: Advanced Micro Devices [AMD] FCH Azalia Controller driver: snd_hda_intel bus-ID: 00:14.2
Card-2: Advanced Micro Devices [AMD/ATI] Device 9840 driver: snd_hda_intel bus-ID: 00:01.1
Sound: Advanced Linux Sound Architecture ver: k3.13.0-24-generic
Network: Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
driver: r8169 ver: 2.3LK-NAPI port: 2000 bus-ID: 02:00.0
IF: eth0 state: down mac: <filter>
Card-2: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter driver: ath9k bus-ID: 01:00.0
IF: wlan0 state: up mac: <filter>
Drives: HDD Total Size: 271.6GB (-) 1: id: /dev/sda model: PLEXTOR_PX size: 256.1GB temp: 0C
2: USB id: /dev/sdb model: Silicon size: 15.5GB temp: 0C
Partition: ID: / size: 3.4G used: 57M (2%) fs: overlayfs
RAID: No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors: System Temperatures: cpu: 54.0C mobo: N/A
Fan Speeds (in rpm): cpu: N/A
Info: Processes: 172 Uptime: 43 min Memory: 613.7/6936.9MB Runlevel: 2 Gcc sys: 4.8.2 Client: Shell inxi: 1.8.4
mint@mint ~ $ 

Any help would be appreciated and if you need more info just ask.

---

### Post by dave131 on 2014-09-21
I'm not knowledgeable in this, but you may want to try searching for threads or web threads about adding a touchpad to the xorg configuration files.  I don't if it will want a driver specification there - if it does I don't know what it may be.

EDIT:  Just did some searching on the net and really didn't find anything for the current version of Ubuntu, and since you are using Mint it should be the same.  I went to Acer and to your model (E5-721) but the only OS they show is Windows 8.1.  There isn't a driver listed there for the touchpad.  There are some hits on the net that show replies for older versions of Ubuntu, but I wouldn't have a clue as to whether those apply to the latest version.

---

