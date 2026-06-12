---
title: "UEFI boot issue solved by Ubuntu studio"
date: 2021-05-21
forum: Installation &amp; Upgrades
---

### Post by oliverjames on 2021-05-21
I have inherited a fairly recent PC tower. This has an Asus P8H61_PRO motherboard that's advertised as tune for Windows, ie has no option for disabling secure boot, although legacy ROM option exists. The graphics card is by Nvidia; effectivement a bit of a challenge. I tried many Linux OS from Mint through Ubuntu, Debian, Manjaro, MX, Fedora and then Xubuntu, all with the legacy ROM setting. Boot was generally interrupted by error messages related to AHCI issues.

I did install Win 10 to check the hardware and it booted perfectly. I then retried the above Linux OSs but this time with the BIOS set to EFI mode. The only Linux that worked for this mboard was Xubuntu and even then it was generall necessary to reboot 2 or 3 times. In addition I always had to turn off number lock in order to imput the pwd.

Then I tried Ubuntu studio, and lo, the system now boots reliably (EFI mode) and the numberlock issue has vanished. Could this be due to the low latency kernel perhaps? 

For info, some detail of the machine setup:
```
$ inxi -F
System:
  Host: richard-Luki Kernel: 5.8.0-53-lowlatency x86_64 bits: 64 
  Desktop: Xfce 4.14.2 Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: ASUSTeK model: P8H61 PRO v: Rev X.0x 
  serial: <superuser/root required> UEFI: American Megatrends v: 4205 
  date: 05/29/2013 
CPU:
  Topology: Quad Core model: Intel Core i5-2500 bits: 64 type: MCP 
  L2 cache: 6144 KiB 
  Speed: 1599 MHz min/max: 1600/3700 MHz Core speeds (MHz): 1: 1607 2: 1622 
  3: 1663 4: 1608 
Graphics:
  Device-1: NVIDIA GF119 [GeForce GT 520] driver: nvidia v: 390.143 
  Display: x11 server: X.Org 1.20.9 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: GeForce GT 520/PCIe/SSE2 v: 4.6.0 NVIDIA 390.143 
Audio:
  Device-1: Intel 6 Series/C200 Series Family High Definition Audio 
  driver: snd_hda_intel 
  Device-2: NVIDIA GF119 HDMI Audio driver: snd_hda_intel 
  Device-3: Texas Instruments PCM2706 stereo audio DAC type: USB 
  driver: hid-generic,snd-usb-audio,usbhid 
  Sound Server: ALSA v: k5.8.0-53-lowlatency 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: 54:04:a6:3e:5f:42 
Drives:
  Local Storage: total: 931.51 GiB used: 69.57 GiB (7.5%) 
  ID-1: /dev/sda vendor: Western Digital model: WD10EZRX-00A8LB0 
  size: 931.51 GiB 
Partition:
  ID-1: / size: 25.19 GiB used: 13.48 GiB (53.5%) fs: ext4 dev: /dev/sda10 
  ID-2: /home size: 5.22 GiB used: 609.6 MiB (11.4%) fs: ext4 dev: /dev/sda8 
  ID-3: swap-1 size: 6.26 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda6 
Sensors:
  System Temperatures: cpu: 29.8 C mobo: 27.8 C gpu: nvidia temp: 53 C 
  Fan Speeds (RPM): N/A gpu: nvidia fan: 40% 
Info:
  Processes: 256 Uptime: 57m Memory: 3.81 GiB used: 1.32 GiB (34.6%) 
  Shell: bash inxi: 3.0.38 


```

---

