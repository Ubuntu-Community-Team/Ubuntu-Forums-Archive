---
title: "HP VIctus 15 with problems"
date: 2023-11-04
forum: Installation &amp; Upgrades
---

### Post by negrazo49 on 2023-11-04
Several weeks ago i was given a HP Victus 15 for my birthday. It came with a preinstalled Windows 11 Home version. Everything worked just fine, but i prefer Linux.
So i removed Windows and tried 3 different flavors:
1.- Xubuntu 22.04 LTS.
2.- Linux Mint 22.1
3.- Ubuntu 22.04 LTS

I choose Ubuntu 22.04 LTS.

With the 3 versions i had 2 problems that, at the moment, i cannot solve:

1.- The screen is really dark and opaque, sometimes i cannot see the mouse or its movement across the screen. The HP Victus has a NVIDIA GEFORCE RTX display card.
      I really believe that this is a drivers trouble.
      THE QUESTION IS IF I CAN USE THE DRIVERS FROM WINDOWS 11 AND HOW TO INSTALL THEM?

2.- The 2nd problem is when i try to Suspend, Restart or Shutdown.
      Whenever i try any action it freezes.
      I think this is a BIOS problem and i just don't know how to solve it.

Someone has been through something like that???
Any idea will be very welcome.

Sincerely,
negrazo49

---

### Post by ajgreeny on 2023-11-04
Assuming you can see enough open a terminal and run command ```
inxi Fzx
``` and post back here the output using  code-tags.
See my signature below for a how-to to on using Code-tags.

---

### Post by negrazo49 on 2023-11-05
Typing inxi -Fzx :
```

inxi -Fzx
System:
  Kernel: 6.2.0-36-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: HP product: Victus by HP Gaming Laptop 15-fb0xxx
    v: N/A serial: <superuser required>
  Mobo: HP model: 8A3D v: 35.44 serial: <superuser required> UEFI: AMI
    v: F.17 date: 04/20/2023
Battery:
  ID-1: BAT0 charge: 70.1 Wh (100.0%) condition: 70.1/70.1 Wh (100.0%)
    volts: 17.2 min: 15.4 model: HP Primary status: Full
CPU:
  Info: 6-core model: AMD Ryzen 5 5600H with Radeon Graphics bits: 64
    type: MT MCP arch: Zen 3 rev: 0 cache: L1: 384 KiB L2: 3 MiB L3: 16 MiB
  Speed (MHz): avg: 1395 high: 3300 min/max: 1200/4280 boost: enabled
    cores: 1: 1197 2: 1200 3: 1200 4: 1200 5: 1397 6: 3300 7: 1198 8: 1200
    9: 1260 10: 1200 11: 1197 12: 1200 bogomips: 79052
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
Graphics:
  Device-1: NVIDIA GA107M [GeForce RTX 3050 Mobile] vendor: Hewlett-Packard
    driver: nouveau v: kernel bus-ID: 01:00.0
  Device-2: AMD Cezanne vendor: Hewlett-Packard driver: amdgpu v: kernel
    bus-ID: 06:00.0
  Device-3: Luxvisions Innotech HP Wide Vision HD Camera type: USB
    driver: uvcvideo bus-ID: 1-3:2
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: gpu: amdgpu resolution: 1280x720~144Hz
  OpenGL: renderer: RENOIR (renoir LLVM 15.0.7 DRM 3.49 6.2.0-36-generic)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes
Audio:
  Device-1: NVIDIA vendor: Hewlett-Packard driver: snd_hda_intel v: kernel
    bus-ID: 01:00.1
  Device-2: AMD Renoir Radeon High Definition Audio vendor: Hewlett-Packard
    driver: snd_hda_intel v: kernel bus-ID: 06:00.1
  Device-3: AMD Raven/Raven2/FireFlight/Renoir Audio Processor
    vendor: Hewlett-Packard driver: snd_rn_pci_acp3x v: kernel bus-ID: 06:00.5
  Device-4: AMD Family 17h HD Audio vendor: Hewlett-Packard
    driver: snd_hda_intel v: kernel bus-ID: 06:00.6
  Sound Server-1: ALSA v: k6.2.0-36-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Hewlett-Packard driver: r8169 v: kernel port: e000 bus-ID: 02:00.0
  IF: eno1 state: down mac: <filter>
  Device-2: MEDIATEK MT7921 802.11ax PCI Express Wireless Network Adapter
    vendor: AzureWave driver: mt7921e v: kernel bus-ID: 03:00.0
  IF: wlo1 state: up mac: <filter>
Bluetooth:
  Device-1: IMC Networks Wireless_Device type: USB driver: btusb v: 0.8
    bus-ID: 1-4:3
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
    bt-v: 3.0 lmp-v: 5.2
Drives:
  Local Storage: total: 476.94 GiB used: 96.71 GiB (20.3%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: MZVL2512HCJQ-00BH1
    size: 476.94 GiB temp: 33.9 C
Partition:
  ID-1: / size: 467.89 GiB used: 96.7 GiB (20.7%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 43.0 C mobo: N/A gpu: amdgpu temp: 40.0 C
  Fan Speeds (RPM): cpu: 0 fan-2: 0
Info:
  Processes: 341 Uptime: 32m Memory: 14.95 GiB used: 3.18 GiB (21.3%)
  Init: systemd runlevel: 5 Compilers: gcc: N/A Packages: 2028 Shell: Bash
  v: 5.1.16 inxi: 3.3.13

```

