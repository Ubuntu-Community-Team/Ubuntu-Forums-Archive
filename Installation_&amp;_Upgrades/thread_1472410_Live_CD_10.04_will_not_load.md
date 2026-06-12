---
title: "Live CD 10.04 will not load?"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by leopar on 2010-05-04
[FONT=Arial, serif][SIZE=2]Hi, Hope you can help. This is my first post, I'm no expert but can you usually follow instructions so long as they are step-by-step. [/SIZE][/FONT] 
  [FONT=Arial, serif][SIZE=2]I'm dual booting Ubuntu 9.10 (x86 64 bit) with windows 7 on an ASUS P5B Deluxe WiFi ([/SIZE][/FONT][COLOR=#000000][FONT=Arial, serif][SIZE=2]P965 Express chipset) [/SIZE][/FONT][/COLOR][FONT=Arial, serif][SIZE=2]and I have a separate home partition.[/SIZE][/FONT]
  

  [FONT=Arial, serif][SIZE=2]My Graphics card is an ATI Radeon HD5570 with the Linux ATI propriety fglrx driver (ati-driver-installer-10-4-x86.x86_64.run) installed and working successfully. [/SIZE][/FONT] 
  [FONT=Arial, serif][SIZE=2]My monitor is an ASUS VH242H 24" Widescreen with 1920x1080 resolution.[/SIZE][/FONT]
  

  [FONT=Arial, serif][SIZE=2]From within Windows, I've backed up my Windows and Ubuntu installation partitions to a separate external harddrive using Easeus Todo Backup 1.1.[/SIZE][/FONT]
  

  [FONT=Arial, serif][SIZE=2]I think I'm now ready to replace my existing Ubuntu 9.10 with a fresh install of Ubuntu 10.04 but I can't get Live CD to load beyond the Ubuntu screen with the alternating white and red dots. After cycling through for a while my monitor just shuts down and I have to do a hard reset to fire up the machine again. I've been reading through the forum and I'm left with the impression that the installation of 10.04 is proving a little tricky for some. A number of posts seem to point to graphic card issues? My question is how can I get Live CD to complete the boot cycle so that I can take a look at 10.04? I don't want to mess up my existing system but would love to take a look at 10.04. My xorg.conf file looks like this:[/SIZE][/FONT]
  

  [FONT=Arial, serif][SIZE=2]Section "ServerLayout" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    Identifier     "aticonfig Layout" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    Screen      0  "aticonfig-Screen[0]-0" 0 0 [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]EndSection [/SIZE][/FONT]
  
  [FONT=Arial, serif][SIZE=2]Section "Files" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]EndSection [/SIZE][/FONT]
  
  [FONT=Arial, serif][SIZE=2]Section "Module" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]EndSection [/SIZE][/FONT]
  
  [FONT=Arial, serif][SIZE=2]Section "ServerFlags" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    Option        "Xinerama" "off" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]EndSection [/SIZE][/FONT]
  
  [FONT=Arial, serif][SIZE=2]Section "Monitor" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    Identifier   "aticonfig-Monitor[0]-0" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    Option        "VendorName" "ATI Proprietary Driver" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    Option        "ModelName" "Generic Autodetecting Monitor" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    Option        "DPMS" "true" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]EndSection [/SIZE][/FONT]
  
  [FONT=Arial, serif][SIZE=2]Section "Device" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    Identifier  "aticonfig-Device[0]-0" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    Driver      "fglrx" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    BusID       "PCI:1:0:0" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]EndSection [/SIZE][/FONT]
  
  [FONT=Arial, serif][SIZE=2]Section "Screen" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    Identifier "aticonfig-Screen[0]-0" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    Device     "aticonfig-Device[0]-0" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    Monitor    "aticonfig-Monitor[0]-0" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    DefaultDepth     24 [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    SubSection "Display" [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]        Viewport   0 0 [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]        Depth     24 [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]    EndSubSection [/SIZE][/FONT]
  [FONT=Arial, serif][SIZE=2]EndSection [/SIZE][/FONT]

---

