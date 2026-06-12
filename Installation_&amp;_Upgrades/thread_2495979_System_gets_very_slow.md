---
title: "System gets very slow"
date: 2024-03-10
forum: Installation &amp; Upgrades
---

### Post by Pierre Dartigues on 2024-03-10
Hello folks,
I am using Ubuntu 22.04 as my main system on an ASUS laptop. After conquering boot problems by using BootRepair. I have been installing Ubuntu 23.10 on an external harddisk so that I am able to boot from that external disk without interfering with the internal boot disk.
However,
Immeadiately after booting up as  from the internal disk, to UBUNTU 22.03, the system gets slow and increasingly slower when continuing using the system. Even Terminal needs more than 1,5 minute to start up. LibreOffice version 7.3.2 ditto, as well as Thunderbird v 115.8.1I used the maintenance option from the Grub menu in order to check all file systems, to repair broken chains and to free up disk space. I also updated the system by running [HTML]sudo apt-get update && sudo apt-get upgrade -y [/HTML]. It completed but with errors.

I runned [HTML]inxi -Fxz[/HTML] , the results are:

```
Asus:~$ inxi -FxzSystem:
  Kernel: 6.5.0-25-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: ASUSTeK product: N550JK v: 1.0
    serial: <superuser required>
  Mobo: ASUSTeK model: N550JK v: 1.0 serial: <superuser required>
    UEFI: American Megatrends v: N550JK.210 date: 06/12/2019
Battery:
  ID-1: BAT0 charge: 46.3 Wh (98.3%) condition: 47.1/60.5 Wh (77.9%)
    volts: 15.0 min: 15.0 model: ASUSTeK N550-40 status: Not charging
CPU:
  Info: quad core model: Intel Core i7-4710HQ bits: 64 type: MT MCP
    arch: Haswell rev: 3 cache: L1: 256 KiB L2: 1024 KiB L3: 6 MiB
  Speed (MHz): avg: 1922 high: 2495 min/max: 800/3500 cores: 1: 2378
    2: 1100 3: 800 4: 1894 5: 2495 6: 1749 7: 2469 8: 2495 bogomips: 39908
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel 4th Gen Core Processor Integrated Graphics vendor: ASUSTeK
    driver: i915 v: kernel bus-ID: 00:02.0
  Device-2: NVIDIA GM107M [GeForce GTX 850M] vendor: ASUSTeK driver: nvidia
    v: 470.239.06 bus-ID: 01:00.0
  Device-3: IMC Networks USB2.0 UVC HD Webcam type: USB driver: uvcvideo
    bus-ID: 3-7:5
  Display: x11 server: X.Org v: 1.21.1.4 driver: X:
    loaded: modesetting,nvidia unloaded: fbdev,nouveau,vesa gpu: i915
    resolution: 1920x1080~60Hz
  OpenGL: renderer: NVIDIA GeForce GTX 850M/PCIe/SSE2
    v: 4.6.0 NVIDIA 470.239.06 direct render: Yes
Audio:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio
    driver: snd_hda_intel v: kernel bus-ID: 00:03.0
  Device-2: Intel 8 Series/C220 Series High Definition Audio
    vendor: ASUSTeK driver: snd_hda_intel v: kernel bus-ID: 00:1b.0
  Sound Server-1: ALSA v: k6.5.0-25-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Wireless 7260 driver: iwlwifi v: kernel bus-ID: 04:00.0
  IF: wlp4s0 state: up mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: ASUSTeK driver: r8169 v: kernel port: d000 bus-ID: 05:00.0
  IF: enp5s0 state: down mac: <filter>
Bluetooth:
  Device-1: Intel Bluetooth wireless interface type: USB driver: btusb v: 0.8
    bus-ID: 3-5:4
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
    bt-v: 2.1 lmp-v: 4.0
Drives:
  Local Storage: total: 744.38 GiB used: 280.14 GiB (37.6%)
  ID-1: /dev/mmcblk0 type: USB vendor: SanDisk model: SL32G size: 28.97 GiB
  ID-2: /dev/sda vendor: Etelcom model: SSD0512S00 size: 476.94 GiB
  ID-3: /dev/sdb type: USB vendor: SanDisk model: SD6SB1M256G1002
    size: 238.47 GiB
Partition:
  ID-1: / size: 368.62 GiB used: 232.1 GiB (63.0%) fs: ext4 dev: /dev/sda4
  ID-2: /boot/efi size: 99.2 MiB used: 31.9 MiB (32.2%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 512 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 66.0 C mobo: N/A gpu: nvidia temp: 57 C
  Fan Speeds (RPM): cpu: 2400
Info:
  Processes: 334 Uptime: 2h 3m Memory: 7.63 GiB used: 3.31 GiB (43.4%)
  Init: systemd Compilers: gcc: 11.4.0 Packages: 3230 Shell: Bash v: 5.1.16
  inxi: 3.3.13



```


What could I do to get this installation up to normal speed again?

---

### Post by TheFu on 2024-03-10
Please fix the inxi output above.  

Somehow it was pasted as 1 line.  Just run it again in a terminal, select everything in the terminal and use the middle mouse button to past that into the code-/code tags you already have.  It will have lines where expected that way.  To hard to read as it is.  

Also, the attachment link isn't working.

Please make it easy to help you, not hard.

My first guess is that you could load a lighter DE, like Mate, XFCE, or LXQt. Avoid Gnome.
My second guess is that you could use a larger swap setup - 4GB for desktops seems to be the right answer.
My last guess is to ensure the storage used is as fast as possible (preferably an SSD), connected to a USB3 port (not USB2).  Slow Flash storage will cause a slow system.

