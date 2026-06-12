---
title: "Excessive hard drive activity after upgrade to Ubuntu 20.04"
date: 2020-08-11
forum: Installation &amp; Upgrades
---

### Post by ajs37 on 2020-08-11
Whilst I'm not new to Ubuntu, I'm not that skilled with it (although always willing to learn) I have used Ubunbtu 14, 18 and have just upgraded to 20.04 two days ago. Since then the hard drive has barely stopped chuntering and I would like this to stop. My machine has a 120Gb SSD as the boot drive (/dev/sda1 - 30% used), a 4Tb SATA disk ( /dev/sdc1 - 42% used - which is the one that is chuntering) and a 6Tb external SATA drive (/dev/sdb1 - 34% used) which has been setup for backup. The system now has 16Gb ram (having just added another 8Gb, which has been recognised in BIOS and by Ubuntu 20)
Any help to find out what the hard drive is doing, or reassurance that it is behaving normally after an upgrade would be gratefully received
thanks!

---

### Post by TheFu on 2020-08-11
Start by posting the command and output from: **inxi -Fxxpztcmc0 **
That command gets us an overview of the system and the top file CPU/RAM using processes.

Please post using the Advanced Reply and wrap everything in "code tags" - that's the '#' button in the advanced editor here.

---

### Post by dino99 on 2020-08-11
Also glace at 'journalctl -b' to know about possible issue (red lines = errors, yellow ones = harmless warnings)

Such problem can be the result of some leftover links/symlinks/old settings that disturb the actual system. So first clean it via autoclean, autoremove then reboot.

---

### Post by ajs37 on 2020-08-12
thanks for the responses - This is the output from your suggested inxi -Fxxpztcmc0 command - 


