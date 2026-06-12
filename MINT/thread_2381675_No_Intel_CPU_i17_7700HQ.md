---
title: "No Intel CPU i17 7700HQ"
date: 2018-01-01
forum: MINT
---

### Post by astrino on 2018-01-01
Hi,

I just bought new Omen 15-ce011nw with i7-7700HQ and GTX-1060 GPU.

It  should have HD 630 Intel GPU in CPU. But when I've installed Linux (Ubuntu first, but few  distros tested) there is no Intel GPU card. I've searched many forums,  and other users with this CPU has Intel card. Not me :/

 
Whole mine lspci:

```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 05)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 05)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 05)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-H Serial IO I2C Controller #0 (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA Controller [AHCI mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #1 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #5 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #6 (rev f1)
00:1c.6 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #7 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation CM238 HD Audio Controller (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
01:00.0 VGA compatible controller: NVIDIA Corporation GP106M [GeForce GTX 1060 Mobile 6GB] (rev a1)
3b:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 16)
3c:00.0 Network controller: Intel Corporation Wireless 7265 (rev 61)
3d:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
``` 
Other users has:
```
[COLOR=#ff0000]00:02.0 VGA compatible controller: Intel Corporation Device 591b (rev 04)[/COLOR]
01:00.0 VGA compatible controller: NVIDIA Corporation GP106M [GeForce GTX 1060 Mobile 6GB] (rev a1)
```

I don't have 00:02.0 ID BUS.
 
Mine "inxi -F":
```
 Machine:   Device: laptop System: HP product: OMEN by HP Laptop 15-ce0xx
           Mobo: HP model: 8390 v: 40.21 UEFI: American Megatrends v: F.05 date: 06/21/2017
Battery    BAT0: charge: 67.0 Wh 100.0% condition: 67.0/67.0 Wh (100%)
CPU:       Quad core Intel Core i7-7700HQ (-HT-MCP-) cache: 6144 KB
           clock speeds: max: 3800 MHz 1: 2800 MHz 2: 2800 MHz 3: 2800 MHz 4: 2800 MHz 5: 2800 MHz 6: 2800 MHz
           7: 2800 MHz 8: 2800 MHz
Graphics:  Card: NVIDIA GP106M [GeForce GTX 1060 Mobile 6GB]
           Display Server: x11 (X.Org 1.19.5 ) driver: nvidia Resolution: 1920x1080@120.11hz
           OpenGL: renderer: GeForce GTX 1060 with Max-Q Design/PCIe/SSE2 version: 4.5.0 NVIDIA 384.98
Audio:     Card Intel CM238 HD Audio Controller driver: snd_hda_intel Sound: ALSA v: k4.14.0-sabayon
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
           IF: enp59s0 state: down mac: 3c:52:82:e3:49:1a
           Card-2: Intel Wireless 7265 driver: iwlwifi
           IF: wlp60s0 state: up mac: cc:2f:71:15:c7:3c
Drives:    HDD Total Size: 2000.4GB (35.0% used)
           ID-1: /dev/sda model: HGST_HTS721010A9 size: 1000.2GB
           ID-2: USB /dev/sdb model: Expansion size: 1000.2GB
Partition: ID-1: / size: 28G used: 8.7G (34%) fs: ext4 dev: /dev/sda8
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 291 Uptime: 56 min Memory: 2175.4/7802.9MB Client: Shell (bash) inxi: 2.3.34 
```

While other users with this CPU has for example:
```
System:    Host: fabian-Aspire-VN7-793G Kernel: 4.8.0-58-generic x86_64 (64 bit)
           Desktop: KDE Plasma 5.8.7 Distro: Linux Mint 18.2 Sonya                   
Machine:   System: Acer (portable) product: Aspire VN7-793G v: V1.03                 
           Mobo: KBL model: Neptune_KLS v: V1.03                                     
           Bios: Insyde v: V1.03 date: 02/17/2017                                   
CPU:       Quad core Intel Core i7-7700HQ (-HT-MCP-) cache: 6144 KB                 
           clock speeds: max: 3800 MHz 1: 799 MHz 2: 799 MHz 3: 825 MHz 4: 799 MHz   
           5: 2940 MHz 6: 3186 MHz 7: 1459 MHz 8: 3191 MHz                           
Graphics:  [COLOR=#FF0000]Card-1: Intel Device 591b   [/COLOR]                                              
           Card-2: NVIDIA Device 1c20                                               
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 3840x2160@60.02hz
           GLX Renderer: Mesa DRI Intel Kabylake GT2 GLX Version: 3.0 Mesa 12.0.6
Audio:     Card Intel Device a171 driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.8.0-58-generic
Network:   Card-1: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter
           driver: ath10k_pci
           IF: wlp2s0 state: up mac: 58:00:e3:78:0a:cd
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           IF: enp3s0 state: down mac: 30:65:ec:bb:11:60
Drives:    HDD Total Size: 1000.2GB (12.2% used)
           ID-1: /dev/nvme0n1 model: N/A size: 512.1GB
           ID-2: /dev/sda model: ST1000LM035 size: 1000.2GB
Partition: ID-1: / size: 113G used: 40G (37%) fs: ext4 dev: /dev/nvme0n1p5
           ID-2: swap-1 size: 34.24GB used: 0.00GB (0%) fs: swap dev: /dev/nvme0n1p6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 39.0C mobo: 31.0C
           Fan Speeds (in rpm): cpu: N/A
``` 
Under windows also I cant find Intel card at device manager under Graphics card subtree.
 
Anyone has the same problem? Maybe its normal behavior in HP Omen? Or its malfunction at CPU.
Could any Omen+Linux users post me their lspci or inxi -F output?
Thanks in advance.

---

### Post by gordintoronto on 2018-01-01
That laptop is configured so the GTX 1060 is the sole GPU.

---

### Post by Perfect Storm on 2018-01-03
Thread moved to mint.

---

