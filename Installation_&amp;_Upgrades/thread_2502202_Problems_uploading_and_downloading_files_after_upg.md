---
title: "Problems uploading and downloading files after upgrade"
date: 2024-11-05
forum: Installation &amp; Upgrades
---

### Post by freedom1984 on 2024-11-05
Good morning! Since I ran the command sudo apt-get upgrade -y, I can neither upload nor download files. Current: 24.04.01 LTS When uploading I get the error message that “permission denied”. When downloading, Firefox hangs and has to be closed.
This is very annoying for me right now.
All the pictures from my Myanmar research trip are on the PC. So I can't reinstall it.
At the same time, I can't print my bank statements as a PDF, which would be necessary for applying for social security benefits.

```
System:
  Kernel: 6.8.0-48-generic arch: x86_64 bits: 64
  Desktop: GNOME v: 46.0 Distro: Ubuntu 24.04.1 LTS (Noble Numbat)
Machine:
  Type: Laptop System: LENOVO product: 20C6S09W00 v: ThinkPad Edge E540
    serial: <filter>
  Mobo: LENOVO model: 20C6S09W00 v: 0B98401 WIN serial: <filter>
    UEFI-[Legacy]: LENOVO v: J9ET9DWW (2.23 ) date: 02/04/2016
Battery:
  ID-1: BAT0 charge: 18.1 Wh (98.4%) condition: 18.4/56.2 Wh (32.7%)
CPU:
  Info: quad core model: Intel Core i7-4712MQ bits: 64 type: MT MCP cache:
    L2: 1024 KiB
  Speed (MHz): avg: 2376 min/max: 800/3300 cores: 1: 800 2: 2914 3: 2836
    4: 800 5: 3300 6: 2100 7: 2960 8: 3300
Graphics:
  Device-1: Intel 4th Gen Core Processor Integrated Graphics driver: i915
    v: kernel
  Device-2: Bison Integrated Camera driver: uvcvideo type: USB
  Display: server: X.Org v: 23.2.6 with: Xwayland v: 23.2.6 driver: X:
    loaded: modesetting unloaded: fbdev,vesa dri: crocus gpu: i915
    resolution: 1366x768~60Hz
  API: EGL v: 1.5 drivers: crocus,swrast platforms: x11,surfaceless,device
  API: OpenGL v: 4.6 compat-v: 4.5 vendor: intel mesa v: 24.0.9-0ubuntu0.2
    renderer: Mesa Intel HD Graphics 4600 (HSW GT2)
  API: Vulkan v: 1.3.296 drivers: N/A surfaces: xcb,xlib
Audio:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio
    driver: snd_hda_intel
  Device-2: Intel 8 Series/C220 Series High Definition Audio
    driver: snd_hda_intel
  API: ALSA v: k6.8.0-48-generic status: kernel-api
Network:
  Device-1: Realtek RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet
    driver: r8169
  IF: enp3s0 state: down mac: <filter>
  Device-2: Intel Wireless 7260 driver: iwlwifi
  IF: wlp4s0 state: up mac: <filter>
Bluetooth:
  Device-1: Intel Bluetooth wireless interface driver: btusb type: USB
  Report: hciconfig ID: hci0 state: up address: <filter> bt-v: 4.0
Drives:
  Local Storage: total: 232.89 GiB used: 174.37 GiB (74.9%)
  ID-1: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB
Partition:
  ID-1: / size: 228.17 GiB used: 174.37 GiB (76.4%) fs: ext4 dev: /dev/sda2
Swap:
  ID-1: swap-1 type: file size: 4 GiB used: 0 KiB (0.0%) file: /swap.img
Sensors:
  System Temperatures: cpu: 56.0 C mobo: N/A
  Fan Speeds (rpm): cpu: 0 fan-2: 0
Info:
  Memory: total: 8 GiB available: 7.47 GiB used: 3.05 GiB (40.8%) igpu: 32 MiB
  Processes: 284 Uptime: 2h 57m Shell: Sudo inxi: 3.3.34
```


1: the error has only now occurred completely independently of Bios settings. Assuming that does not apply: the update or upgrade has problems with these settings. 2. download: For example, a notice of termination from the Federal Employment Agency homepage into the download folder. Upload: For example, a screen screenshot on Twitter

"/home/aporie/Bilder/Bildschirmfotos" "/home/aporie/Downloads"