```
System:
  Kernel: 5.4.0-42-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: Gnome 3.36.3 wm: gnome-shell dm: GDM3 
  Distro: Ubuntu 20.04.1 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: ASUSTeK model: A88XM-PLUS v: Rev X.0x serial: <filter> 
  BIOS: American Megatrends v: 2102 date: 01/20/2015 
CPU:
  Topology: Quad Core model: AMD A10-7700K Radeon R7 10 Compute Cores 4C+6G 
  bits: 64 type: MCP arch: Steamroller rev: 1 L2 cache: 2048 KiB 
  flags: avx lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 32719 
  Speed: 1895 MHz min/max: 1900/4100 MHz Core speeds (MHz): 1: 1895 2: 1894 
  3: 2778 4: 1939 
Graphics:
  Device-1: AMD Kaveri [Radeon R7 Graphics] vendor: ASUSTeK driver: radeon 
  v: kernel bus ID: 00:01.0 chip ID: 1002:1313 
  Display: x11 server: X.Org 1.20.8 driver: ati,radeon 
  unloaded: fbdev,modesetting,vesa compositor: gnome-shell 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: AMD KAVERI (DRM 2.50.0 5.4.0-42-generic LLVM 10.0.0) 
  v: 4.5 Mesa 20.0.8 direct render: Yes 
Audio:
  Device-1: AMD Kaveri HDMI/DP Audio vendor: ASUSTeK driver: snd_hda_intel 
  v: kernel bus ID: 00:01.1 chip ID: 1002:1308 
  Device-2: AMD FCH Azalia vendor: ASUSTeK driver: snd_hda_intel v: kernel 
  bus ID: 00:14.2 chip ID: 1022:780d 
  Sound Server: ALSA v: k5.4.0-42-generic 
Network:
  Device-1: Intel Wireless 7265 driver: iwlwifi v: kernel port: f100 
  bus ID: 02:00.0 chip ID: 8086:095a 
  IF: wlp2s0 state: up mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: ASUSTeK driver: r8169 v: kernel port: e000 bus ID: 03:00.0 
  chip ID: 10ec:8168 
  IF: enp3s0 state: down mac: <filter> 
Drives:
  Local Storage: total: 9.21 TiB used: 3.35 TiB (36.4%) 
  ID-1: /dev/sda vendor: Kingston model: SV300S37A120G size: 111.79 GiB 
  speed: 6.0 Gb/s serial: <filter> 
  ID-2: /dev/sdb type: USB vendor: Seagate model: ST6000DM003-2CY186 
  size: 5.46 TiB serial: <filter> 
  ID-3: /dev/sdc vendor: Toshiba model: HDWE140 size: 3.64 TiB 
  speed: 6.0 Gb/s serial: <filter> 
Partition:
  ID-1: / size: 101.81 GiB used: 28.76 GiB (28.2%) fs: ext4 dev: /dev/sda1 
  ID-2: /home size: 3.58 TiB used: 1.50 TiB (41.8%) fs: ext4 dev: /dev/sdc1 
  ID-3: /mnt/backup size: 5.41 TiB used: 1.82 TiB (33.7%) fs: ext4 
  dev: /dev/sdb1 
  ID-4: /snap/canonical-livepatch/94 raw size: 9.1 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop0 
  ID-5: /snap/canonical-livepatch/95 raw size: 9.1 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop2 
  ID-6: /snap/connect4/1 raw size: 8.0 MiB size: <superuser/root required> 
  used: <superuser/root required> fs: squashfs dev: /dev/loop1 
  ID-7: /snap/core/9665 raw size: 97.0 MiB size: <superuser/root required> 
  used: <superuser/root required> fs: squashfs dev: /dev/loop4 
  ID-8: /snap/core/9804 raw size: 96.6 MiB size: <superuser/root required> 
  used: <superuser/root required> fs: squashfs dev: /dev/loop20 
  ID-9: /snap/core18/1880 raw size: 55.0 MiB size: <superuser/root required> 
  used: <superuser/root required> fs: squashfs dev: /dev/loop5 
  ID-10: /snap/core18/1885 raw size: 55.3 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop6 
  ID-11: /snap/gnome-3-28-1804/116 raw size: 160.2 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop8 
  ID-12: /snap/gnome-3-28-1804/128 raw size: 161.4 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop10 
  ID-13: /snap/gnome-3-34-1804/36 raw size: 255.6 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop9 
  ID-14: /snap/gtk-common-themes/1502 raw size: 54.8 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop13 
  ID-15: /snap/gtk-common-themes/1506 raw size: 62.1 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop18 
  ID-16: /snap/icloud-notes-linux-client/10 raw size: 51.3 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop17 
  ID-17: /snap/jgalaxian/125 raw size: 146.9 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop7 
  ID-18: /snap/jgalaxian/129 raw size: 147.9 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop11 
  ID-19: /snap/libreoffice/180 raw size: 416.2 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop15 
  ID-20: /snap/libreoffice/183 raw size: 416.0 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop12 
  ID-21: /snap/snap-store/467 raw size: 49.8 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop16 
  ID-22: /snap/strawberry/3795 raw size: 200.6 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop19 
  ID-23: /snap/strawberry/4244 raw size: 202.4 MiB 
  size: <superuser/root required> used: <superuser/root required> 
  fs: squashfs dev: /dev/loop14 
  ID-24: swap-1 size: 8.22 GiB used: 657.2 MiB (7.8%) fs: swap 
  dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 41.0 C mobo: N/A gpu: radeon temp: 22 C 
  Fan Speeds (RPM): N/A 
Processes:
  CPU top: 5 
  1: cpu: 30.1% command: baloo_file_extractor pid: 3133 
  mem: 7509.5 MiB (50.2%) 
  2: cpu: 7.5% command: chrome pid: 17480 mem: 602.3 MiB (4.0%) 
  3: cpu: 2.5% command: chrome pid: 4563 mem: 218.8 MiB (1.4%) 
  4: cpu: 1.9% command: gnome-shell pid: 2586 mem: 179.9 MiB (1.2%) 
  5: cpu: 1.9% command: chrome pid: 4644 mem: 114.0 MiB (0.7%) 
  Memory top: 5 
  1: mem: 7509.5 MiB (50.2%) command: baloo_file_extractor pid: 3133 
  cpu: 30.1% 
  2: mem: 653.2 MiB (4.3%) command: tracker-extract pid: 1671 cpu: 1.0% 
  3: mem: 602.3 MiB (4.0%) command: chrome pid: 17480 cpu: 7.5% 
  4: mem: 218.8 MiB (1.4%) command: chrome pid: 4563 cpu: 2.5% 
  5: mem: 179.9 MiB (1.2%) command: gnome-shell pid: 2586 cpu: 1.9% 
Info:
  Processes: 279 Uptime: 4h 26m Memory: 14.60 GiB used: 6.69 GiB (45.8%) 
  Init: systemd v: 245 runlevel: 5 default: 2 Compilers: gcc: 9.3.0 alt: 7/9 
  Shell: bash v: 5.0.17 running in: gnome-terminal inxi: 3.0.38

```
Hope I got the code wrapping right! I'm not sure what I would be looking for here - I hope you can educate me!
Cheers
Andy

