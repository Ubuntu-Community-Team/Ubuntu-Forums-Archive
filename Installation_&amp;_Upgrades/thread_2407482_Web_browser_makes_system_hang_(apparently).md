---
title: "Web browser makes system hang (apparently)"
date: 2018-12-04
forum: Installation &amp; Upgrades
---

### Post by Marco_Ros on 2018-12-04
After a time of use of any browser (Firefox and Chromium), system resources are hoarded by it and it is virtually impossible to recover, except for a "hard reboot" (energy disconnection) or maybe waiting more that one hour.
Is there a way to diagnose this problem and/or solve it?


[LIST]
[*]Firefox Quantum ver.63.0.3 (64-bits)
[*]Chromium Ver 70.0.3538.77 (Build official) Built on Ubuntu , running on Ubuntu 18.04 (64 bits)
[/LIST]

Acer Aspire 2920 Laptop
[LIST]
[*]UBUNTU 18.04 LTS
[*] OS TYPE: 64 bits
[*]RAM: 4GB
[*]Intel® Core™2 Duo CPU T7300 @ 2.00GHz × 2
[*]GRAPHICS:Intel® 965GM
[/LIST]

---

### Post by kc1di on 2018-12-05
please install inxi with this command ```
sudo apt install inxi
``` 
once installed run this command and post the output back here, use code tags please. #
```
inxi -Fxzd
```

---

### Post by freemedia2018 on 2018-12-05
I've had a possibly related problem lately where the "Web Content" sometimes refuses to close when the browser does, and when it does, it also prevents "ps aux" from giving the console back. Then the reboot and poweroff commands don't work, kill -9 doesn't work, I have to Alt+Sysrq REISUB if this happens. Note this isn't all the time.

Only some websites trigger it. Youtube is particularly bad, I do not have Adobe anything installed. Avoiding Youtube seems to help a lot.

Very interested in where this thread is going. I suspect a bug in Mozilla web browsers, or the kernel. I haven't experienced a bug this bad in years, I doubt it is specific to Ubuntu. Apart from running Youtube it is not easy to reproduce. And if Youtube can hijack the system that badly, it is fair to call it a bug in some software we are running. A bug this severe is rare in my experience, and just to reiterate-- I do not think this is Ubuntu-specific. I note that you are having the same problem with different browsers, I guess we can rule out the JS engine. I just started having these problems in the past week or two, and only on one machine (the one I watch the most video on.)

---

### Post by Marco_Ros on 2018-12-05
since some time, and several UBUNTU generations, I've had a problem with Firefox, apparently, there is a bug in a CHROME library, or something like that, that makes some scripts take possession of all the resources, until Firefox ask if you want to continue with script.

---

### Post by Marco_Ros on 2018-12-05
> **kc1di said:**
> please install inxi with this command ```
sudo apt install inxi
``` 
once installed run this command and post the output back here, use code tags please. #
```
inxi -Fxzd
```
thanks!

