---
title: "Upgrading from 16.04 to 18.04 leaves lots of problems, help."
date: 2018-10-18
forum: Installation &amp; Upgrades
---

### Post by alynur2 on 2018-10-18
H guys, I finally upgraded my LXDE 16.04 to Lubuntu 18.04. Since these new problems have occured due to the upgrade, I figure I'll list them here and you guys can guide me as to if I should start a new post in a different section. 
1. First off I get an error message whenever I run sudo apt update, that being:
        E: The repository 'http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu bionic Release' does not have a Release file.
2. Synaptic Manager will not launch. I've removed it and reinstalled it but still no go.
3. My printer won't print. I've removed it and re-added it numerous times both in Printers and Hplip Toolbox.It will show me the ink levels in Hplip but        no matter what I try to print, nothing happens. The printer works fine in any of my other distros.
4. A few of my apps won't launch, like Timeshift, Gparted and Xsane image scanning program, get an failed to open device message.

There may be others but I haven't checked everything yet.
Here is my computer info.

```
albert@albert-desktop:~$ inxi -FzSystem:    Host: albert-desktop Kernel: 4.15.0-36-generic x86_64 bits: 64
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop Mobo: ASRock model: AM1B-M serial: N/A
           BIOS: American Megatrends v: P1.50 date: 04/29/2015
CPU:       Quad core AMD Athlon 5370 APU with Radeon R3 (-MCP-) 
           cache: 2048 KB
           clock speeds: max: 2200 MHz 1: 938 MHz 2: 918 MHz 3: 963 MHz
           4: 1029 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
           Resolution: 1024x768@75.03hz, 1024x768@75.03hz
           OpenGL: renderer: AMD CEDAR (DRM 2.50.0 / 4.15.0-36-generic, LLVM 6.0.0)
           version: 3.3 Mesa 18.0.5
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300/7300 Series]
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-36-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 500.1GB (32.0% used)
           ID-1: /dev/sda model: WDC_WD5000AUDX size: 500.1GB
Partition: ID-1: / size: 49G used: 33G (71%) fs: ext4 dev: /dev/sda2
           ID-2: swap-1 size: 8.65GB used: 0.00GB (0%)
           fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 23.1C mobo: N/A gpu: 56.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 261 Uptime: 1:09 Memory: 2111.9/7914.6MB
           Client: Shell (bash) inxi: 2.3.56 



```

---

### Post by him610 on 2018-10-18
Hello alynur2,

I have a similar system as yours - Asus AM1I-A, AMD Athlon 5350 running Xubuntu 18.04.1 which I believe I upgraded in place from 16.04 around May 2018. All of my applications work as expected; although, I did find it necessary to reinstall the drivers to my printer/scanner/fax device.

Lubuntu 18.04 release notes can be found here [https://lubuntu.net/lubuntu-18-04-bionic-beaver-released/]("https://lubuntu.net/lubuntu-18-04-bionic-beaver-released/")

With several of your applications not working, you may have more success by doing a fresh installation from scratch. There is a download link referenced in the release notes above.

Good luck.

---

### Post by alynur2 on 2018-10-18
Hi him610, I was afraid somebody was going to say that. I was hoping to avoid that since I have this partition set up with a few extras which needed more partition space. It is what it is so I guess I'll have to bite the bullet.

---

### Post by Claus7 on 2018-10-19
Hello,

have you tried changing the server that programs are downloaded? Since synaptic does not work, have you tried software and updates instead? Since something is malfunctioning in your updates, if you fix it, it might fix the other problems as well.

Regards!

---

