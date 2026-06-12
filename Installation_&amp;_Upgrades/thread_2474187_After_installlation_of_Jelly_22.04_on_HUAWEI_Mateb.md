---
title: "After installlation of Jelly 22.04 on HUAWEI Matebook D15 I get no sound or mike"
date: 2022-04-23
forum: Installation &amp; Upgrades
---

### Post by aiwayfr89 on 2022-04-23
I just come to **install jelly** on my HUAWEI Matebook D15 but unfortunately **I get no sound.**
I observe that it is a** dummy output** that has been installed.
Here are my observations :
[COLOR=#ff0000]HUAWEI Matebook D15(Core  Intel I3 10110U)             use Intel Smart Sound technology (SST Audio Device WDM)
[/COLOR]

**$ lspci | grep -i audio**
[HTML]00:1f.3 Multimedia audio controller: Intel Corporation Comet Lake PCH-LP cAVS[/HTML]



**$ inxi -F**
```
System:
  Host: francois-BOHB-WAX9 Kernel: 5.15.0-25-generic x86_64 bits: 64
    Desktop: GNOME 42.0 Distro: Ubuntu 22.04 (Jammy Jellyfish)
Machine:
  Type: Laptop System: HUAWEI product: BOHB-WAX9 v: M1340
    serial: <superuser required>
  Mobo: HUAWEI model: BOHB-WAX9-PCB-B2 v: M1340
    serial: <superuser required> UEFI: HUAWEI v: 1.41 date: 02/21/2022
Battery:
  ID-1: BAT1 charge: 41.6 Wh (99.8%) condition: 41.7/41.6 Wh (100.3%)
CPU:
  Info: dual core model: Intel Core i3-10110U bits: 64 type: MT MCP cache:
    L2: 512 KiB
  Speed (MHz): avg: 800 min/max: 400/4100 cores: 1: 800 2: 800 3: 800
    4: 800
Graphics:
  Device-1: Intel CometLake-U GT2 [UHD Graphics] driver: i915 v: kernel
  Device-2: IMC Networks HD Camera type: USB driver: uvcvideo
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: gpu: i915 resolution: 1: 1920x1080~60Hz
    2: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel UHD Graphics (CML GT2) v: 4.6 Mesa 22.0.1
Audio:
  Device-1: Intel Comet Lake PCH-LP cAVS driver: sof-audio-pci-intel-cnl
  Sound Server-1: ALSA v: k5.15.0-25-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Comet Lake PCH-LP CNVi WiFi driver: iwlwifi
  IF: wlp0s20f3 state: up mac: a4:42:3b:83:fb:c1
Bluetooth:
  Device-1: Intel Bluetooth 9460/9560 Jefferson Peak (JfP) type: USB
    driver: btusb
  Report: hciconfig ID: hci0 state: up address: A4:42:3B:83:FB:C5 bt-v: 3.0
Drives:
  Local Storage: total: 238.47 GiB used: 7.78 GiB (3.3%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: MZVLB256HBHQ-00000
    size: 238.47 GiB
Partition:
  ID-1: / size: 70.95 GiB used: 7.74 GiB (10.9%) fs: ext4 dev: /dev/nvme0n1p8
  ID-2: /boot/efi size: 96 MiB used: 44.7 MiB (46.6%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: partition size: 5.48 GiB used: 0 KiB (0.0%)
    dev: /dev/nvme0n1p9
Sensors:
  System Temperatures: cpu: 41.0 C pch: 36.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 265 Uptime: 6h 58m Memory: 7.51 GiB used: 3.06 GiB (40.7%)
  Shell: Bash inxi: 3.3.13

```

Have you any idea, thanks.

François

---

### Post by #&amp;thj^% on 2022-04-23
hummm
Mine works:
```
Audio:
  Device-1: Intel Comet Lake PCH-LP cAVS driver: sof-audio-pci-intel-cnl
  Sound Server-1: ALSA v: k5.15.0-23-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes

```
Laptop:
```
System: LENOVO product: 20R10010US v: ThinkPad X1 Carbon 7th
    serial: <superuser required>
  Mobo: LENOVO model: 20R10010US v: SDK0J40697 WIN
    serial: <superuser required> UEFI: LENOVO v: N2QET45W(1.39 )
    date: 02/03/2022

```

---

### Post by aiwayfr89 on 2022-04-23
Any idea?

**$ aplay -l**
```
**** Liste des périphériques matériels PLAYBACK ****
carte 0 : sofhdadsp [sof-hda-dsp], périphérique 1 : HDMI1 (*) []
  Sous-périphériques : 1/1
  Sous-périphérique #0 : subdevice #0
carte 0 : sofhdadsp [sof-hda-dsp], périphérique 2 : HDMI2 (*) []
  Sous-périphériques : 1/1
  Sous-périphérique #0 : subdevice #0
carte 0 : sofhdadsp [sof-hda-dsp], périphérique 3 : HDMI3 (*) []
  Sous-périphériques : 1/1
  Sous-périphérique #0 : subdevice #0
```


**$ pacmd list-sources**
```
1 source(s) available.
  * index: 0
    name: <auto_null.monitor>
    driver: <module-null-sink.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 1000
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max rewind: 344 KiB
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stéréo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
    monitor_of: 0
    module: 14
    properties:
        device.description = "Monitor of Sortie fictive"
        device.class = "monitor"
        device.icon_name = "audio-input-microphone"
```



**$ pacmd list-sinks**
```
1 sink(s) available.
  * index: 0
    name: <auto_null>
    driver: <module-null-sink.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 1000
    volume: front-left: 57853 /  88% / -3.25 dB,   front-right: 57853 /  88% / -3.25 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 344 KiB
    max rewind: 344 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stéréo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
    module: 14
    properties:
        device.description = "Sortie fictive"
        device.class = "abstract"
        device.icon_name = "audio-card"
```

---

### Post by #&amp;thj^% on 2022-04-23
Not really, do you have an older kernel to boot to check?

---

### Post by aiwayfr89 on 2022-04-23
I will try another kernel with mainline...

---

### Post by #&amp;thj^% on 2022-04-23
I was hoping for an older kernel, but keep us informed.

---

### Post by aiwayfr89 on 2022-04-24
After trying many other kernel older or newer, nothing new! I also tried to put a new version of intel sof_ ...

---

### Post by #&amp;thj^% on 2022-04-25
Try this, add "**snd_intel_dspcfg.dsp_driver=1**" to your **GRUB_CMDLINE_LINUX_DEFAULT** 
and just for GP
```
sudo update-grub
```
EDIT if that don't work, show this please:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by aiwayfr89 on 2022-04-26
So I modified  [B] /etc/default/grub
[/B][B]
$ cat /etc/default/grub[/B]
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#Modifié le 27 Avril 2022
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="snd_intel_dspcfg.dsp_driver=1"
GRUB_CMDLINE_LINUX=""


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

Then run  **sudo update-grub** and reboot it doesn't work

**$cat /etc/modprobe.d/alsa-base.conf**
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7


# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }


# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
```

---

### Post by aiwayfr89 on 2022-04-27
**$ sudo dmesg | grep -Ei "audio|error|warning"**


```
[    0.066228] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.106173] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.GPLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.106189] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.106195] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.TPLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.106198] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.106206] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.GUPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.106210] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.106214] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.TUPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.106217] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.106243] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS01._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.106247] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.106251] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS01._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.106254] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.109367] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS02._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.109367] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.109367] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS02._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.109367] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.109646] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS03._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.109652] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.109656] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS03._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.109659] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.111345] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS04._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.111349] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.111353] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS04._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.111357] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.113384] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS05._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.113384] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.113384] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS05._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.113384] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.114753] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS06._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.114757] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.114761] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS06._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.114765] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.117371] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS07._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.117371] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.117371] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS07._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.117371] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.118148] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS08._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.118153] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.118156] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS08._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.118160] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.119842] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS09._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.119846] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.119850] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS09._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.119853] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.121541] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS10._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.121546] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.121550] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.HS10._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.121553] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.123305] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS01._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.123310] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.123314] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS01._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.123317] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.123343] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS02._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.123347] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.123351] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS02._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.123354] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.123380] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS03._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.123384] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.123388] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS03._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.123391] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.123417] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS04._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.123420] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.123424] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS04._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.123427] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.123453] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS05._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.123457] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.123461] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS05._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.123464] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.123489] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS06._UPC], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.123493] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.123497] ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0.XHC.RHUB.SS06._PLD], AE_ALREADY_EXISTS (20210730/dswload2-326)
[    0.123500] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20210730/psobject-220)
[    0.710282] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.DGPV], AE_NOT_FOUND (20210730/psargs-330)
[    0.710291] ACPI Error: Aborting method \_SB.PCI0.RP05.PCRP._ON due to previous error (AE_NOT_FOUND) (20210730/psparse-529)
[    0.843423] pcieport 0000:00:1d.0: DPC: error containment capabilities: Int Msg #0, RPExt+ PoisonedTLP+ SwTrigger+ RP PIO Log 4, DL_ActiveErr+
[    1.136129] RAS: Correctable Errors collector initialized.
[    2.725561] EXT4-fs (nvme0n1p8): re-mounted. Opts: errors=remount-ro. Quota mode: none.
[    4.024502] sof-audio-pci-intel-cnl 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if info 0x040100
[    4.024524] sof-audio-pci-intel-cnl 0000:00:1f.3: Digital mics found on Skylake+ platform, using SOF driver
[    4.024538] sof-audio-pci-intel-cnl 0000:00:1f.3: enabling device (0000 -> 0002)
[    4.024719] sof-audio-pci-intel-cnl 0000:00:1f.3: DSP detected with PCI class/subclass/prog-if 0x040100
[    4.194712] sof-audio-pci-intel-cnl 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    4.202352] sof-audio-pci-intel-cnl 0000:00:1f.3: use msi interrupt mode
[    4.217133] sof-audio-pci-intel-cnl 0000:00:1f.3: hda codecs found, mask 4
[    4.217136] sof-audio-pci-intel-cnl 0000:00:1f.3: using HDA machine driver skl_hda_dsp_generic now
[    4.217140] sof-audio-pci-intel-cnl 0000:00:1f.3: DMICs detected in NHLT tables: 2
[    4.218481] sof-audio-pci-intel-cnl 0000:00:1f.3: Firmware info: version 2:1:1-3964a
[    4.218483] sof-audio-pci-intel-cnl 0000:00:1f.3: Firmware: ABI 3:21:0 Kernel ABI 3:18:0
[    4.218484] sof-audio-pci-intel-cnl 0000:00:1f.3: warn: FW ABI is more recent than kernel
[    4.218487] sof-audio-pci-intel-cnl 0000:00:1f.3: unknown sof_ext_man header type 3 size 0x30
[    4.317397] sof-audio-pci-intel-cnl 0000:00:1f.3: Firmware info: version 2:1:1-3964a
[    4.317399] sof-audio-pci-intel-cnl 0000:00:1f.3: Firmware: ABI 3:21:0 Kernel ABI 3:18:0
[    4.317401] sof-audio-pci-intel-cnl 0000:00:1f.3: warn: FW ABI is more recent than kernel
[    4.323554] sof-audio-pci-intel-cnl 0000:00:1f.3: Topology: ABI 3:21:0 Kernel ABI 3:18:0
[    4.323557] sof-audio-pci-intel-cnl 0000:00:1f.3: warn: topology ABI is more recent than kernel
[    4.334181] sof-audio-pci-intel-cnl 0000:00:1f.3: ASoC: Parent card not yet available, widget card binding deferred



```

---