---

### Post by ajs37 on 2020-08-12
I suspect you are right about the leftover links etc - I do get a lot of red lines and more yellow ones (and some blue ones): I have pasted the redlines and some of the yellow lines here:

```
Aug 12 09:43:20 AndyPC kernel: [COLOR=#CC0000]**ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.VGA.LCD._BCM.AFN7], AE_NOT_FOUND (20190816/psargs-330)**[/COLOR]
Aug 12 09:43:20 AndyPC kernel: 
                               [COLOR=#D7D75F][B]Initialized Local Variables for Method [_BCM]:
[/B][/COLOR]
Aug 12 09:43:20 AndyPC kernel: [COLOR=#CC0000]**ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.VGA.LCD._BCM.AFN7], AE_NOT_FOUND (20190816/psargs-330)**[/COLOR]
Aug 12 09:43:20 AndyPC kernel: 
                               [COLOR=#D7D75F]**Initialized Local Variables for Method [_BCM]:**[/COLOR]
Aug 12 09:43:20 AndyPC kernel: [COLOR=#D7D75F]**  Local0: (____ptrval____) <Obj>           Integer 00000000000000FF**[/COLOR]
Aug 12 09:43:20 AndyPC kernel: [COLOR=#D7D75F]**  Local1: (____ptrval____) <Obj>           Integer 0000000000000000**[/COLOR]
Aug 12 09:43:20 AndyPC kernel: [COLOR=#D7D75F]**Initialized Arguments for Method [_BCM]:  (1 arguments defined for method invocation)**[/COLOR]
Aug 12 09:43:20 AndyPC kernel: [COLOR=#D7D75F]**  Arg0:   (____ptrval____) <Obj>           Integer 0000000000000064**[/COLOR]
Aug 12 09:43:20 AndyPC kernel: [COLOR=#CC0000]**ACPI Error: Aborting method \_SB.PCI0.VGA.LCD._BCM due to previous error (AE_NOT_FOUND) (20190816/psparse-529)**[/COLOR]
Aug 12 09:43:20 AndyPC kernel: [COLOR=#CC0000][B]ACPI Error: Evaluating _BCM failed (20190816/video-357)
[/B][/COLOR]
Aug 12 09:43:22 AndyPC systemd-tmpfiles[1079]: [COLOR=#CC0000][B]rm_rf(/tmp): Operation not permitted
[/B][/COLOR]Aug 12 09:43:23 AndyPC bluetoothd[1254]: [COLOR=#CC0000][FONT=Verdana]**Failed to set mode: Blocked through rfkill (0x12)**[/FONT][/COLOR]

Aug 12 09:43:24 AndyPC colord-sane[1525]: [COLOR=#CC0000]**io/hpmud/musb.c 2101: Invalid usb_open: Permission denied**[/COLOR]
Aug 12 09:43:24 AndyPC colord-sane[1525]: [COLOR=#CC0000]**io/hpmud/musb.c 2101: Invalid usb_open: Permission denied**[/COLOR]
Aug 12 09:43:24 AndyPC colord-sane[1525]: [COLOR=#CC0000][B]io/hpmud/musb.c 2101: Invalid usb_open: Permission denied

[/B][/COLOR]
Aug 12 09:43:26 AndyPC systemd[1]: [COLOR=#CC0000][B]Failed to start VirtualBox Linux kernel module.
[/B][/COLOR]
Aug 12 09:43:28 AndyPC /hpfax[2726]: [COLOR=#CC0000][B][2726]: error: Failed to create /var/spool/cups/tmp/.hplip
[/B][/COLOR]
Aug 12 09:43:32 AndyPC bluetoothd[1254]: [COLOR=#CC0000][B]Failed to set mode: Blocked through rfkill (0x12)
[/B][/COLOR]
Aug 12 09:43:34 AndyPC /hp-systray[2971]: [COLOR=#CC0000][B]hp-systray[2971]: error: hp-systray requires Qt4 GUI and DBus support. Exiting.
[/B][/COLOR]
Aug 12 09:44:50 AndyPC systemd[1]: [COLOR=#D7D75F]**dev-disk-by\x2did-usb\x2dVendorCo_ProductCode_9664561043707297317\x2d0:0\x2dpart1.device: Job dev-disk-by\x2did-usb\x2dVendorCo_ProductCo**[/COLOR][COLOR=#300A24]>[/COLOR]
Aug 12 09:44:50 AndyPC systemd[1]: [COLOR=#CC0000]**Timed out waiting for device /dev/disk/by-id/usb-VendorCo_ProductCode_9664561043707297317-0:0-part1.**[/COLOR]
Aug 12 09:44:50 AndyPC systemd[1]: [COLOR=#D7D75F]**Dependency failed for /mnt/usb-VendorCo_ProductCode_9664561043707297317-0:0-part1.**[/COLOR]
Aug 12 09:44:50 AndyPC systemd[1]: **mnt-usb\x2dVendorCo_ProductCode_9664561043707297317\x2d0:0\x2dpart1.mount: Job mnt-usb\x2dVendorCo_ProductCode_9664561043707297317\x2d0:0**[COLOR=#300A24]>[/COLOR]
Aug 12 09:44:50 AndyPC systemd[1]: **dev-disk-by\x2did-usb\x2dVendorCo_ProductCode_9664561043707297317\x2d0:0\x2dpart1.device: Job dev-disk-by\x2did-usb\x2dVendorCo_ProductCo**[COLOR=#300A24]>[/COLOR]
Aug 12 09:44:50 AndyPC systemd[1]: [COLOR=#D7D75F]**dev-disk-by\x2duuid-5A5CCA945CCA69F9.device: Job dev-disk-by\x2duuid-5A5CCA945CCA69F9.device/start timed out.**[/COLOR]
Aug 12 09:44:50 AndyPC systemd[1]: [COLOR=#CC0000]**Timed out waiting for device /dev/disk/by-uuid/5A5CCA945CCA69F9.**[/COLOR]
Aug 12 09:44:50 AndyPC systemd[1]: [COLOR=#D7D75F]**Dependency failed for /mnt/5A5CCA945CCA69F9.**[/COLOR]
Aug 12 09:44:50 AndyPC systemd[1]: **mnt-5A5CCA945CCA69F9.mount: Job mnt-5A5CCA945CCA69F9.mount/start failed with result 'dependency'.**
Aug 12 09:44:50 AndyPC systemd[1]: Startup finished in 2.674s (kernel) + 1min 30.486s (userspace) = 1min 33.161s.
Aug 12 09:44:50 AndyPC systemd[1]: **dev-disk-by\x2duuid-5A5CCA945CCA69F9.device: Job dev-disk-by\x2duuid-5A5CCA945CCA69F9.device/start failed with result 'timeout'.**
Aug 12 09:44:51 AndyPC tracker-store[2986]: [COLOR=#D7D75F]**Source ID 2 was not found when attempting to remove it**[/COLOR]
Aug 12 09:44:51 AndyPC tracker-store[2986]: OK
Aug 12 09:44:51 AndyPC systemd[1537]: tracker-store.service: Succeeded.
Aug 12 09:44:51 AndyPC tracker-miner-f[1672]: [COLOR=#D7D75F]**Could not remove files in volumes: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message**[/COLOR][COLOR=#300A24]>[/COLOR]
Aug 12 09:44:51 AndyPC tracker-miner-f[1672]: [COLOR=#D7D75F]**Could not remove files in volumes: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message**[/COLOR][COLOR=#300A24]>[/COLOR]
Aug 12 09:44:51 AndyPC tracker-miner-f[1672]: [COLOR=#D7D75F]**Could not initialize currently active mount points: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconne**[/COLOR][COLOR=#300A24]>[/COLOR]
Aug 12 10:31:27 AndyPC sudo[14934]: [COLOR=#CC0000]**    andy : a password is required ; TTY=pts/3 ; PWD=/home/andy ; USER=root ; COMMAND=/usr/sbin/hddtemp -nq -u C /dev/sda**[/COLOR]
Aug 12 10:31:27 AndyPC sudo[14936]: [COLOR=#CC0000]**    andy : a password is required ; TTY=pts/3 ; PWD=/home/andy ; USER=root ; COMMAND=/usr/sbin/hddtemp -nq -u C /dev/sdb**[/COLOR]
Aug 12 10:31:27 AndyPC sudo[14938]: [COLOR=#CC0000]**    andy : a password is required ; TTY=pts/3 ; PWD=/home/andy ; USER=root ; COMMAND=/usr/sbin/hddtemp -nq -u C /dev/sdc**[/COLOR]
Aug 12 14:09:36 AndyPC sudo[18812]: [COLOR=#CC0000]**    andy : a password is required ; TTY=pts/1 ; PWD=/home/andy ; USER=root ; COMMAND=/usr/sbin/hddtemp -nq -u C /dev/sda**[/COLOR]
Aug 12 14:09:36 AndyPC sudo[18814]: [COLOR=#CC0000]**    andy : a password is required ; TTY=pts/1 ; PWD=/home/andy ; USER=root ; COMMAND=/usr/sbin/hddtemp -nq -u C /dev/sdb**[/COLOR]
Aug 12 14:09:36 AndyPC sudo[18816]: [COLOR=#CC0000][B]    andy : a password is required ; TTY=pts/1 ; PWD=/home/andy ; USER=root ; COMMAND=/usr/sbin/hddtemp -nq -u C /dev/sdc

[/B][/COLOR]

```4466 lines - some of the errors I understand - eg; the HP printer errors and the blutooth ones (not enabled in Ubuntu) - the others are a bit more of a puzzle.