```
aporie@Dissonanz:~$ sudo snap list -all
[sudo] Passwort für aporie: 
Fehler: unknown flag `a'
aporie@Dissonanz:~$ snap list -all
Fehler: unknown flag `a'
aporie@Dissonanz:~$ snap list
Name                       Version                      Revision  Tracking            Herausgeber      Hinweise
bare                       1.0                          5         latest/stable       canonical&#10003;       base
chromium-ffmpeg            116575-116569-115541-115016  58        latest/stable       canonical&#10003;       -
core                       16-2.61.4-20240607           17200     latest/stable       canonical&#10003;       core
core18                     20240920                     2846      latest/stable       canonical&#10003;       base
core20                     20240911                     2434      latest/stable       canonical&#10003;       base
core22                     20241001                     1663      latest/stable       canonical&#10003;       base
core24                     20240920                     609       latest/stable       canonical&#10003;       base
firefox                    132.0-1                      5187      latest/stable       mozilla&#10003;         -
firmware-updater           0+git.7983059                147       latest/stable/…     canonical&#10003;       -
gaming-graphics-core22     24.2.3~kisak1~j              184       kisak-fresh/stable  canonical&#10003;       -
gnome-3-38-2004            0+git.efb213a                143       latest/stable       canonical&#10003;       -
gnome-42-2204              0+git.510a601                176       latest/stable/…     canonical&#10003;       -
gnome-46-2404              0+git.5d6be1b                48        latest/stable       canonical&#10003;       -
gnome-chess                46.0                         89        latest/stable       ken-vandine&#10026;     -
gtk-common-themes          0.1-81-g442e511              1535      latest/stable/…     canonical&#10003;       -
gtk2-common-themes         0.1                          13        latest/stable       canonical&#10003;       -
mesa-2404                  24.0.9                       143       latest/stable       canonical&#10003;       -
opera                      114.0.5282.144               341       latest/stable       opera-software&#10003;  -
pdfarranger                1.10.1                       33        latest/stable       soumyadghosh&#10026;    -
snap-store                 0+git.4fcd62b7               1218      latest/stable/…     canonical&#10003;       -
snapd                      2.63                         21759     latest/stable       canonical&#10003;       snapd
snapd-desktop-integration  0.9                          253       latest/stable/…     canonical&#10003;       -
steam                      1.0.0.81                     206       latest/stable       canonical&#10003;       -
aporie@Dissonanz:~$ snap list all
Fehler: keine passenden Snaps installiert
aporie@Dissonanz:~$ snap list -all
Fehler: unknown flag `a'
```[/CODE]

---

### Post by grahammechanical on 2024-11-05
Why did you use the -y switch when running apt-get upgrade? This is what it does:

> y, --yes, --assume-yes
           Automatic yes to prompts; assume "yes" as answer to all prompts and run non-interactively. If an undesirable situation, such as changing a held package, trying to install an
           unauthenticated package or removing an essential package occurs then apt-get will abort. Configuration Item: APT::Get::Assume-Yes.

That is from the apt-get man (manual) page.

By the way, Your Firefox is a snap packaged application. Snaps do not get refreshed (upgraded) when we run apt upgrade or apt-get upgrade. So, I am assuming that Firefox has not been altered by the apt-get upgrade -y command.

Have you altered the settings in Firefox? What do you see when you run these commands?

```
sudo apt update
sudo apt upgrade
```

If the OS updates the software repositories without any problems and can then upgrade any installed applications then the problem is not with the OS. We have to look elsewhere. Do you have these problems when you use the Opera browser?

How are you connecting to the Internet Service Provider (ISP)? I had lots of problems with downloading and with connections to certain web sites not progressing because there was interference on the telephone landline that I used to connect to the ISP.

Regards

---

### Post by freedom1984 on 2024-11-05
Yes, Firefox hangs during the download and must be closed.

When uploading, there is an error message that access is denied.

Under Opera, downloads are blocked or load with 0 bytes and a question mark.

I don't know the settings of the router, as I just moved into the shared   flat, but a few days ago everything worked perfectly here.



```
aporie@Dissonanz:~$ sudo apt update
[sudo] Passwort für aporie: 
OK:1 http://archive.ubuntu.com/ubuntu noble InRelease
Holen:2 http://archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]      
Holen:3 http://archive.ubuntu.com/ubuntu noble-backports InRelease [126 kB]    
Holen:4 http://archive.ubuntu.com/ubuntu noble-updates/main i386 Packages [324 kB]
Holen:5 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages [621 kB]
Holen:6 http://archive.ubuntu.com/ubuntu noble-updates/main Translation-en [150 kB]
Holen:7 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 Components [114 kB]
Holen:8 http://archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Packages [420 kB]
Holen:9 http://archive.ubuntu.com/ubuntu noble-updates/restricted Translation-en [80,4 kB]
Holen:10 http://archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Components [212 B]
Holen:11 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 Packages [710 kB]
Holen:12 http://security.ubuntu.com/ubuntu noble-security InRelease [126 kB]   
Holen:13 http://archive.ubuntu.com/ubuntu noble-updates/universe i386 Packages [439 kB]
Holen:14 http://archive.ubuntu.com/ubuntu noble-updates/universe Translation-en [211 kB]
Holen:15 http://archive.ubuntu.com/ubuntu noble-updates/universe amd64 Components [305 kB]
OK:16 https://packages.lunarg.com/vulkan noble InRelease                       
Holen:17 http://archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 Components [940 B]
Holen:18 http://archive.ubuntu.com/ubuntu noble-backports/main amd64 Components [208 B]
Holen:19 http://archive.ubuntu.com/ubuntu noble-backports/restricted amd64 Components [212 B]
Holen:20 http://archive.ubuntu.com/ubuntu noble-backports/universe amd64 Components [20,9 kB]
Holen:21 http://archive.ubuntu.com/ubuntu noble-backports/multiverse amd64 Components [212 B]
Holen:22 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages [445 kB]
Holen:23 http://security.ubuntu.com/ubuntu noble-security/main i386 Packages [196 kB]
Holen:24 http://security.ubuntu.com/ubuntu noble-security/main Translation-en [95,3 kB]
Holen:25 http://security.ubuntu.com/ubuntu noble-security/main amd64 Components [7.228 B]
Holen:26 http://security.ubuntu.com/ubuntu noble-security/restricted amd64 Components [212 B]
Holen:27 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Packages [557 kB]
Holen:28 http://security.ubuntu.com/ubuntu noble-security/universe i386 Packages [354 kB]
Holen:29 http://security.ubuntu.com/ubuntu noble-security/universe Translation-en [149 kB]
Holen:30 http://security.ubuntu.com/ubuntu noble-security/universe amd64 Components [51,9 kB]
Holen:31 http://security.ubuntu.com/ubuntu noble-security/multiverse amd64 Components [208 B]
Es wurden 5.631 kB in 5 s geholt (1.194 kB/s).                     
Paketlisten werden gelesen… Fertig
Abhängigkeitsbaum wird aufgebaut… Fertig
Statusinformationen werden eingelesen… Fertig
Aktualisierung für 8 Pakete verfügbar. Führen Sie »apt list --upgradable« aus, um sie anzuzeigen.
aporie@Dissonanz:~$ sudo apt upgrade
Paketlisten werden gelesen… Fertig
Abhängigkeitsbaum wird aufgebaut… Fertig
Statusinformationen werden eingelesen… Fertig
Paketaktualisierung (Upgrade) wird berechnet… Fertig
Folgende Aktualisierungen wurden aufgrund von gestaffelter Auslieferung vorerst zurückgehalten:
  file-roller python3-distupgrade shotwell shotwell-common
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
Die folgenden Pakete werden aktualisiert (Upgrade):
  libmpg123-0t64 libopenjp2-7