---

### Post by Pierre Dartigues on 2024-03-10
With your help I managed to correct the "one-line" issue. Thanx.
My sda is an SSD with 403 GB reserved for UBUNTU data and swap, the swap space is 2 GB.
So, I found a tutorial with the name "How To Add Swap Space on Ubuntu 22.04" see: > [https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-22-04) and I followed the instructions therein. I have not been successful in trying to double the swap space to 4 GB but all the rest went smoothly and if I interpreted well what I read in the instructions, 2 GB should be sufficient after all. 
I finished the instructions so far and the system is quicker now. However, I am not satisfied. Opening files or directories can take up to 20 seconds and opening a new program is still slow as well..

---

### Post by TheFu on 2024-03-10
Well, that CPU has a 5.5K passmark. It's a Haswell from 2012-ish.  It should be fine, but not blazing.

With 8GB of RAM, you'll need 4G of swap to deal with bloated browsers.  With just 2GB of RAM, it is easily possible to have memory allocation failures and the OOM watchdog will kill processes.  This comes back to the design of Linux and how memory is allocated.  The designers made a choice.  It is expensive to check if every allocation succeeds like the C language specification expects, so in Linux, every allocation is just returned with a pointer to some free RAM ... even when memory is tight.  This is 90% faster.  It is a trade off and since people doing new systems typically have 16+ GB of RAM, it really is expected there will be plenty.  

Also, the modern browsers all pre-cache links on the current page to make loading them seem faster.  I've seen Firefox claim 64GB of RAM when my system only had 16GB.  We all know this isn't true.  Anyways, over the decades, I've run Linux systems with very little RAM and with lots of RAM - over 1 TB for some servers.  For a desktop, less than 4GB of SWAP is likely to have problems if there isn't at least 16GB of physical RAM in the system.  2G just isn't enough for a desktop doing typical desktop stuff.

The trick to swap is that it cannot be expanded. It has to be disabled, destroyed, then created new with the size you want.

Be careful following instructions from VPS providers when you have a desktop system. They are not the same.  Always start with help.ubuntu.com for official instructions for your specific release and DE.    Your DE is Gnome 42, which is one of the most bloated DEs available.  It really likes fast, direct, access to a fast GPU.  I don't use it.

That leads to the next thing to check - verify you are actually using the GPU you think you are and that the proprietary drivers are being used.  I don't have a laptop with 2 GPUs. Mine all use on-board Intel iGPUs, which makes it better for power use and it avoids buggy nVidia drivers.  I don't know how to read the output for the GPUs above, but I suspect the iGPU from intel is being used with the old 4th-gen drivers.  That is worth checking.  Sorry, I don't know how.

Lastly, we need to look at what is running when things are slow.  **top**, **htop**, **glances** are all user-friendly tools for that.  What you want to find is the specific program that is eating all the CPU and memory (RAM) at the time.  There are other tools available, but these are the most common on desktops. Actually, you can use **inxi -t** to get the top 5 CPU/RAM processes listed too.  Beware that the column headers aren't exactly clear in top/htop/glances.  They are useful, but especially the RAM amounts can be more complex than "used/available".  The CPU **is** clear.  Just know that each CPU core-thread is a "CPU"  So if you have a 2 core (4 thread) CPU, then 400% is the max, not 100%.  These programs are console, so you can find guides on their use from almost anywhere and those guides will be useful - desktop/server - it doesn't matter.

BTW, 22.04 is big into using snap packaged programs rather than the traditional debian packaged programs.  Snaps are good and bad.  They run programs in a constrained sandbox to protect the rest of the system from nefarious code, but if you get only core Canonical code, I don't see the gain in having all those things constrained.  These constrains add overhead  that can be felt by users.  Canonical has gone overboard with snap packages and seems to be forcing as many core packages to be snap-installed because they think it is "new".  Sadly, 22.04 snap packages (aka "snaps") have driven me away from Canonical distros for desktops.  

You can see which snap packages are installed with the 
```
snap list
``` command. For example, 
```
$ snap list
Name    Version        Rev    Tracking       Publisher   Notes
bare    1.0            5      latest/stable  canonical&#10003;  base
core20  20240111       2182   latest/stable  canonical&#10003;  base
lxd     4.0.9-a29c6f1  24061  4.0/stable/…   canonical&#10003;  -
snapd   2.61.2         21184  latest/stable  canonical&#10003;  snapd
```
I use LXD, which is only available under Ubuntu as a snap package. The other snaps are mandated to have lxd. With GUI programs, the required snaps are many and those are each huge.

I moved to Linux Mint to avoid them and those packages.  I'm not against constraints _where they make sense._  I've been running email and browsers under a constraint system that I control for about 8 yrs. Because snaps and my constraint system conflict on a per-program level, both aren't possible and the default constraints that all snap packages have conflict with a number of my workflows.  I have data outside my HOME directory, which snap packages don't allow to be accessed. That's just one example.

To summarize.
[LIST]
[*]Create a 4GB Swap; Add 8GB more RAM, if it is cheap enough and possible - say $20 or less.
[*]Switch to a lighter DE
[*]Check which programs are using the CPU and RAM when things get slow.
[*]
[/LIST]
Hope this is helpful.

---

### Post by Pierre Dartigues on 2024-03-10
It has been helpful! I found this tutorial: > [https://linuxhandbook.com/increase-swap-ubuntu/](https://linuxhandbook.com/increase-swap-ubuntu/) and with its help I managed to increase the swapfile to 4GB. I also changed swappiness to 10 . The result is a faster boot to begin with. The rest I will test now... :) and tested and it works!

---

