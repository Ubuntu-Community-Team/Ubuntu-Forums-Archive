---
title: "Ubuntu 22.04 take 5-10 minutes  to launch to the desktop"
date: 2024-02-08
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2024-02-08
ubuntu 22.04 was working few day ago but lately it has started to take long long time to launch the desktop 5-10 minutes 
it takes 1 minutes just to open the terminal when it has launched
Now firefox won't launch 
Gtk-Message: 08:08:29.873: Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.
Error: cannot open display: :0
 any suggestion ?

Cheers

---

### Post by ajgreeny on 2024-02-08
What hardware do you have?
As a start please run command ```
inxi -Fzx
```and copy back here the output using code tags.

---

### Post by hoboy on 2024-02-08
```
inxi -Fzx
System:
  Kernel: 6.5.0-17-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop Mobo: ASUSTeK model: PRIME H310M-K v: Rev X.0x
    serial: <superuser required> UEFI: American Megatrends v: 2012
    date: 01/18/2019
CPU:
  Info: 8-core model: Intel Core i7-9700K bits: 64 type: MCP
    arch: Coffee Lake rev: C cache: L1: 512 KiB L2: 2 MiB L3: 12 MiB
  Speed (MHz): avg: 800 min/max: 800/4900 cores: 1: 800 2: 800 3: 800
    4: 800 5: 800 6: 800 7: 800 8: 800 bogomips: 57600
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel CoffeeLake-S GT2 [UHD Graphics 630] vendor: ASUSTeK
    driver: N/A bus-ID: 00:02.0
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: vesa
    unloaded: fbdev,modesetting gpu: N/A resolution: 1920x1080~77Hz
  OpenGL: renderer: llvmpipe (LLVM 15.0.7 256 bits)
    v: 4.5 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes
Audio:
  Device-1: Intel Cannon Lake PCH cAVS vendor: ASUSTeK driver: snd_hda_intel
    v: kernel bus-ID: 00:1f.3
  Device-2: Sennheiser Headset [PC 8] type: USB
    driver: hid-generic,snd-usb-audio,usbhid bus-ID: 1-9:4
  Sound Server-1: ALSA v: k6.5.0-17-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8192CE PCIe Wireless Network Adapter vendor: ASUSTeK
    driver: rtl8192ce v: kernel port: 4000 bus-ID: 01:00.0
  IF: wlp1s0 state: down mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: ASUSTeK PRIME B450M-A driver: r8169 v: kernel port: 3000
    bus-ID: 02:00.0
  IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
  IF-ID-1: anbox0 state: down mac: <filter>
  IF-ID-2: cali2c7985c94cd state: up speed: 10000 Mbps duplex: full
    mac: <filter>
  IF-ID-3: cali34aae558806 state: up speed: 10000 Mbps duplex: full
    mac: <filter>
  IF-ID-4: docker0 state: down mac: <filter>
  IF-ID-5: lxcbr0 state: down mac: <filter>
  IF-ID-6: vxlan.calico state: unknown speed: -1 duplex: unknown
    mac: <filter>
Drives:
  Local Storage: total: 1.35 TiB used: 137.97 GiB (10.0%)
  ID-1: /dev/sda vendor: Gigabyte model: GP-GSTFS31480GNTD size: 447.13 GiB
  ID-2: /dev/sdb vendor: Toshiba model: HDWD110 size: 931.51 GiB
Partition:
  ID-1: / size: 915.32 GiB used: 137.97 GiB (15.1%) fs: ext4 dev: /dev/sdb2
  ID-2: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 12 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 27.8 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 404 Uptime: 1h 25m Memory: 15.46 GiB used: 8.63 GiB (55.8%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 2692 Shell: Bash
  v: 5.1.16 inxi: 3.3.13
```

---

### Post by Rubi1200 on 2024-02-08
Very hard to read and interpret output that is not wrapped in code tags.

Please edit your post and click on Go Advanced. Highlight the output with Ctrl+A or the mouse and then click on the # icon on the ribbon to wrap with the code tag.

Thanks.

---

### Post by corradoventu on 2024-02-08
Try to start with wayland session instead x11

---

### Post by hoboy on 2024-02-08
Try to start with wayland session instead x11

How can I do that ?

---

### Post by hoboy on 2024-02-08
done .. changed to wayland

 inxi -Fzx
