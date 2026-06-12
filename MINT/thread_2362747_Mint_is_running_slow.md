---
title: "Mint is running slow"
date: 2017-06-01
forum: MINT
---

### Post by omrthaq on 2017-06-01
Hello,

Yesterday I install Mint and Windows in a dualboot.
I wanted to test mint so i use it currently.
But the thing is that Mint is lagging so much when i use it.
CSGO (Counter-Strike) is running with 1 < FPS.
On windows CSGO has 300 > FPS.
What can i do?

Omrtha

---

### Post by Bucky Ball on 2017-06-01
Have you installed a driver for your graphics card? You may need to. Please open a terminal and post the output of this command (between code tags, please ... see the green link in my signature for how).

```
sudo lshw -C video
```

That will give us a quick look at what you've got and the driver currently being used.

---

### Post by omrthaq on 2017-06-01
Its german sorry for that

```
  *-display               
       Beschreibung: VGA compatible controller
       Produkt: Hawaii PRO [Radeon R9 290]
       Hersteller: Advanced Micro Devices, Inc. [AMD/ATI]
       Physische ID: 0
       Bus-Informationen: pci@0000:01:00.0
       Version: 00
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm pciexpress msi vga_controller bus_master cap_list rom
       Konfiguration: driver=radeon latency=0
       Ressourcen: irq:123 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:e000(Größe=256) memory:f7e00000-f7e3ffff memory:f7e40000-f7e5ffff
```

---

### Post by ajgreeny on 2017-06-01
What driver are you using?
Show us the output from terminal command ```
lspci -k
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by omrthaq on 2017-06-01
```
00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)
        Subsystem: ASUSTeK Computer Inc. Skylake Host Bridge/DRAM Registers
00:01.0 PCI bridge: Intel Corporation Sky Lake PCIe Controller (x16) (rev 07)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
        Subsystem: ASUSTeK Computer Inc. Sunrise Point-H USB 3.0 xHCI Controller
        Kernel driver in use: xhci_hcd
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
        Subsystem: ASUSTeK Computer Inc. Sunrise Point-H CSME HECI
        Kernel driver in use: mei_me
        Kernel modules: mei_me
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #9 (rev f1)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
        Subsystem: ASUSTeK Computer Inc. Sunrise Point-H LPC Controller
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
        Subsystem: ASUSTeK Computer Inc. Sunrise Point-H PMC
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
        Subsystem: ASUSTeK Computer Inc. Sunrise Point-H HD Audio
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
        Subsystem: ASUSTeK Computer Inc. Sunrise Point-H SMBus                                                      
        Kernel modules: i2c_i801                                                                                    
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-V (rev 31)                              
        Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I219-V                                             
        Kernel driver in use: e1000e                                                                                
        Kernel modules: e1000e                                                                                      
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii PRO [Radeon R9 290]                
        Subsystem: PC Partner Limited / Sapphire Technology Hawaii PRO [Radeon R9 290]                              
        Kernel driver in use: radeon                                                                                
        Kernel modules: radeon                                                                                      
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii HDMI Audio                                      
        Subsystem: PC Partner Limited / Sapphire Technology Hawaii HDMI Audio                                       
        Kernel driver in use: snd_hda_intel                                                                         
        Kernel modules: snd_hda_intel                                                                               
02:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller (rev 01)                     
        Subsystem: Samsung Electronics Co Ltd NVMe SSD Controller                                                   
        Kernel driver in use: nvme
        Kernel modules: nvme
```

---

### Post by ajgreeny on 2017-06-01
```
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Hawaii PRO [Radeon R9 290]                
        Subsystem: PC Partner Limited / Sapphire Technology Hawaii PRO [Radeon R9 290]                              
        Kernel driver in use: radeon                                                                                
        Kernel modules: radeon
```
I suspect that the problem may be the AMD graphics card which as far as I'm aware is not (yet) well supported by the proprietary AMD drivers AMDGPU or AMDGPU-PRO so yours is using the open source radeon driver.
Have you looked in **Additional Drivers** to see if anything else is available for you?  If not do so now and try any that are listed.

It is a long time since I have used any AMD hardware so I can't tell you much more at this time but other users may be able to help further so keep looking back at this thread and you may get some better, more useful answers than mine.

---

### Post by Bucky Ball on 2017-06-02
The driver (and card) was there in the first output I asked for in (sudo lshw -C video) and was posted in post #3. ;)

driver=radeon

And card:

Hawaii PRO [Radeon R9 290]

Is that of the problematic variety? I know some of the radeons are at this point.

---

### Post by ajgreeny on 2017-06-02
So it was; I missed that when reading too quickly.
Thanks BB.

---

### Post by omrthaq on 2017-06-02
hm.

But why is running windows so good?

---

### Post by QIII on 2017-06-02
Because the Windows driver for the monolithic and rarely-changing Windows graphics stack works better than AMDGPU does for that GPU under Linux at the moment.   The open source Radeon driver is functional and a great driver for most people, but it is not capable of good gaming performance.

My R9 380X, which is supported by AMDGPU-PRO, works like a champ.

AMD is working very hard to provide the excellent open source driver we have been asking for for years.  There is a lot of "road construction" right now and it is a bumpy ride.  To support their new generation of hardware and also  Vulkan, AMD has had to completely redesign their Linux driver.

---

### Post by omrthaq on 2017-06-02
hello

i've installed drivers. But now the Resolution is very very bad.

Im out with linux. Sorry but on ubuntu i had over 300fps and even my usb is better than my pc.
I go to windows because i cant do anything

hello Windows >:(

---

### Post by QIII on 2017-06-02
If Windows works better for your purposes, then by all means use it.  Nothing wrong with that.  Use what works.

---

### Post by Bucky Ball on 2017-06-02
Oh well. Perhaps have another go when AMD have finished on the driver or if you acquire hardware that works well with Ubuntu. If you're intending on using Ubuntu/Mint, vid/wireless hardware particularly are a major consideration. 

If you've finished with Mint, perhaps you could mark this thread as solved and save others some time? See the link in my signature for how or use Thread Tools at top of page. Good luck. :)

---

### Post by omrthaq on 2017-06-02
Thanks. :).

---