---

### Post by MAFoElffen on 2023-11-05
I just finished with helping resolve another Laptop with this combination of GPU (NVidia GA107) and AMD iGPU (Cezanne), the magic combination that I found for theirs to work best was to first edit the /etc/default/grub file
```

sudo nano /etc/default/grub

```
And edit these lines to this
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=4"
GRUB_CMDLINE_LINUX="radeon.si_support=0 amdgpu.si_support=1 radeon.cik_support=0 amdgpu.cik_support=1 amdgpu.dc=1"

```
Save and exit. Pick up  the changes
```

sudo update-grub

```
Then install this NVidia driver
```

sudo apt remove --purge nvidia*
sudo apt install -y nvidia-driver-470

```
The combination of those kernel boot parameters and the driver should fix your graphics and resuming from suspend issues.

Try those and tell me how that goes...

---

### Post by negrazo49 on 2023-11-06
I just did what you told me, and the issue with the Suspend, Restart and Shutdown has been fixed.
The problem with the graphics card still remains. 
The file /etc/default/grub was modified:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
# GRUB_TIMEOamdgpu.cik_support=1 amdgpu.dc=1"UT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=4"
GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX="radeon.cik_support=1 amdgpu.cik_support=1 amdgpu.dc=1"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


```

Thank you for your help.

Negrazo49

---

### Post by MAFoElffen on 2023-11-06
Sorry, corrected post #4. That should have been like this
```

GRUB_CMDLINE_LINUX="radeon.si_support=0 amdgpu.si_support=1 radeon.cik_support=0 amdgpu.cik_support=1 amdgpu.dc=1"

```
And did nvidia-driver-470 install okay? Now lets see the output from 
```

nvidia-smi

```

---

### Post by negrazo49 on 2023-11-07
```

rmuneton@rafael-Victus:~$ nvidia-smi
Tue Nov  7 12:02:13 2023       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 470.223.02   Driver Version: 470.223.02   CUDA Version: 11.4     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   36C    P0    12W /  N/A |      5MiB /  3910MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      2878      G   /usr/lib/xorg/Xorg                  4MiB |
+-----------------------------------------------------------------------------+



```

This is the output. Everything seems OK.

---

### Post by MAFoElffen on 2023-11-07
But even then, it is still having graphics issues? Are you running Xorg or Wayland?

If Wayland, try Xorg. NVidia seems happier with Xorg as the graphics engine.

---

### Post by negrazo49 on 2023-11-07
The issue with the graphics driver almost is gone, now i can see the display much better.
Anyway, i don't know what are you talking about Xorg or Wayland.
Where can i check this point?

Thanks for your help MAFoElffen, has been really nice to know there is someone who can help us.

Sincerely,
Negrazo49.

---

### Post by #&amp;thj^% on 2023-11-07
> **negrazo49 said:**
> 
Anyway, i don't know what are you talking about Xorg or Wayland.
Where can i check this point?
.
Yep he's a keeper
EDIT: in post #3 you show this:
```
 Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
```
Your on a Wayland session.
to see real quick Xorg or Wayland
```
inxi -G | grep Display
  Display: x11 server: X.Org v: 1.21.1.7 driver: X: loaded: modesetting

```

---

### Post by MAFoElffen on 2023-11-07
To swap, Log out...

After you select your user at the Graphical Login / GDM3... When the password dialog box appears, ypou will see a Gear Icon appear in the lower right of tha screen. Select it with your mouse and a dropdown box will appear. Select "Ubuntu Xorg"... Then enter your password and log back in.

---

### Post by negrazo49 on 2023-11-08
Following the thread:
```

rmuneton@rafael-Victus:~$ inxi -G | grep Display
  Display: x11 server: X.Org v: 1.21.1.4 driver: X:

```

This is the output, it seems that Xorg is working.
Anyway, as i told you  before, i can see my display much better than before all of this stuff and i think that i should close this thread.

Thank you again,
Negrazo49.

---

### Post by MAFoElffen on 2023-11-08
Happy things are working now. Please select the "Thread Tools" link at the upper right of the first page of this thread and mark your thread as "Solved'. That way others can find your solution to their similar problems.

---

### Post by salva-tore on 2024-02-12
i have the issue with standby in my hp victus 15 but  with intel cpu, con someone help me?

---

