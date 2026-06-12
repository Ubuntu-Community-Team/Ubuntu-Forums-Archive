---
title: "Re: Uninstalled xorg intel drivers. Acceleration works. XFCE broken."
date: 2017-11-26
forum: MINT
---

### Post by friedchips2 on 2017-11-26
I get a generic XFCE screen when I get auto-logged in. One hint I have is that dmesg is not logging anything.... Strange. Help! I don't even know where to start with no log. I uninstalled the xorg-driver-intel package I think it was called..

update. Looks like dbus is broken. How to fix that?

---

### Post by uRock on 2017-11-26
Why did you uninstall it? If uninstalling something breaks a system, then reinstall it. Hit Ctrl+Alt+F1 then log in and enter ```
"sudo apt-get install xorg-driver-intel
```then ```
sudo shutdown -r now
```

---

### Post by friedchips2 on 2017-11-26
That did fix it. My graphic rendering was much better with the driver removed tho. Is there a way I can do this without breaking everything? I tried switching to "uxa" as mentioned here [https://ubuntuforums.org/showthread.php?t=2130640](https://ubuntuforums.org/showthread.php?t=2130640)  That also broke things... I removed the xorg.conf file again and all is well.

Is it possible to make my system use another driver or blacklist the intel driver for example?

---

### Post by mc4man on 2017-11-26
> **friedchips2 said:**
> Is it possible to make my system use another driver or blacklist the intel driver for example?

Why don't you install inxi then run
```
inxi -Fxz
```
Post complete output in a code box, then anyone trying to help you know what you are running & on what hardware..
(- for _most_ recent Intel iGPU hardware the  xserver-xorg-video-intel package is not needed.. (2007+

---

### Post by friedchips2 on 2017-11-26
[https://cubethethird.wordpress.com/2016/05/12/boost-xorg-by-removing-intel-drivers/](https://cubethethird.wordpress.com/2016/05/12/boost-xorg-by-removing-intel-drivers/)

Here is a link about what I'm talking about. The xorg file they talk about removing already doesn't exist however.

---

### Post by him610 on 2017-11-26
How about posting the results of ```
inxi -F
``` between the *code* tags

---

### Post by friedchips2 on 2017-11-26
```
System:    Host: stephen-ThinkPad-T61 Kernel: 4.8.0-53-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Xfce 4.12.3 (Gtk 2.24.28) Distro: Linux Mint 18.2 Sonya
Machine:   System: LENOVO product: 64644YU v: ThinkPad T61
           Mobo: LENOVO model: 64644YU
           Bios: LENOVO v: 7LETD0WW (2.30 ) date: 02/27/2012
CPU:       Dual core Intel Core2 Duo T7300 (-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 ssse3 vmx) bmips: 7980
           clock speeds: max: 2001 MHz 1: 1200 MHz 2: 1600 MHz
Graphics:  Card: Intel Mobile GM965/GL960 Integrated Graphics Controller (primary)
           bus-ID: 00:02.0
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1280x800@60.00hz, 1920x1080@60.00hz
           GLX Renderer: Mesa DRI Intel 965GM
           GLX Version: 2.1 Mesa 17.0.7 Direct Rendering: Yes
Audio:     Card Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.8.0-53-generic
Network:   Card-1: Intel 82566MM Gigabit Network Connection
           driver: e1000e v: 3.2.6-k port: 1840 bus-ID: 00:19.0
           IF: enp0s25 state: up speed: 100 Mbps duplex: full mac: <filter>
           Card-2: Intel PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
           driver: iwl4965 v: in-tree: bus-ID: 03:00.0
           IF: wls3 state: down mac: <filter>
Drives:    HDD Total Size: 120.0GB (73.9% used)
           ID-1: /dev/sda model: FUJITSU_MHW2120B size: 120.0GB
Partition: ID-1: / size: 11G used: 6.6G (65%) fs: ext4 dev: /dev/sda1
           ID-2: /home size: 97G used: 75G (81%) fs: ext4 dev: /dev/sda6
           ID-3: swap-1 size: 2.29GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 45.0C mobo: 38.0C
           Fan Speeds (in rpm): cpu: 2976
Info:      Processes: 208 Uptime: 26 min Memory: 1405.3/2982.5MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35 

```

---

### Post by Yellow Pasque on 2017-11-26
What are you trying to do is force the "modesetting" driver to be used. Make sure you have it installed (I don't know if Mint has a separate package or it's built in to the Xserver), and then you can try it by creating a /etc/X11/xorg.conf
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "modesetting"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```


> **friedchips2 said:**
> [https://cubethethird.wordpress.com/2016/05/12/boost-xorg-by-removing-intel-drivers/](https://cubethethird.wordpress.com/2016/05/12/boost-xorg-by-removing-intel-drivers/)
Here is a link about what I'm talking about. The xorg file they talk about removing already doesn't exist however.

The directions were made with Arch Linux, so some filenames may be different. Also, there's no need to remove the intel driver when you can specify modesetting like above.

---

### Post by jeremy31 on 2017-11-26
*Thread moved to **MINT**.*

---

### Post by friedchips2 on 2017-11-26
Using that xorg.conf basically did the same as uninstalling the intel driver. It gave me good video but broke a lot. Why would I lose dbus by changing graphics drivers?

It switched as intended. Even showed DRI 3 instead of two. But my normal desktop was not working properly. I'd screenshot, but GIMP won't open that way. Firefox will. Chrome won't. No menu's. I have to right click on desktop like it was openbox or something but it is not. I can even get back to the login screen and pick a different session type.

---

### Post by Yellow Pasque on 2017-11-26
> Why would I lose dbus by changing graphics drivers? 
I'm not sure.

---

### Post by friedchips2 on 2017-11-26
What logs can I check to make sure of what is happening? I'm open to any and all suggestions on how to investigate this. Thanks for all the help thus far.

---

### Post by Yellow Pasque on 2017-11-26
You said dmesg doesn't work? Maybe look at journalctl if Mint uses systemd.

---

### Post by friedchips2 on 2017-12-03
I'm getting a new laptop for Christmas. I don't care anymore lol.

---

