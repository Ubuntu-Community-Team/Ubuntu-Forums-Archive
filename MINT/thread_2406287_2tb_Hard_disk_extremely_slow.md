---
title: "2tb Hard disk extremely slow"
date: 2018-11-18
forum: MINT
---

### Post by tackskull on 2018-11-18
Hi there, I am using an external 2tb hard disk drive and untill a month ago to write files on it was fast, but at a certain point the hard disk  become very slow, like to copy a file of 3gb require hours to complete. I am not understanding what's the problem, can you guys help me to fix my hard disk?

Edit: I tried to use my hard disk on another pc and is very fast, looks like it get slow only on this pc where I am using linux mint. On the other two laptops (one running ubuntu and the other running manjaro) is everything ok. Can you help me understand why this linux  mint pc  make my hard disk slow and how to solve it?

---

### Post by 23dornot23d on 2018-11-18
Seems to me from your description - that the hard disk itself is not the problem - if it is working on two other systems ok.

Is the linux mint pc a older pc ...............

Not sure if you can run this on it ..... but no harm in trying to get some more information as people will need it later on to work
out what is happening.

[B]$ sudo apt install inxi

$ inxi -F[/B]

Post back the information ...... from the Linux Mint PC ........ see what processor etc and memory it has .......

Quite possible that its a older machine .... but who knows.

---

### Post by angisky on 2018-11-18
To add to what the previous user said you can also try opening system monitor while doing the file transfer and viewing what resources are being used. For example if it's an old PC you'll likely see the CPU and even ram be completely consumed during the transfer process. If you see that neither of those things happen then it might be some bottle neck going on somewhere else in the system. 

A good question would also be whether this is an external drive being used through USB or if it's an internal drive using SATA. USB can be bottle necked by other devices that are plugged into the same bus as with USB every connection has to be processed by the same bus causing multiple devices to interfere with each other.

---

### Post by tackskull on 2018-11-19
Thanks guys for reply.

My pc is quite recent and it have 2 usb holes. In one I have insert my wireless mouse and to the other one there is the 2tb external hard disk drive. The laptop has a bluetooth game controller connected, the ethernet cable for the internet and the hdmi cable for the tv as well.

```
$ inxi -F
System:    Host: tackskull-Lenovo-ideapad-320-15ABR Kernel: 4.15.0-39-generic x86_64
           bits: 64
           Desktop: Cinnamon 3.8.9  Distro: Linux Mint 19 Tara
Machine:   Device: laptop System: LENOVO product: 80XS v: Lenovo ideapad 320-15ABR serial: N/A
           Mobo: LENOVO model: LNVNB161216 v: SDK0J40709WIN serial: N/A
           UEFI: LENOVO v: 5QCN18WW date: 07/13/2017
Battery    BAT0: charge: 26.4 Wh 98.1% condition: 26.9/30.0 Wh (90%)
CPU:       Quad core AMD A10-9620P RADEON R5 10 COMPUTE CORES 4C+6G (-MCP-) 
           cache: 4096 KB
           clock speeds: max: 2500 MHz 1: 1343 MHz 2: 1367 MHz 3: 1284 MHz
           4: 1283 MHz
Graphics:  Card-1: Advanced Micro Devices [AMD/ATI] Carrizo
           Card-2: Advanced Micro Devices [AMD/ATI] Topaz XT [Radeon R7 M260/M265 / M340/M360 / M440/M445]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: ati,amdgpu (unloaded: modesetting,fbdev,vesa,radeon)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: AMD CARRIZO (DRM 3.23.0 / 4.15.0-39-generic, LLVM 6.0.0)
           version: 4.5 Mesa 18.0.5
Audio:     Card-1 Advanced Micro Devices [AMD] Device 157a
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] Kabini HDMI/DP Audio
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-39-generic
Network:   Card-1: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter
           driver: ath10k_pci
           IF: wlp1s0 state: down mac: e8:2a:44:fd:b2:c7
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp2s0 state: up speed: 100 Mbps duplex: full
           mac: 54:e1:ad:f8:dc:39
           Card-3: Atheros
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 3000.6GB (53.0% used)
           ID-1: USB /dev/sda model: M3 size: 2000.4GB
           ID-2: /dev/sdb model: WDC_WD10SPZX size: 1000.2GB
Partition: ID-1: / size: 916G used: 575G (67%) fs: ext4 dev: /dev/sdb2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 0.0C mobo: N/A gpu: 42.0,N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 228 Uptime: 2:39 Memory: 2203.0/7424.9MB
           Client: Shell (bash) inxi: 2.3.56 
 
```

---

### Post by 23dornot23d on 2018-11-19
What boot mode are you using ........... Rapid ? if so that could be a problem.