### Post by #&amp;thj^% on 2024-02-12
> **salva-tore said:**
> i have the issue with standby in my hp victus 15 but  with intel cpu, con someone help me?

Please read Post #11, and this on Gnome BTW

---

### Post by vinayak-thosar on 2024-03-13
System:
  Kernel: 6.5.0-25-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: HP product: Victus by HP Gaming Laptop 15-fb0xxx
    v: N/A serial: <superuser required>
  Mobo: HP model: 8A3E v: 35.44 serial: <superuser required> UEFI: AMI
    v: F.18 date: 08/11/2023
Battery:
  ID-1: BAT0 charge: 45.8 Wh (95.2%) condition: 48.1/48.1 Wh (100.0%)
    volts: 13.2 min: 11.6 model: HP Primary status: Charging
CPU:
  Info: 6-core model: AMD Ryzen 5 5600H with Radeon Graphics bits: 64
    type: MT MCP arch: Zen 3 rev: 0 cache: L1: 384 KiB L2: 3 MiB L3: 16 MiB
  Speed (MHz): avg: 1888 high: 3986 min/max: 400/4280 cores: 1: 2657
    2: 3986 3: 3264 4: 400 5: 2693 6: 2404 7: 400 8: 1510 9: 2237 10: 400
    11: 400 12: 2306 bogomips: 79045
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Mobile / Max-Q]
    vendor: Hewlett-Packard driver: nvidia v: 535.161.07 bus-ID: 01:00.0
  Device-2: AMD Cezanne vendor: Hewlett-Packard driver: amdgpu v: kernel
    bus-ID: 06:00.0
  Device-3: Luxvisions Innotech HP Wide Vision HD Camera type: USB
    driver: uvcvideo bus-ID: 1-3:3
  Display: x11 server: X.Org v: 1.21.1.4 driver: X:
    loaded: amdgpu,ati,nvidia unloaded: fbdev,modesetting,nouveau,radeon,vesa
    gpu: amdgpu resolution: 1920x1080~144Hz
  OpenGL: renderer: RENOIR (renoir LLVM 15.0.7 DRM 3.54 6.5.0-25-generic)
    v: 4.6 Mesa 23.2.1-1ubuntu3.1~22.04.2 direct render: Yes
Audio:
  Device-1: NVIDIA vendor: Hewlett-Packard driver: snd_hda_intel v: kernel
    bus-ID: 01:00.1
  Device-2: AMD Renoir Radeon High Definition Audio vendor: Hewlett-Packard
    driver: snd_hda_intel v: kernel bus-ID: 06:00.1
  Device-3: AMD Raven/Raven2/FireFlight/Renoir Audio Processor
    vendor: Hewlett-Packard driver: snd_rn_pci_acp3x v: kernel bus-ID: 06:00.5
  Device-4: AMD Family 17h HD Audio vendor: Hewlett-Packard
    driver: snd_hda_intel v: kernel bus-ID: 06:00.6
  Sound Server-1: ALSA v: k6.5.0-25-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Hewlett-Packard driver: r8169 v: kernel port: e000 bus-ID: 02:00.0
  IF: eno1 state: down mac: <filter>
  Device-2: MEDIATEK MT7921 802.11ax PCI Express Wireless Network Adapter
    vendor: AzureWave driver: mt7921e v: kernel bus-ID: 03:00.0
  IF: wlo1 state: up mac: <filter>
Bluetooth:
  Device-1: IMC Networks Wireless_Device type: USB driver: btusb v: 0.8
    bus-ID: 1-4:4
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
    bt-v: 3.0 lmp-v: 5.2
Drives:
  Local Storage: total: 476.94 GiB used: 12.09 GiB (2.5%)
  ID-1: /dev/nvme0n1 vendor: Western Digital
    model: WD PC SN810 SDCPNRY-512G-1006 size: 476.94 GiB temp: 49.9 C
Partition:
  ID-1: / size: 53.79 GiB used: 12 GiB (22.3%) fs: ext4 dev: /dev/nvme0n1p6
  ID-2: /boot/efi size: 256 MiB used: 89.7 MiB (35.0%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: partition size: 93.13 GiB used: 0 KiB (0.0%)
    dev: /dev/nvme0n1p5
Sensors:
  System Temperatures: cpu: 52.0 C mobo: N/A gpu: amdgpu temp: 49.0 C
  Fan Speeds (RPM): cpu: 2702 fan-2: 2414
Info:
  Processes: 389 Uptime: 18m Memory: 7.09 GiB used: 2.14 GiB (30.2%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 1776 Shell: Bash
  v: 5.1.16 inxi: 3.3.13


I have this configuration but I unable to control my brightness 
I have followed this command 
sudo nano /etc/default/grub
and updated file
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
like this and saved and then rebooted but now the brightness is stuck on MAX 
And if follow this grub coomand again to remove the acpi_backlight=vendor I am unable to write it again 
Also the fn keys for brightness is not working i have stuck with max brightness

---