```
System:
  Kernel: 6.5.0-17-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop Mobo: ASUSTeK model: PRIME H310M-K v: Rev X.0x
    serial: <superuser required> UEFI: American Megatrends v: 2012
    date: 01/18/2019
CPU:
  Info: 8-core model: Intel Core i7-9700K bits: 64 type: MCP
    arch: Coffee Lake rev: C cache: L1: 512 KiB L2: 2 MiB L3: 12 MiB
  Speed (MHz): avg: 2675 high: 2835 min/max: 800/4900 cores: 1: 2645
    2: 2835 3: 2642 4: 2703 5: 2641 6: 2647 7: 2638 8: 2650 bogomips: 57600
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel CoffeeLake-S GT2 [UHD Graphics 630] vendor: ASUSTeK
    driver: i915 v: kernel bus-ID: 00:02.0
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: X: loaded: vesa unloaded: fbdev,modesetting
    gpu: i915 resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel UHD Graphics 630 (CFL GT2)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes
Audio:
  Device-1: Intel Cannon Lake PCH cAVS vendor: ASUSTeK driver: snd_hda_intel
    v: kernel bus-ID: 00:1f.3
  Device-2: Sennheiser Headset [PC 8] type: USB
    driver: hid-generic,snd-usb-audio,usbhid bus-ID: 1-9:4
  Sound Server-1: ALSA v: k6.5.0-17-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8192CE PCIe Wireless Network Adapter vendor: ASUSTeK
    driver: rtl8192ce v: kernel port: 4000 bus-ID: 01:00.0
  IF: wlp1s0 state: down mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: ASUSTeK PRIME B450M-A driver: r8169 v: kernel port: 3000
    bus-ID: 02:00.0
  IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
  IF-ID-1: anbox0 state: down mac: <filter>
  IF-ID-2: cali2c7985c94cd state: up speed: 10000 Mbps duplex: full
    mac: <filter>
  IF-ID-3: cali34aae558806 state: up speed: 10000 Mbps duplex: full
    mac: <filter>
  IF-ID-4: docker0 state: down mac: <filter>
  IF-ID-5: lxcbr0 state: down mac: <filter>
  IF-ID-6: vxlan.calico state: unknown speed: -1 duplex: unknown
    mac: <filter>
Drives:
  Local Storage: total: 1.35 TiB used: 137.55 GiB (10.0%)
  ID-1: /dev/sda vendor: Gigabyte model: GP-GSTFS31480GNTD size: 447.13 GiB
  ID-2: /dev/sdb vendor: Toshiba model: HDWD110 size: 931.51 GiB
Partition:
  ID-1: / size: 915.32 GiB used: 137.54 GiB (15.0%) fs: ext4 dev: /dev/sdb2
  ID-2: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/sda1
Swap:[CODE]
```
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 27.8 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 349 Uptime: 24m Memory: 15.46 GiB used: 5.73 GiB (37.1%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 2672 Shell: Bash
  v: 5.1.16 inxi: 3.3.13[/code]

---

### Post by ajgreeny on 2024-02-08
Did choosing x11 solve the problem?

If so please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction.
It is a great help to other users searching the forum.

---

### Post by hoboy on 2024-02-08
> **ajgreeny said:**
> Did choosing x11 solve the problem?

If so please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction.
It is a great help to other users searching the forum.

I have put the output of  inxi -Fzx
```
System:
  Kernel: 6.5.0-17-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop Mobo: ASUSTeK model: PRIME H310M-K v: Rev X.0x
    serial: <superuser required> UEFI: American Megatrends v: 2012
    date: 01/18/2019
CPU:
  Info: 8-core model: Intel Core i7-9700K bits: 64 type: MCP
    arch: Coffee Lake rev: C cache: L1: 512 KiB L2: 2 MiB L3: 12 MiB
  Speed (MHz): avg: 2675 high: 2835 min/max: 800/4900 cores: 1: 2645
    2: 2835 3: 2642 4: 2703 5: 2641 6: 2647 7: 2638 8: 2650 bogomips: 57600
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel CoffeeLake-S GT2 [UHD Graphics 630] vendor: ASUSTeK
    driver: i915 v: kernel bus-ID: 00:02.0
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: X: loaded: vesa unloaded: fbdev,modesetting
    gpu: i915 resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel UHD Graphics 630 (CFL GT2)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes
Audio:
  Device-1: Intel Cannon Lake PCH cAVS vendor: ASUSTeK driver: snd_hda_intel
    v: kernel bus-ID: 00:1f.3
  Device-2: Sennheiser Headset [PC 8] type: USB
    driver: hid-generic,snd-usb-audio,usbhid bus-ID: 1-9:4
  Sound Server-1: ALSA v: k6.5.0-17-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8192CE PCIe Wireless Network Adapter vendor: ASUSTeK
    driver: rtl8192ce v: kernel port: 4000 bus-ID: 01:00.0
  IF: wlp1s0 state: down mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: ASUSTeK PRIME B450M-A driver: r8169 v: kernel port: 3000
    bus-ID: 02:00.0
  IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
  IF-ID-1: anbox0 state: down mac: <filter>
  IF-ID-2: cali2c7985c94cd state: up speed: 10000 Mbps duplex: full
    mac: <filter>
  IF-ID-3: cali34aae558806 state: up speed: 10000 Mbps duplex: full
    mac: <filter>
  IF-ID-4: docker0 state: down mac: <filter>
  IF-ID-5: lxcbr0 state: down mac: <filter>
  IF-ID-6: vxlan.calico state: unknown speed: -1 duplex: unknown
    mac: <filter>
Drives:
  Local Storage: total: 1.35 TiB used: 137.55 GiB (10.0%)
  ID-1: /dev/sda vendor: Gigabyte model: GP-GSTFS31480GNTD size: 447.13 GiB
  ID-2: /dev/sdb vendor: Toshiba model: HDWD110 size: 931.51 GiB
Partition:
  ID-1: / size: 915.32 GiB used: 137.54 GiB (15.0%) fs: ext4 dev: /dev/sdb2
  ID-2: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 27.8 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 349 Uptime: 24m Memory: 15.46 GiB used: 5.73 GiB (37.1%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 2672 Shell: Bash
  v: 5.1.16 inxi: 3.3.13
```

---

### Post by ubfan1 on 2024-02-08
The first page of output of systemd-analyze blame  would indicate what's taking the time.  Probably NetworkManager. If so see various askubuntu answers like 1009999.

---

### Post by corradoventu on 2024-02-08
Did choosing Wayland solve the problem?

---

### Post by hoboy on 2024-02-08
No it didn't it is the same

---

### Post by ajgreeny on 2024-02-08
As has already been suggested let's see the output of ```
systemd-analyze blame
```
Please use code tags for all terminal output when you post it back here.
See my signature below for a **Code-Tags** how-to.

---

### Post by hoboy on 2024-02-09
> **ajgreeny said:**
> As has already been suggested let's see the output of ```
systemd-analyze blame
```
Please use code tags for all terminal output when you post it back here.
See my signature below for a **Code-Tags** how-to.
```
1min 37.177s docker.service
1min 36.402s ua-timer.service
1min 13.680s plymouth-quit-wait.service
 1min 5.731s e2scrub_reap.service
  1min 711ms apt-daily-upgrade.service
     53.392s preload.service
     47.165s podman-restart.service
     39.898s snap.docker.nvidia-container-toolkit.service
     38.275s snapd.service
     36.135s systemd-journal-flush.service
     27.505s [email]tor@default.servic[/email]e
     27.400s containerd.service
     26.030s snap.microk8s.daemon-containerd.service
     24.759s NetworkManager-wait-online.service
     20.958s [email]user@1000.servic[/email]e
     20.826s dev-loop59.device
     19.812s dev-sdb2.device
     18.530s dev-loop57.device
     18.109s dev-loop51.device
     17.696s dev-loop34.device
     17.235s dev-loop29.device
     17.017s dev-loop52.device
     16.976s logrotate.service
     16.615s dev-loop60.device
     16.507s dev-loop53.device
     16.474s dev-loop56.device
     16.443s dev-loop55.device
     16.426s dev-loop54.device
     16.261s dev-loop58.device
     16.122s dev-loop50.device
     16.007s dev-loop48.device
     16.000s dev-loop47.device
     15.904s dev-loop46.device
     15.859s dev-loop40.device
     15.760s dev-loop44.device
     15.745s dev-loop30.device
     15.632s dev-loop45.device
     15.615s dev-loop42.device
     15.548s dev-loop32.device
     15.538s dev-loop41.device
     15.314s dev-loop43.device
     15.128s dev-loop28.device
     15.035s udisks2.service
     14.456s dev-loop26.device
     14.332s dev-loop33.device
     14.175s dev-loop49.device
     13.673s ufw.service
     13.410s dev-loop38.device
     13.391s dev-loop31.device
     13.268s dev-loop39.device
     13.221s dev-loop23.device
     13.176s dev-loop35.device
     13.171s dev-loop36.device
     13.077s dev-loop37.device
     12.889s accounts-daemon.service
     12.516s dev-loop20.device
     12.319s apparmor.service
     12.261s apport-autoreport.service
     11.856s dev-loop18.device
     11.613s dev-loop21.device
     11.486s dev-loop19.device
     11.485s dev-loop24.device
     11.476s networkd-dispatcher.service
     11.426s dev-loop27.device
     11.211s dev-loop17.device
     10.940s dev-loop15.device
     10.786s dev-loop13.device
     10.712s ModemManager.service
     10.711s dev-loop22.device
     10.681s dev-loop8.device
     10.436s dev-loop16.device
     10.422s dev-loop14.device
     10.175s dev-loop25.device
     10.016s gdm.service
      9.990s dev-loop11.device
      9.875s dev-loop12.device
      9.869s dev-loop9.device
      9.427s cups.service
      9.281s power-profiles-daemon.service
      9.175s polkit.service
      8.776s dev-loop10.device
      7.423s systemd-rfkill.service
      7.045s dev-loop0.device
      6.952s lxc-net.service
      6.281s avahi-daemon.service
      6.254s NetworkManager.service
      6.154s fwupd-refresh.service
      5.976s update-notifier-download.service
      5.844s switcheroo-control.service
      5.841s systemd-logind.service
      5.839s wpa_supplicant.service
      5.447s fwupd.service
      4.932s lxc.service
      4.832s snapd.apparmor.service
      4.618s dev-loop7.device
      4.483s dev-loop6.device
      4.439s dev-loop3.device
      4.044s dev-loop5.device
      3.652s apport.service
      3.368s dev-loop4.device
      3.333s qemu-kvm.service
      3.323s systemd-modules-load.service
      3.284s dev-loop1.device
      3.007s colord.service
      2.442s [email]systemd-fsck@dev-disk-by\x2duuid-1497\x2d1BC9.servic[/email]e
      2.424s dev-loop2.device
      2.411s packagekit.service
      2.399s rsyslog.service
      2.107s gpu-manager.service
      2.060s systemd-udevd.service
      1.757s plymouth-start.service
      1.677s grub-common.service
      1.622s upower.service
      1.507s podman.service
      1.472s snap-anbox-186.mount
      1.426s systemd-binfmt.service
      1.422s secureboot-db.service
      1.381s run-qemu.mount
      1.324s snap-amazon\x2dssm\x2dagent-7628.mount
      1.237s snap-core20-2105.mount
      1.225s snap-bare-5.mount
      1.190s snap-firefox-3779.mount
      1.190s snap-core20-2015.mount
      1.180s snap-beekeeper\x2dstudio-244.mount
      1.170s systemd-oomd.service
      1.139s snap-canonical\x2dlivepatch-246.mount
      1.133s snap-canonical\x2dlivepatch-264.mount
      1.128s snap-google\x2dcloud\x2dcli-211.mount
      1.115s kerneloops.service
      1.100s snap-chromium-2738.mount
      1.085s snap-chromium-2742.mount
      1.065s snap-core-16202.mount
      1.056s snap-core-16574.mount
      1.037s snap-core18-2796.mount
      1.032s snap-core18-2812.mount
      1.021s snap-emacs-2307.mount
       996ms snap-core22-1033.mount
       988ms snap-core22-864.mount
       979ms systemd-resolved.service
       969ms snap-docker-2904.mount
       964ms snap-grafana-36.mount
       962ms snap-docker-2915.mount
       938ms snap-firefox-3728.mount
       922ms lm-sensors.service
       909ms snap-gaming\x2dgraphics\x2dcore22-154.mount
       895ms snap-gnome\x2d3\x2d28\x2d1804-198.mount
       893ms tor.service
       881ms snap-gnome\x2d3\x2d38\x2d2004-143.mount
       867ms snap-gnome\x2d42\x2d2204-120.mount
       862ms snap-gnome\x2d42\x2d2204-141.mount
       843ms snap-gnome\x2dsystem\x2dmonitor-186.mount
       826ms systemd-random-seed.service
       822ms systemd-tmpfiles-setup.service
       818ms snap-google\x2dcloud\x2dcli-213.mount
       807ms snap-gradle-134.mount
       803ms snap-kf5\x2d5\x2d111\x2dqt\x2d5\x2d15\x2d11\x2dcore22-7.mount
       780ms systemd-sysusers.service
       771ms snap-gtk\x2dcommon\x2dthemes-1535.mount
       753ms snap-jenkins-4620.mount
       751ms keyboard-setup.service
       751ms systemd-udev-trigger.service
       745ms snap-jenkins-4623.mount
       723ms snap-kube\x2dapiserver-3549.mount
       722ms geoclue.service
       708ms snap-kube\x2dcontroller\x2dmanager-3318.mount
       697ms snap-kube\x2dscheduler-3195.mount
       686ms snap-kubeadm-3224.mount
       676ms snap-kubelet-3151.mount
       663ms snap-marktext-9.mount
       657ms snap-wine\x2dplatform\x2druntime\x2dcore20-99.mount
       651ms snap-microk8s-6089.mount
       643ms plymouth-read-write.service
       638ms snap-node-8169.mount
       634ms snap-whatsapp\x2dfor\x2dlinux-58.mount
       614ms snap-notepad\x2dplus\x2dplus-397.mount
       614ms console-setup.service
       606ms systemd-sysctl.service
       603ms snap-office365webdesktop-5.mount
       587ms snap-powershell-262.mount
       578ms snap-snap\x2dstore-959.mount
       577ms grub-initrd-fallback.service
       566ms snap-snapd-20290.mount
       557ms snap-sublime\x2dtext-137.mount
       551ms snap-snapd-20671.mount
       534ms snap-snapd\x2ddesktop\x2dintegration-83.mount
       530ms systemd-journald.service
       503ms snap-steam-171.mount
       480ms snap-teams\x2dfor\x2dlinux-521.mount
       473ms snap-teams\x2dfor\x2dlinux-523.mount
       465ms systemd-tmpfiles-setup-dev.service
       460ms snap-tempest-191.mount
       456ms snap-wine\x2dplatform\x2druntime\x2dcore20-98.mount
       448ms snap-termius\x2dapp-180.mount
       443ms snap-termius\x2dapp-181.mount
       419ms [email]user-runtime-dir@1000.servic[/email]e
       401ms [email]modprobe@drm.servic[/email]e
       399ms snap-wine\x2dplatform\x2d7\x2ddevel\x2dcore20-24.mount
       391ms swapfile.swap
       321ms boot-efi.mount
       316ms podman-auto-update.service
       297ms snap.kube-apiserver.daemon.service
       289ms proc-sys-fs-binfmt_misc.mount
       274ms snap.kube-scheduler.daemon.service
       222ms systemd-timesyncd.service
       212ms setvtrgb.service
       199ms systemd-remount-fs.service
       183ms rtkit-daemon.service
       161ms dev-hugepages.mount
       158ms dev-mqueue.mount
       154ms sys-kernel-debug.mount
       150ms sys-kernel-tracing.mount
       144ms snap.kube-controller-manager.daemon.service
       134ms [email]modprobe@configfs.servic[/email]e
       134ms [email]modprobe@fuse.servic[/email]e
       134ms kmod-static-nodes.service
       131ms systemd-user-sessions.service
       123ms systemd-update-utmp.service
        67ms systemd-tmpfiles-clean.service
        62ms snap-kube\x2dcontroller\x2dmanager-3329.mount
        31ms alsa-restore.service
        28ms motd-news.service
        24ms openvpn.service
        24ms var-snap-firefox-common-host\x2dhunspell.mount
        18ms snap-kube\x2dscheduler-3214.mount
        17ms snap-kubelet-3163.mount
        16ms docker.socket
        15ms snap-kubeadm-3237.mount
        14ms dev-loop66.device
        10ms snap-kube\x2dapiserver-3563.mount
         7ms dev-loop65.device
         6ms dev-loop62.device
         5ms sys-fs-fuse-connections.mount
         4ms systemd-update-utmp-runlevel.service
         2ms sys-kernel-config.mount
         1ms [email]modprobe@efi_pstore.servic[/email]e
         1ms snapd.socket
         1ms dev-loop64.device
       773us dev-loop63.device
```

---

### Post by ubfan1 on 2024-02-09
So many slow items.  Did you ever look at the SMART data for your disks?  package smartmontools, then run smartctl -a <dev>

---

### Post by corradoventu on 2024-02-10
mounting all those snap devices takes a lot of time
let's see the output of 
```
systemd-analyze critical-chain --no-pager
```

---

### Post by ajgreeny on 2024-02-10
You  have marked this as SOLVED now which is good to hear, but please do tell us the final solution and what output  you saw from that **critical-chain --no-pager ** command.

---

### Post by MAFoElffen on 2024-02-10
I'm curious as well.

If it was waiting on NetworkManager, then adding "optional: yes" to the responsible /etc/netplan/00-network-manager-config.all.yaml file would fix that part, but he didn't get far enough for someone to pick up  on it to recommend that. I'm confused in how, all of a sudden he is now "Solved"???

---

### Post by hoboy on 2024-02-11
I reinstall ubuntu from scratch format the rubbish.
now have clean installation

---