Additional info: I did try to install WINE some time ago, with a view to installing itunes (I do a bit of audio work) but I end up with "you have held broken packages" error message - I don't know how to get around this error. I'm not sure how to autoclean or autoremove stuff

Any help gratefully received!
Thanks

---

### Post by TheFu on 2020-08-12
You got the 'code tags' perfect. Thanks. Very readable.

Here's what my first look at the data (may need to come back for more details) has me looking at more closely:

```
System:
  Kernel: **5.4.0-42-generic**
  Desktop: **Gnome 3.36.3 wm**: gnome-shell dm: **GDM3 **
  Distro: **Ubuntu 20.04.1 LTS**
CPU:
  Topology: Quad Core model: AMD **A10-7700K** Radeon R7 10 Compute Cores 4C+6G 
Graphics:
  Display: **x11** server: X.Org 1.20.8 driver: **ati**,radeon 
  unloaded: fbdev,modesetting,vesa compositor: gnome-shell 
Network:
  Device-1: **Intel Wireless 7265** driver: iwlwifi v: kernel port: f100 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: ASUSTeK driver: **r8169** v: kernel port: e000 bus ID: 03:00.0 
Drives:
  Local Storage: total: 9.21 TiB used: 3.35 TiB (36.4%) 
  ID-1: /dev/sda vendor: **Kingston** model: SV300S37A120G size: 111.79 GiB 
  ID-2: /dev/sdb type: USB vendor: **Seagate** model: ST6000DM003-2CY186 
  size: **5.46 TiB** serial: <filter> 
  ID-3: /dev/sdc vendor: Toshiba model: **HDWE140** size: **3.64 TiB **
  speed: 6.0 Gb/s serial: <filter> 
Partition:
[B]  ID-1: / size: 101.81 GiB used: 28.76 GiB (28.2%) fs: ext4 dev: /dev/sda1 
  ID-2: /home size: 3.58 TiB used: 1.50 TiB (41.8%) fs: ext4 dev: /dev/sdc1 
  ID-3: /mnt/backup size: 5.41 TiB used: 1.82 TiB (33.7%) fs: ext4 
  dev: /dev/sdb1 
_[COLOR="#FF0000"]**WAY, WAY, WAY, WAY, WAY, WAY, WAY, WAY, WAY, WAY, WAY,  tooooooooo many snaps**[/COLOR]_
  ID-24: **swap**-1 size: **8.22 GiB** used: 657.2 MiB (7.8%) fs: swap 
  dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 41.0 C mobo: N/A gpu: radeon temp: 22 C 
  Fan Speeds (RPM): N/A 
Processes:
  CPU top: 5 
  1: **cpu: 30.1% command: baloo_file_extractor** pid: 3133 
  mem: 7509.5 MiB (50.2%) 
  2: cpu: 7.5% command: chrome pid: 17480 mem: 602.3 MiB (4.0%) 
  3: cpu: 2.5% command: chrome pid: 4563 mem: 218.8 MiB (1.4%) 
  4: cpu: 1.9% command: gnome-shell pid: 2586 mem: 179.9 MiB (1.2%) 
  5: cpu: 1.9% command: chrome pid: 4644 mem: 114.0 MiB (0.7%) 
  Memory top: 5 
  1: mem: **7509.5 MiB (50.2%) command: baloo_file_extractor** pid: 3133 
  cpu: 30.1% 
  2: mem: 653.2 MiB (4.3%) command: **tracker-extract** pid: 1671 cpu: 1.0% 
  3: mem: 602.3 MiB (4.0%) command: **chrome** pid: 17480 cpu: 7.5% 
  4: mem: 218.8 MiB (1.4%) command: chrome pid: 4563 cpu: 2.5% 
  5: mem: 179.9 MiB (1.2%) command: gnome-shell pid: 2586 cpu: 1.9% 
Info:
  Processes: 279 Uptime: 4h 26m Memory: 14.60 GiB used: 6.69 GiB (45.8%) 
  Init: systemd v: 245 runlevel: 5 default: 2 Compilers: gcc: 9.3.0 alt: 7/9 
  Shell: bash v: 5.0.17 running in: gnome-terminal inxi: 3.0.38

```

