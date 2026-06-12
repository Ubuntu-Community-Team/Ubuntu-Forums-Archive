---
title: "Can't Shutdown Desktop Ubuntu Mate 16.04"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by poorguy on 2016-04-22
Hey All,

Just installed the Ubuntu Mate 16.04 32bit and can't shutdown my computer it does restart without any problems.
I figured someone else is experiencing the same problem and since this release is only one day old I figured there will be some issues.

Appreciate any help when a spare moment opens as I know forum support members are very busy.

Thanks
The PoorGuy

My system specs.

Intel-DG33BU:~$  inxi -Fx 
System:    Host: Intel-DG33BU Kernel: 4.4.0-21-generic i686 (32 bit gcc: 5.3.1)
           Desktop: MATE 1.12.1 (Gtk 3.18.9-1ubuntu3) Distro: Ubuntu 16.04 xenial
Machine:   System: MDGs product: N/A
           Mobo: Intel model: DG33BU v: AAD79951-407
           Bios: Intel v: DPP3510J.86A.0293.2007.1002.1519 date: 10/02/2007
CPU:       Dual core Intel Pentium Dual E2220 (-MCP-) cache: 1024 KB
           flags: (lm nx pae sse sse2 sse3 ssse3) bmips: 9600
           clock speeds: max: 2400 MHz 1: 2000 MHz 2: 1600 MHz
Graphics:  Card: Intel 82G33/G31 Express Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa) Resolution: 1280x720@60.00hz
           GLX Renderer: Mesa DRI Intel G33 x86/MMX/SSE2 GLX Version: 1.4 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-21-generic
Network:   Card: Intel 82566DC-2 Gigabit Network Connection driver: e1000e v: 3.2.6-k port: 2400 bus-ID: 00:19.0
           IF: enp0s25 state: up speed: 100 Mbps duplex: full mac: 00:1c:c0:22:52:f6
Drives:    HDD Total Size: 80.0GB (10.3% used) ID-1: /dev/sda model: WDC_WD800AAJS size: 80.0GB
Partition: ID-1: / size: 70G used: 4.0G (7%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 4.21GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 174 Uptime: 8 min Memory: 405.4/3896.0MB Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.3.421) inxi: 2.2.35

---

### Post by vasa1 on 2016-04-22
> **poorguy said:**
> Hey All,

Just installed the Ubuntu Mate 16.04 32bit and can't shutdown my computer ...
What exactly happens? Do you get a sort of blank screen but the computer doesn't power down? It happened once to me with 16.04 but not on subsequent occasions.

---

### Post by poorguy on 2016-04-22
Hey vasa1,

Nope goes to the screen with the logo and dots / runs the dots and then the dots stop running and it will stay that way until I do a manual shutdown with the power button.

Originally installed 64bit and it did the same thing / this motherboard doesn't like 64bit so I installed 32bit and no change.

Thanks

---

### Post by sudodus on 2016-04-22
If you cannot do anything else, there is a soft shutdown, which is much better than a hard shutdown (pressing the power button for a long time).

I would recommend

[SIZE=3]***SysRq + r e i s u b***[/SIZE]

The hotkey combination for ***SysRq*** is often but not always ***alt + PrtScrn***.

Keep the hotkey combination for SysRq pressed, and press slowly each of the keys ***r e i s u b*** one after another. See this link for more information about the method

[Magic SysRq key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by poorguy on 2016-04-22
Hey sudodus,

Yes that does seem to work most of the time depending on how I keystroke and I can live with this minor problem for now. 
I see why it is best to wait awhile with a new release but being my 1st new release I had to try and now I know.

Thanks.

The PoorGuy

---

### Post by poorguy on 2016-04-22
I will say this about Ubuntu / Ubuntu Mate / Xubuntu / Lubuntu 16.04 new release is that they are all consistent. 
I have the same exact problem with all of them.

I thought it may be the desktop that I have installed them on but not the problem.
I have installed  Ubuntu / Ubuntu Mate / Xubuntu / Lubuntu 14.04 on the same desktop and with any one of the 14.04 versions the desktop will shutdown as it is supposed to do.

Confusing.

The PoorGuy

---

### Post by yazdzik-k on 2016-04-22
Dear Poor and friends,

It is,  for the record, the same in gnome.  it may,  or may not, reboot a couple of times,  but the install,  which I have now tried about two dozen times,  does not stay consistent, and, once installed,  "shutdown -h now" has no meaning, and sometimes the install disk asks to be removed and sometimes not.  It is deeply shocking,  considering that on really old equipment mate would have run well.  But throw in uhd and a newer nvida card,  plus synaptics that needs 4.5, ant the polish is gone.  And,  since there is so litte we can see since none of the processes are transparent,  we cannot solve it by editing a file,  as we cannot find out the problem.

some commands have little effect as well, and ctl-alt-del does not always bring you back....

but I think it is not the distro,  as it is the super rapid development this year of ssd, nmve and hidpi all coming at once.

best,
m

---

### Post by poorguy on 2016-04-22
There has got to be a fix.

---

### Post by poorguy on 2016-05-21
Ubuntu Mate 16.04 shutdown problem solved by updating bios to newest version.

All is working as it should be now.

---