2 aktualisiert, 0 neu installiert, 0 zu entfernen und 6 nicht aktualisiert.
2 standard LTS security updates
Es müssen noch 169 kB von 343 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 0 B Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] J
Holen:1 http://archive.ubuntu.com/ubuntu noble-updates/main amd64 libmpg123-0t64 amd64 1.32.5-1ubuntu1.1 [169 kB]
Es wurden 169 kB in 2 s geholt (74,3 kB/s).
(Lese Datenbank ... 208944 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Entpacken von .../libmpg123-0t64_1.32.5-1ubuntu1.1_amd64.deb ..
.
Entpacken von libmpg123-0t64:amd64 (1.32.5-1ubuntu1.1) über (1.32.5-1ubuntu1) ..
.
Vorbereitung zum Entpacken von .../libopenjp2-7_2.5.0-2ubuntu0.2_amd64.deb ...
Entpacken von libopenjp2-7:amd64 (2.5.0-2ubuntu0.2) über (2.5.0-2ubuntu0.1) ...
libmpg123-0t64:amd64 (1.32.5-1ubuntu1.1) wird eingerichtet ...
libopenjp2-7:amd64 (2.5.0-2ubuntu0.2) wird eingerichtet ...
Trigger für libc-bin (2.39-0ubuntu8.3) werden verarbeitet ...
aporie@Dissonanz:~$ 

```

---

