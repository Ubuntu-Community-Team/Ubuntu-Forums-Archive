---
title: "Brightness problem"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by Evgenyi on 2014-05-02
[COLOR=#000000]Hello, I have the same problem as a guy had - [/COLOR][http://ubuntuforums.org/showthread.php?t=2088190](http://ubuntuforums.org/showthread.php?t=2088190)
[COLOR=#000000]But I haven't got any folders in /sys/class/backlight.[/COLOR]
[COLOR=#000000]It disappeared after I made manipulation with that instruction:[/COLOR]
[COLOR=#000000][COLOR=#000000]1. Open a terminal (Program - Accessories - Terminal)[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]2. Type in "sudo gedit /etc/default/grub" (without the "")[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]3. Find the line that says: GRUB_CMDLINE_LINUX="quiet splash"[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]4. Edit it so it says: GRUB_CMDLINE_LINUX="quiet splash acpi_backlight=vendor"[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]5. Save and exit[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]6. Run the command "sudo update-grub" (again without quotes of course)[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]7. Reboot and enjoy!

here is information that were asked:

[/COLOR][/COLOR][COLOR=#000000]BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=6af82d53-e87d-480c-b345-b346a96c109e ro quiet splash acpi_backlight=vendor[/COLOR]
1
[COLOR=#000000]/sys/class/backlight/*[/COLOR]
[COLOR=#000000]cat: /sys/class/backlight/*/brightness: No such file or directory[/COLOR]
[COLOR=#000000]cat: /sys/class/backlight/*/max_brightness: No such file or directory[/COLOR]

[COLOR=#000000]Sony Corporation[/COLOR]
[COLOR=#000000]VPCEH1L1R[/COLOR]


[COLOR=#000000]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119M [GeForce 410M] [10de:1055] (rev a1) (prog-if 00 [VGA controller])[/COLOR]
[COLOR=#000000]Subsystem: Sony Corporation Device [104d:908b][/COLOR]
[COLOR=#000000]Flags: bus master, fast devsel, latency 0, IRQ 16[/COLOR]
[COLOR=#000000]Memory at d2000000 (32-bit, non-prefetchable) [size=16M][/COLOR]
[COLOR=#000000]Memory at c0000000 (64-bit, prefetchable) [size=256M][/COLOR]
[COLOR=#000000]Memory at d0000000 (64-bit, prefetchable) [size=32M][/COLOR]
[COLOR=#000000]I/O ports at 4000 [size=128][/COLOR]
[COLOR=#000000][virtual] Expansion ROM at d3080000 [disabled] [size=512K][/COLOR]
[COLOR=#000000]Capabilities: [60] Power Management version 3[/COLOR]
[COLOR=#000000]Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+[/COLOR]
[COLOR=#000000]Capabilities: [78] Express Endpoint, MSI 00[/COLOR]
[COLOR=#000000]Capabilities: [b4] Vendor Specific Information: Len=14 <?>[/COLOR]
[COLOR=#000000]Capabilities: [100] Virtual Channel[/COLOR]

[COLOR=#000000]video/brightnessup BRTUP 00000086 00000000 K[/COLOR]
[COLOR=#000000]sony/hotkey SNY5001:00 00000001 00000011[/COLOR]
[COLOR=#000000]sony/hotkey SNY5001:00 00000001 0000003b[/COLOR]
[COLOR=#000000]video/brightnessdown BRTDN 00000087 00000000 K[/COLOR]
[COLOR=#000000]sony/hotkey SNY5001:00 00000001 00000010[/COLOR]
[COLOR=#000000]sony/hotkey SNY5001:00 00000001 0000003b[/COLOR]

[COLOR=#000000]Please help me, my eyes promise[/COLOR]

---

### Post by raja.genupula on 2014-05-02
[http://askubuntu.com/questions/149054/how-to-change-lcd-brightness-from-command-line-or-via-script/149265#149265](http://askubuntu.com/questions/149054/how-to-change-lcd-brightness-from-command-line-or-via-script/149265#149265)

---

### Post by Toz on 2014-05-02
Evgenyi,

Can you remove the acpi_backlight=vendor kernel parameter, re-run "sudo update-grub" and reboot your computer (to get it back to the state it was before).

Then, can you run the following commands in a terminal window and post back the results:
1. Your current kernel boot line:
```
cat /proc/cmdline
```
2. Information about your video card(s):
```
lspci -k | grep -iA2 VGA
```
3. Information about your known backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
4. A listing of your loaded kernel modules:
```
lsmod
```
5. Your /var/log/Xorg.0.log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

### Post by Evgenyi on 2014-05-02
```
BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=6af82d53-e87d-480c-b345-b346a96c109e ro quiet splash quiet splash
```

```
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce 410M] (rev a1)
	Subsystem: Sony Corporation Device 908b
	Kernel driver in use: nvidia
```

```
 /sys/class/backlight/acpi_video0
15
15
15
```

```
Module                  Size  Used by
ctr                    13049  2 
ccm                    17773  2 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             27613  0 
vboxdrv               339502  3 vboxnetadp,vboxnetflt,vboxpci
cuse                   13445  3 
rfcomm                 69160  8 
bnep                   19624  2 
binfmt_misc            17468  1 
joydev                 17381  0 
snd_hda_codec_hdmi     46207  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
arc4                   12608  2 
ghash_clmulni_intel    13259  0 
snd_hda_codec_conexant    57441  1 
cryptd                 20359  1 ghash_clmulni_intel
btusb                  32412  0 
psmouse               102222  0 
bluetooth             395423  22 bnep,btusb,rfcomm
serio_raw              13462  0 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              626489  1 ath9k
rtsx_pci_ms            18151  0 
memstick               16966  1 rtsx_pci_ms
snd_seq_midi           13324  0 
lpc_ich                21080  0 
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              484040  3 ath,ath9k,mac80211
snd_rawmidi            30144  1 snd_seq_midi
snd_hda_intel          52355  5 
snd_hda_codec         192906  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
nvidia              10675249  52 
sony_laptop            54219  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
drm                   302817  2 nvidia
video                  19476  0 
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 18627  0 
mac_hid                13205  0 
mei                    82274  1 mei_me
soundcore              12680  1 snd
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_logitech_dj        18581  0 
usbhid                 52616  0 
hid                   106148  3 usbhid,hid_logitech_dj
rtsx_pci_sdmmc         23274  0 
r8169                  67581  0 
mii                    13934  1 r8169
ahci                   25819  2 
rtsx_pci               45956  2 rtsx_pci_ms,rtsx_pci_sdmmc
libahci                32168  1 ahci
```

[http://paste.ubuntu.com/7382405/](http://paste.ubuntu.com/7382405/)

---

### Post by Evgenyi on 2014-05-02
It doesn't work

---

### Post by Toz on 2014-05-02
Lets try this first: 

If the **/etc/X11/xorg.conf** file exists, add:
```
Option "EnableBrightnessControl=1"
```
...to the "Device" section of that file.

If the file does not exist, then with root privileges, create the file **/usr/share/X11/xorg.conf.d/20nvidia.conf** with the following content:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 410M"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```

Log out and back in again to test. If something goes wrong, simply delete that file and reboot to recover the system.

---

### Post by Evgenyi on 2014-05-03
I typed gedit [COLOR=#000000] [/COLOR][B]/etc/X11/xorg.conf  
[/B]There was an empty file.
I used the second variant and ,,,
Amazing! It works!

---