This is the top issue from the data above:
[B]baloo_file_extractor is using 50% of the RAM and 30% of the CPU.
[https://askubuntu.com/questions/1068788/is-it-safe-to-disable-baloo-file-extractor](https://askubuntu.com/questions/1068788/is-it-safe-to-disable-baloo-file-extractor)
[/B]

I'd rethink using Google-Chrome and loading so many snap packages.  Snaps are slower to load, take up boot time, cruft up the system - look at 'df -hT' output too see all the 'loop' stuff that was added by snaps, uses way too much RAM and disk storage, and if you work in a team, data files outside /home/{userid} aren't accessible.  I avoid snaps.  Snaps update like Win10 - you don't get to choose when a new version is installed and 3 copies are retained - to was storage on your SSD in /var/lib/snapd/snaps/  Typically, a program that needs 33MB will pull a snap that is 3-10x that size, since dependencies are included.  I'm not fan of snaps, mainly because these things:
* bloat RAM use, storage abuse
* Constraints are mandatory with no local control over where the programs can access.
There are other packing options - AppImage and Flatpak which don't have the mandatory constraints, but all the bloat. ;)

A10-7700K has a passmark of only 3200 - [https://www.cpubenchmark.net/cpu.php?cpu=AMD+A10-7700K+APU&id=2146](https://www.cpubenchmark.net/cpu.php?cpu=AMD+A10-7700K+APU&id=2146)
That's a lower-end desktop by the standards today.  Sorta like a Core i3 from 2015 (I have a 2015 chromebook w/ 2000 passmarks and a  $305 2018 laptop with 6100 passmarks).  Running Gnome3 + gnome-shell on the A10 system is going to use more CPU/RAM than I'd like.  I'd definitely switch to a lighter DE or no DE if it was me. But if you can live with the slower machine from the "cheese" in the GUI, fine.

/ is a little large.  I keep mine at 25G or less, so that OS backups are faster, easier and smaller. If I need to wipe the OS and start over from backups, this is extremely handy. Takes less than 30 min - including the 15 min for a fresh install.  If you've ever troubleshot anything for longer than 30 minutes, wouldn't knowing that you could return to last night's backup set in 30 min or less be handy?  Anyways, 100G isn't THAT bad, just something to consider in the future.

swap partition is too large, IMHO.  Anything over 4G is only desired when there are specific requirements or you don't mind a slow system.  There are many opinions on this. May want to research swap file/partition size threads in these forums to get some other opinions. The purpose of swap is to provide "slow" feedback to the user when all RAM use begins getting tight so the users can take steps to reduce RAM use.

The file systems seem fine, though I would have selected a different SSD and wouldn't touch Seagate anything. Seagate HDDs between about 600GB and 7.99TB have a poor history. 8TB+ seagate HDDs are in-line with other vendor storage for lifespans. The Toshiba is about average for HDD.  BTW, on those data-only ext4 partitions, you might want to reduce the number of reserved blocks from the 5% default. Don't do that on any OS partitions, ever, but for end-user storage, especially with TB+ HDDs, reserving 5% for root process needs is excessive.  Use **tune2fs** to modify that. I don't think the file system even needs to be umounted to make the change.  For data partitions, I set it to 0 blocks reserved.

System temps seem fine.

Helpful?

---

### Post by TheFu on 2020-08-12
> **ajs37 said:**
> I end up with "you have held broken packages" error message - I don't know how to get around this error. I'm not sure how to autoclean or autoremove stuff

```
sudo apt autoremove
sudo apt autoclean
```

If you have broken packages that are held, you probably installed a .deb file directly.  Don't do that. If that broken package is holding some other libraries back, those other libraries will never be updated, and security holes are likely.  Stay with packages, preferably non-snap packages, installed using APT (any of the front-ends are fine - apt, apt-get, aptitude, synaptic), be very careful adding PPAs to your system. Only ppa-add-repo from 100% trusted sources, like a PPA provided by the original project team, not some 3rd party guy working in his basement, alone.  Definitely avoid those pre-built installs claiming to make it 1-click for some complex server stuff - like wordpress or zimbra. Bitnami is one of those, but there are 100s of them now, like Turnkey. New server admins often use those pre-packaged setups without looking at what other stuff is included.

To fix a broken package would depend on the exact package and how it was installed.  First, I'd use synaptic or aptitude which have built-in "fix broken packages" options.  Then I'd look closely at the errors, if those tools don't fix it.  Take the resulting error text, and google it (remove system-specific terms like hostnames, timestamps, memory locations), keep the program name. What does google say?

---

### Post by ajs37 on 2020-08-12
very helpful, thanks! 

[COLOR=#242729][FONT=Consolas]balooctl disable
[/FONT][/COLOR]this helped a lot - a lot of activity stopped after trying it! 

I can also switch to Firefox or Brave and see if that improves things

I know the motherboard and processor are a little old (5+ years) but I'm not too bothered about speed ATM - maybe upgrade that later.....

I'll investigate the swap partitions after next week (away on holiday next week) and see what difference that makes

Having said that, at the moment the disk activity has stopped, so maybe my problem is solved?

I'll let you know how I get on 

Thanks again!

---

### Post by ajs37 on 2020-08-12
thanks - the autoremove and autoclean commands cleared up a fair bit of dead wood (code)

I'll give your suggestions a try and let you know how I gat on in a couple of weeks (away on holiday soon!)

thanks again!

---

### Post by TheFu on 2020-08-12
> **ajs37 said:**
> I can also switch to Firefox or Brave and see if that improves things

I know the motherboard and processor are a little old (5+ years) but I'm not too bothered about speed ATM - maybe upgrade that later.....

I'll investigate the swap partitions after next week (away on holiday next week) and see what difference that makes

Having said that, at the moment the disk activity has stopped, so maybe my problem is solved?

Bloated browsers, all of them, but not using software installed via snap packages will help.

I mentioned the cpu more to recommend dumping gnome3, not any upgrade. xfce, mate, kde, lxqt are all lighter and will be faster on the same hardware. Plus, every release, the gnome guys screw with the interface to make it different, not necessarily better.  I use the same gui I used in 1995 today, after being fed up with bloated guis. No need to learn anything new every 2 yrs.

The swap partition is for the next install. I wouldn't worry about it now. The old rules of thumb that are related to RAM amounts don't apply since systems have GB of RAM now.

---

### Post by ajs37 on 2020-08-13
Thanks - I'll take your advice!

---

### Post by TheFu on 2020-08-13
> thanks - the autoremove and autoclean commands cleared up a fair bit of dead wood (code)
That just cleaned a little storage, not anything related to being slow or using RAM.

With all the snap packages on the system, there may be 3 copies of each.  To see all the snap packages, including the old, unused, versions, run:
```
snap list --all
```
Any of those with 'disabled' on the line are excess, unneeded, unused, just old versions. You can remove them. Snap uses a separate package management solution, outside APT, unfortunately.  You can do this manually or use a little script to make it easier.

---

### Post by dino99 on 2020-08-13
Purging old installed snaps ( to get them loaded quicker)
[https://www.linuxuprising.com/2019/04/how-to-remove-old-snap-versions-to-free.html](https://www.linuxuprising.com/2019/04/how-to-remove-old-snap-versions-to-free.html)

---

### Post by oygle on 2020-10-30
Only yesterday I (finally) got a 20.04.1 clean installation done ( see [https://ubuntuforums.org/showthread.php?t=2452691](https://ubuntuforums.org/showthread.php?t=2452691)  ) . Performance is **very slow** and the light for the HDD is on most of the time. Should I post here or start a new thread ?

---