The other thing I read about was power saving in BIOS ........ - that also can effect the USB apparently ........

They are the two things I spotted while having a look around the Lenovo problems already found on USB's
Although there are lots of other posts complaining about the speed of the model you have ......
Lenovo-ideapad-320-15ABR
[https://forums.lenovo.com/t5/Lenovo-IdeaPad-1xx-3xx-5xx-7xx/New-Ideapad-320-really-slow/td-p/3763971](https://forums.lenovo.com/t5/Lenovo-IdeaPad-1xx-3xx-5xx-7xx/New-Ideapad-320-really-slow/td-p/3763971)

---

### Post by deadflowr on 2018-11-19
*Thread moved to **MINT***

---

### Post by tackskull on 2018-11-20
What do you mean with rapid boot? On the power management I don't have any option activated, the pc is in full work

---

### Post by 23dornot23d on 2018-11-20
The options are in the BIOS ....... Basic Input Output System ...... 

I believe you have to press Fn2 ( Function key 2 ) at boot up to see the settings ........

On looking for the USB 3.0 ...... which could increase transfer rates - there is one sceen shot  I will show - but if you are not used to doing things in the BIOS
it may be better to ask or wait from more help from someone that knows more about your Lenovo Laptop on the Lenovo site [https://forums.lenovo.com/t5/Lenovo-IdeaPad-1xx-3xx-5xx-7xx/LENOVO-IDEAPAD-320-15IKB-81BT-USB-3-0-PORT/td-p/4124630](https://forums.lenovo.com/t5/Lenovo-IdeaPad-1xx-3xx-5xx-7xx/LENOVO-IDEAPAD-320-15IKB-81BT-USB-3-0-PORT/td-p/4124630)

I have been searching around for possible problems ...... and the ones I gave initially are on the Lenovo site .....  you could ask there - as the Ubuntu Forum probably
is not going to help you that much with it being MINT you are using for no 1 and the problem you are encountering - which may be just something to do with the
BIOS setup on that one machine - as you said previously it works fine on 2 other machines.

[IMG]https://s14-eu5.startpage.com/cgi-bin/serveimage?url=https:%2F%2Fmsdnshared.blob.core.windows.net%2Fmedia%2FMSDNBlogsFS%2Fprod.evol.blogs.msdn.com%2FCommunityServer.Blogs.Components.WeblogFiles%2F00%2F00%2F01%2F29%2F62%2F5684.Picture2.jpg&sp=f6d92ed18ac780c16eb315805ee027c0[/IMG]

---

### Post by tackskull on 2018-11-24
I solved the problem. First I diabled fast boot but the hard disk still was slow, then I tried to poot the hard disk on the other usb hole (the one closest to the hdmi) and the hard disk is running so fast like I never seen on this pc. So I imagine that both  the solution togheter can solve the problem. Thank you guys

---

### Post by 23dornot23d on 2018-11-24
Nice to know you sorted it ......... great work ........ :popcorn:

---

### Post by tackskull on 2018-11-25
Is slow again. After I pooted an sd card on the pc to transfer a couple of file, the pc started to read very slow. I tried to turn off the pc many times, to change usb hole, but nothing. I don't know if the slow usb reading it happened again after I used the sd card or if I was just lucky for a little time to have fast reading again. I don't really know what I can do

---

### Post by 23dornot23d on 2018-11-25
Is the BIOS retaining its settings ........... sometimes the backup battery fails ..... and the BIOS will keep going to
default values ......

Its the only other thing I can think of at the moment - seeing its worked ok once at least ........ something's changed !!!

USB3 .......... and the drive is not going into Windows then into Ubuntu without it being safely removed or unmounted
as windows sometimes seems to lock them up - but not as far as I know slow them down. ( but that is the only other thing that comes to mind.)

You might have to try again with the stop Rapid boot ...... if its changed back ........ also is it using the USB3 as a USB3 in the BIOS

> 
First I disabled fast boot but the hard disk still was slow, then I tried  to boot the hard disk on the other usb slot (the one closest to the  hdmi) and the hard disk is running so fast


Maybe also could be a problem with other usb devices plugged in at the same time .......... maybe a conflict .......... try with only the usb drive plugged in ...........
or go through your usb devices one at a time to see if any difference in performance.

Checking your log files /var/log/system.log ... xorg.log   etc ...... maybe one will give a clue to what is happening ........ if there is a conflict somewhere ......

---

### Post by MoebusNet on 2018-11-28
Looking at your question, it is not clear to me what speed USB you are using. Is your external HDD capable of USB3? Is your problematic notebook equipped with USB3? USB3 is much, much faster than USB2. You might not notice the difference on small files, but I can assure you that it makes a huge difference on large files. If your are not sure what you have on your notebook: ```
lsusb
```should tell you whether you have USB2 only on your notebook or USB3 available which will work with USB2 & USB1 devices also

---

### Post by tackskull on 2018-11-30
```
 tackskull@tackskull-Lenovo-ideapad-320-15ABR:~$ lsusb
Bus 001 Device 004: ID 13d3:5a02 IMC Networks 
Bus 001 Device 003: ID 0cf3:e500 Atheros Communications, Inc. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0bc2:61b5 Seagate RSS LLC 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 145f:01c8 Trust 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
```

---

### Post by tackskull on 2018-11-30
Getting deeper to the problem I have noticed (i wasn't caring so much before) is that when I put the external hard disk on the pc I get this error:[https://www.dropbox.com/s/r01yd3mv2mqevgj/20181130_163323.jpg?dl=0](https://www.dropbox.com/s/r01yd3mv2mqevgj/20181130_163323.jpg?dl=0)

Then I can see that the pc is seeing not one hard disk (like it should) but two of them: [https://www.dropbox.com/s/oht7hnojp6x7vyf/20181130_163340.jpg?dl=0](https://www.dropbox.com/s/oht7hnojp6x7vyf/20181130_163340.jpg?dl=0)

So I tried some stuff: If I unmount the lower one automatically the upper get mounted and If i put files on it, the transer is very fast. But otherwise if I start an application (in this case retroarch to play the roms from the hard disk) it doesn't read the storage, like is unmounted. 

So very strange stuff and uncommon..... do you understand why my pc is acting like this?

---

### Post by coffeecat on 2018-11-30
Your first screenshot shows a message telling you that sda1 is already mounted on /media/usb0. This is a default mountpoint that the app usbmount uses.

[https://wiki.debian.org/usbmount](https://wiki.debian.org/usbmount)

Do you have usbmount installed and, if so, why? I'm a bit out of date with this, but it used to be that usbmount broke automounting in GUI versions of Ubuntu, and presumably Mint too. It was really designed for server systems without a GUI. 

If you have usbmount installed, I suggest you uninstall it. There is no need for it if you have a desktop environment. I have no idea whether usbmount would explain the problem you describe, but you would be better off without it.

---

### Post by MoebusNet on 2018-11-30
@tackskull, just for basic information you can usually physically tell USB2 from USB3  by looking into the slot. USB3 typically has a blue plastic tab inside, USB2 typically has a white plastic tab inside. You want your external HDD to be plugged into USB3 for speed; stuff like USB keyboards and mice will work just as well on USB2 ports, since they don't use much data by design.

---

### Post by tackskull on 2018-11-30
Is installed by default on mint but now I'll try to unistall it and I let you guys know

---

### Post by tackskull on 2018-11-30
> **MoebusNet said:**
> @tackskull, just for basic information you can usually physically tell USB2 from USB3  by looking into the slot. USB3 typically has a blue plastic tab inside, USB2 typically has a white plastic tab inside. You want your external HDD to be plugged into USB3 for speed; stuff like USB keyboards and mice will work just as well on USB2 ports, since they don't use much data by design.


Yes, my hard disk have blue plastic inside so it should be usb3, I should try back fast boot. 

Anyway I tried unistal usbmount, I don't get any error but hard disk is still slow and plus is not readed by retroarch, so I installed it back

---

### Post by MoebusNet on 2018-11-30
> Yes, my hard disk have blue plastic inside so it should be usb3 But is your USB cable plugged into USB3 on your notebook? Both ends of the cable must be plugged into USB3 to get USB3 speed.

---

### Post by tackskull on 2018-12-02
> **MoebusNet said:**
> But is your USB cable plugged into USB3 on your notebook? Both ends of the cable must be plugged into USB3 to get USB3 speed.

This laptop have only two usb holes and I tried both of them many times. This pc have some usb problem and I can't understand what is.

---

### Post by MoebusNet on 2018-12-08
I looked up your notebook model specifications: >  Ports and connectivity

    2x USB Type-A 3.0 (3.1 Gen 1)
    1x USB Type-C 3.0 (3.1 Gen 1) 

Since you have USB3 only, my theory that it was a USB2-caused slowdown seems to not apply. Maybe someone else will have an idea.

---

### Post by MoebusNet on 2018-12-08
I just had a thought; the 2 USB Type-A ports share the same controller. If they are both in use at the same time (plugged-in) that may very well reduce the speed available. Perhaps you should try the USB Type-C port, even if you need an adapter. It should have its own dedicated controller which won't share its speed with anything else. Just an idea!

---

### Post by tackskull on 2018-12-11
Yes I have noticed that usb c, I'll follow your advice buying a usb c adaptor and I will see, good idea thanks :) 

I'll let you guys know

---

