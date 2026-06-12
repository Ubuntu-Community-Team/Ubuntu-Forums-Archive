---
title: "High CPU usage - latest Ubu, R/RStudio install - Graphic Card?"
date: 2019-03-04
forum: Installation &amp; Upgrades
---

### Post by rdfleay on 2019-03-04
Hey guys!
SO i have realllly worked up to a level that I understand most of all this new stuff.. Computers! but really if someone could walk me through some explanations and possibly try give an exact assist to my current last little problem before i can tackle some serious Rstudio data....
THank YOU!!!

System:    Host: -Lenovo-G50-45 Kernel: 4.15.0-45-generic x86_64
           bits: 64
           Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.2 LTS
Machine:   Device: laptop System: LENOVO product: 80E3 v: Lenovo G50-45 serial: N/A
           Mobo: LENOVO model: Lancer 5B2 v: 31900058 WIN serial: N/A
           UEFI: LENOVO v: A2CN45WW(V2.13) date: 08/04/2016
Battery    BAT1: charge: 9.9 Wh 52.9% condition: 18.7/28.5 Wh (66%)
CPU:       Quad core AMD A6-6310 APU with AMD Radeon R4 Graphics (-MCP-) 
           cache: 2048 KB
           clock speeds: max: 1800 MHz 1: 1124 MHz 2: 1183 MHz 3: 1243 MHz
           4: 1221 MHz
[B]Graphics:  Card: Advanced Micro Devices [AMD/ATI] Mullins [Radeon R4/R5 Graphics]
           Display Server: x11 (X.Org 1.19.6 ) driver: radeon
           Resolution: 1366x768@60.00hz
           OpenGL: renderer: AMD MULLINS (DRM 2.50.0, 4.15.0-45-generic, LLVM 7.0.0)
           version: 4.5 Mesa 18.2.2[/B]
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] Kabini HDMI/DP Audio
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-45-generic
Network:   Card-1: Realtek RTL8723BE PCIe Wireless Network Adapter
           driver: rtl8723be
           IF: wlp1s0 state: up mac: 34:68:95:3e:4c:5b
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp2s0 state: down mac: 68:f7:28:81:b6:ab
Drives:    HDD Total Size: 1000.2GB (1.3% used)
           ID-1: /dev/sda model: ST1000LM024_HN size: 1000.2GB
Partition: ID-1: / size: 506G used: 13G (3%) fs: ext4 dev: /dev/sda6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 61.8C mobo: N/A gpu: 61.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 341 Uptime: 2:46 Memory: 4227.1/6929.1MB
           Client: Shell (bash) inxi: 2.3.56

---

### Post by rdfleay on 2019-03-04
```
PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND           
 7993 rdfleay   20   0  820632 204960  38560 R  92,4  2,9   0:59.82 rsession          
 1482 rdfleay   20   0 4198132 218356 100348 S  29,4  3,1  18:13.99 gnome-shell       
 1166 rdfleay   20   0 1072380 115628  84032 S  23,4  1,6  19:59.57 Xorg              
16280 rdfleay   20   0 2050848 326444 141060 S  16,2  4,6   8:44.30 Web Content       
  374 rdfleay   20   0 1875092 118352  87420 S   6,9  1,7   3:09.62 gnome-control-c
```   

so i have reduced the R dataframe to 1/50th its size..yes it has a few points).. but my supervisors laptop , which is older than mine and running on 200Gb while mine has 1T (i understand that space is not Everything.. but anyway).. and my quad-core is running 100% ..swapping..swapping around..  I have read that the Graphics packages for the latest Ubu 18.04 lts need some work.. based on what you see here.. or that I am happy to further provide information.. is there a somewhat 'simple' solution.. update / install.. that can get my computer processing the data ( lower the CPU usage/upddate the graphics config.? ) .. i read earlier that the ** LLVM 7.0.0 **in the graphics seems to be the 'draining' issue..
MUCHLY APPRECIATED FOR SOME ASSISTANCE!!
```
 6791 rdfleay   20   0  684092  48548  34892 S   6,3  0,7   5:56.41 gnome-system-mo   
14756 rdfleay   20   0  728276  38092  28512 S   4,0  0,5   0:08.96 gnome-terminal-   
16158 rdfleay   20   0 2847632 486120 153
```

---