Here is the output:
```

[COLOR=#729FCF]**System:   **[/COLOR][COLOR=#729FCF]**Host:**[/COLOR][COLOR=#D3D7CF] linuxhost [/COLOR][COLOR=#729FCF]**Kernel:**[/COLOR][COLOR=#D3D7CF] 4.15.0-42-generic x86_64[/COLOR]
[COLOR=#729FCF]**bits:**[/COLOR][COLOR=#D3D7CF] 64 [/COLOR][COLOR=#729FCF]**gcc:**[/COLOR][COLOR=#D3D7CF] 7.3.0[/COLOR]
[COLOR=#729FCF]**Desktop:**[/COLOR][COLOR=#D3D7CF] Gnome 3.28.3 (Gtk 3.22.30-1ubuntu1)[/COLOR]
[COLOR=#729FCF]**Distro:**[/COLOR][COLOR=#D3D7CF] Ubuntu 18.04.1 LTS[/COLOR]
[COLOR=#729FCF]**Machine:  **[/COLOR][COLOR=#729FCF]**Device:**[/COLOR][COLOR=#D3D7CF] laptop [/COLOR][COLOR=#729FCF]**System:**[/COLOR][COLOR=#D3D7CF] Acer [/COLOR][COLOR=#729FCF]**product:**[/COLOR][COLOR=#D3D7CF] Aspire 2920 [/COLOR][COLOR=#729FCF]**v:**[/COLOR][COLOR=#D3D7CF] 0100 [/COLOR][COLOR=#729FCF]**serial:**[/COLOR][COLOR=#D3D7CF] N/A[/COLOR]
[COLOR=#729FCF]**Mobo:**[/COLOR][COLOR=#D3D7CF] Acer [/COLOR][COLOR=#729FCF]**model:**[/COLOR][COLOR=#D3D7CF] Calado [/COLOR][COLOR=#729FCF]**v:**[/COLOR][COLOR=#D3D7CF] Rev [/COLOR][COLOR=#729FCF]**serial:**[/COLOR][COLOR=#D3D7CF] N/A[/COLOR]
[COLOR=#729FCF]**BIOS:**[/COLOR][COLOR=#D3D7CF] Phoenix [/COLOR][COLOR=#729FCF]**v:**[/COLOR][COLOR=#D3D7CF] V1.03 [/COLOR][COLOR=#729FCF]**date:**[/COLOR][COLOR=#D3D7CF] 10/18/2007[/COLOR]
[COLOR=#729FCF]**Battery   **[/COLOR][COLOR=#729FCF]**BAT0:**[/COLOR][COLOR=#729FCF]**charge:**[/COLOR][COLOR=#D3D7CF] 1.1 Wh 100.0% [/COLOR][COLOR=#729FCF]**condition:**[/COLOR][COLOR=#D3D7CF] 1.1/53.3 Wh (2%)[/COLOR]
[COLOR=#729FCF]**model:**[/COLOR][COLOR=#D3D7CF] SANYO GARDA32 [/COLOR][COLOR=#729FCF]**status:**[/COLOR][COLOR=#D3D7CF] Full[/COLOR]
[COLOR=#729FCF]**CPU:      **[/COLOR][COLOR=#729FCF]**Dual core**[/COLOR][COLOR=#D3D7CF] Intel Core2 Duo T7300 (-MCP-) [/COLOR]
[COLOR=#729FCF]**arch:**[/COLOR][COLOR=#D3D7CF] Conroe rev.10 [/COLOR][COLOR=#729FCF]**cache:**[/COLOR][COLOR=#D3D7CF] 4096 KB[/COLOR]
[COLOR=#729FCF]**flags:**[/COLOR][COLOR=#D3D7CF] (lm nx sse sse2 sse3 ssse3 vmx) [/COLOR][COLOR=#729FCF]**bmips:**[/COLOR][COLOR=#D3D7CF] 7980[/COLOR]
[COLOR=#729FCF]**clock speeds:**[/COLOR][COLOR=#729FCF]**max:**[/COLOR][COLOR=#D3D7CF] 2001 MHz [/COLOR][COLOR=#729FCF]**1:**[/COLOR][COLOR=#D3D7CF] 1220 MHz [/COLOR][COLOR=#729FCF]**2:**[/COLOR][COLOR=#D3D7CF] 1088 MHz[/COLOR]
[COLOR=#729FCF]**Graphics: **[/COLOR][COLOR=#729FCF]**Card:**[/COLOR][COLOR=#D3D7CF] Intel Mobile GM965/GL960 Integrated Graphics Controller (primary)[/COLOR]
[COLOR=#729FCF]**bus-ID:**[/COLOR][COLOR=#D3D7CF] 00:02.0[/COLOR]
[COLOR=#729FCF]**Display Server:**[/COLOR][COLOR=#D3D7CF] x11 (X.Org 1.19.6 ) [/COLOR][COLOR=#729FCF]**driver:**[/COLOR][COLOR=#D3D7CF] i915[/COLOR]
[COLOR=#729FCF]**Resolution:**[/COLOR][COLOR=#D3D7CF] 1280x800@60.00hz[/COLOR]
[COLOR=#729FCF]**OpenGL: renderer:**[/COLOR][COLOR=#D3D7CF] Mesa DRI Intel 965GM[/COLOR]
[COLOR=#729FCF]**version:**[/COLOR][COLOR=#D3D7CF] 2.1 Mesa 18.0.5 [/COLOR][COLOR=#729FCF]**Direct Render:**[/COLOR][COLOR=#D3D7CF] Yes[/COLOR]
[COLOR=#729FCF]**Audio:    **[/COLOR][COLOR=#729FCF]**Card**[/COLOR][COLOR=#D3D7CF] Intel 82801H (ICH8 Family) HD Audio Controller[/COLOR]
[COLOR=#729FCF]**driver:**[/COLOR][COLOR=#D3D7CF] snd_hda_intel [/COLOR][COLOR=#729FCF]**bus-ID:**[/COLOR][COLOR=#D3D7CF] 00:1b.0[/COLOR]
[COLOR=#729FCF]**Sound:**[/COLOR][COLOR=#D3D7CF] Advanced Linux Sound Architecture [/COLOR][COLOR=#729FCF]**v:**[/COLOR][COLOR=#D3D7CF] k4.15.0-42-generic[/COLOR]
[COLOR=#729FCF]**Network:  **[/COLOR][COLOR=#729FCF]**Card-1:**[/COLOR][COLOR=#D3D7CF] Broadcom Limited NetLink BCM5787M Gigabit Ethernet PCIE[/COLOR]
[COLOR=#729FCF]**driver:**[/COLOR][COLOR=#D3D7CF] tg3 [/COLOR][COLOR=#729FCF]**v:**[/COLOR][COLOR=#D3D7CF] 3.137 [/COLOR][COLOR=#729FCF]**bus-ID:**[/COLOR][COLOR=#D3D7CF] 02:00.0[/COLOR]
[COLOR=#729FCF]**IF:**[/COLOR][COLOR=#D3D7CF] enp2s0 [/COLOR][COLOR=#729FCF]**state:**[/COLOR][COLOR=#D3D7CF] down [/COLOR][COLOR=#729FCF]**mac:**[/COLOR][COLOR=#D3D7CF] <filter>[/COLOR]
[COLOR=#729FCF]**Card-2:**[/COLOR][COLOR=#D3D7CF] Intel PRO/Wireless 3945ABG [Golan] Network Connection[/COLOR]
[COLOR=#729FCF]**driver:**[/COLOR][COLOR=#D3D7CF] iwl3945 [/COLOR][COLOR=#729FCF]**v:**[/COLOR][COLOR=#D3D7CF] in-tree:s [/COLOR][COLOR=#729FCF]**bus-ID:**[/COLOR][COLOR=#D3D7CF] 04:00.0[/COLOR]
[COLOR=#729FCF]**IF:**[/COLOR][COLOR=#D3D7CF] wlp4s0 [/COLOR][COLOR=#729FCF]**state:**[/COLOR][COLOR=#D3D7CF] up [/COLOR][COLOR=#729FCF]**mac:**[/COLOR][COLOR=#D3D7CF] <filter>[/COLOR]
[COLOR=#729FCF]**Drives:   **[/COLOR][COLOR=#729FCF]**HDD Total Size:**[/COLOR][COLOR=#D3D7CF] 1000.2GB (75.2% used)[/COLOR]
[COLOR=#729FCF]**ID-1:**[/COLOR][COLOR=#D3D7CF] /dev/sda [/COLOR][COLOR=#729FCF]**model:**[/COLOR][COLOR=#D3D7CF] TOSHIBA_MQ01ABD1 [/COLOR][COLOR=#729FCF]**size:**[/COLOR][COLOR=#D3D7CF] 1000.2GB [/COLOR][COLOR=#729FCF]**temp:**[/COLOR][COLOR=#D3D7CF] 42C[/COLOR]
[COLOR=#729FCF]**Optical-1:**[/COLOR][COLOR=#D3D7CF] /dev/sr0 [/COLOR][COLOR=#729FCF]**model:**[/COLOR][COLOR=#D3D7CF] HL-DT-ST DVDRAM GSA-T20N[/COLOR]
[COLOR=#729FCF]**rev:**[/COLOR][COLOR=#D3D7CF] WP03 [/COLOR][COLOR=#729FCF]**dev-links:**[/COLOR][COLOR=#D3D7CF] cdrom,cdrw,dvd,dvdrw[/COLOR]
[COLOR=#729FCF]**Features: speed:**[/COLOR][COLOR=#D3D7CF] 24x [/COLOR][COLOR=#729FCF]**multisession:**[/COLOR][COLOR=#D3D7CF] yes[/COLOR]
[COLOR=#729FCF]**audio:**[/COLOR][COLOR=#D3D7CF] yes [/COLOR][COLOR=#729FCF]**dvd:**[/COLOR][COLOR=#D3D7CF] yes [/COLOR][COLOR=#729FCF]**rw:**[/COLOR][COLOR=#D3D7CF] cd-r,cd-rw,dvd-r,dvd-ram [/COLOR][COLOR=#729FCF]**state:**[/COLOR][COLOR=#D3D7CF] running[/COLOR]
[COLOR=#729FCF]**Partition:**[/COLOR][COLOR=#729FCF]**ID-1:**[/COLOR][COLOR=#D3D7CF] / [/COLOR][COLOR=#729FCF]**size:**[/COLOR][COLOR=#D3D7CF] 158G [/COLOR][COLOR=#729FCF]**used:**[/COLOR][COLOR=#D3D7CF] 28G (19%) [/COLOR][COLOR=#729FCF]**fs:**[/COLOR][COLOR=#D3D7CF] ext4 [/COLOR][COLOR=#729FCF]**dev:**[/COLOR][COLOR=#D3D7CF] /dev/sda6[/COLOR]
[COLOR=#729FCF]**RAID:     **[/COLOR][COLOR=#D3D7CF] No RAID devices: /proc/mdstat, md_mod kernel module present[/COLOR]
[COLOR=#729FCF]**Sensors:  **[/COLOR][COLOR=#729FCF]**System Temperatures: cpu:**[/COLOR][COLOR=#D3D7CF] 62.0C [/COLOR][COLOR=#729FCF]**mobo:**[/COLOR][COLOR=#D3D7CF] 58.0C[/COLOR]
[COLOR=#729FCF]**Fan Speeds (in rpm): cpu:**[/COLOR][COLOR=#D3D7CF] N/A[/COLOR]
[COLOR=#729FCF]**Info:     **[/COLOR][COLOR=#729FCF]**Processes:**[/COLOR][COLOR=#D3D7CF] 265 [/COLOR][COLOR=#729FCF]**Uptime:**[/COLOR][COLOR=#D3D7CF] 25 min [/COLOR][COLOR=#729FCF]**Memory:**[/COLOR][COLOR=#D3D7CF] 2311.6/3936.2MB[/COLOR]
[COLOR=#729FCF]**Init:**[/COLOR][COLOR=#D3D7CF] systemd [/COLOR][COLOR=#729FCF]**runlevel:**[/COLOR][COLOR=#D3D7CF] 5 [/COLOR][COLOR=#729FCF]**Gcc sys:**[/COLOR][COLOR=#D3D7CF] 7.3.0[/COLOR]
[COLOR=#729FCF]**Client:**[/COLOR][COLOR=#D3D7CF] Shell (bash 4.4.191) [/COLOR][COLOR=#729FCF]**inxi:**[/COLOR][COLOR=#D3D7CF] 2.3.56 [/COLOR]

```

---

### Post by kc1di on 2018-12-06
I would suggest that you would be better off with that machine using xubuntu or may even mate instead of Gnome.  Though dual core is listed as a minimum requirement. it would most likely run much better with a lighter desktop-- Good Luck.

---

### Post by Marco_Ros on 2018-12-06
> **kc1di said:**
> I would suggest that you would be better off with that machine using xubuntu or may even mate instead of Gnome.  Though dual core is listed as a minimum requirement. it would most likely run much better with a lighter desktop-- Good Luck.

Thanks Dave,
I switched desktop to Unity **Desktop** (sorry if this data does not appear in the information I pasted)

---

### Post by kc1di on 2018-12-08
Unity is still quite heavy on resources it's based on gnome and is actually some times more resource intensive than gnome.  still think you'd be better off with mate or xfce on that machine. 
good luck.

---

