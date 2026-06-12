---
title: "ubuntu server blank screen while booting and after"
date: 2018-02-14
forum: Installation &amp; Upgrades
---

### Post by bijupp on 2018-02-14
I have installed Ubuntu server in software raid but after installation I found the the server is up and running but after grub nothing is displayed in the Display [blank screen] I tried 'nomodeset' in the boot option but didn't get any thing in the screen.. Now I login by recovery options ... pl. help


    I have edited /etc/default/grub as follows






    GRUB_DEFAULT=0
    GRUB_HIDDEN_TIMEOUT=0
    GRUB_HIDDEN_TIMEOUT_QUIET=true
    GRUB_TIMEOUT=10
    GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
    GRUB_CMDLINE_LINUX=""






    grub update also done




    pl. tell me what went wrong..


    thanks in advance..

---

### Post by cruzer001 on 2018-02-14
Please post your specifications:

```
inxi -b
```

---

### Post by bijupp on 2018-02-16
> **cruzer001 said:**
> Please post your specifications:

```
inxi -b
```


I have run the code get this output....
> System:    Host: server Kernel: 4.4.0-112-generic i686 (32 bit)
           Console: tty 0 Distro: Ubuntu 16.04 xenial
Machine:   System: HP product: ProLiant ML110 G5 v: NA
           Mobo: Wistron model: ProLiant ML110 G5 v: NA
           Bios: HP v: O15 date: 10/09/2009
CPU:       Dual core Intel Xeon E3110 (-HT-MCP-) speed/max: 2000/3000 MHz
Graphics:  Card: Matrox Systems MGA G200e [Pilot] ServerEngines (SEP1)
           Display Server: N/A driver: N/A
           tty size: 80x24 Advanced Data: N/A out of X
Network:   Card: Broadcom NetXtreme BCM5722 Gigabit Ethernet PCI Express
           driver: tg3
Drives:    HDD Total Size: 320.1GB (2.0% used)
RAID:      Devices: 1: /dev/md1 2: /dev/md3 3: /dev/md0 4: /dev/md2
Info:      Processes: 139 Uptime: 5:49 Memory: 246.3/2012.5MB
           Init: systemd runlevel: 5 Client: Shell (bash) inxi: 2.2.35



---

### Post by cruzer001 on 2018-02-16
Hello

> Graphics: Card: Matrox Systems MGA G200e [Pilot] ServerEngines (SEP1)
Display Server: N/A driver: N/A

I'm vague on server requirements, I expected to see at least "Display Server: x11".  Surely xserver-xorg-core is already installed.  Maybe inxi will not pick up on a core install.  Like I said, I'm vague on this.

Your running a Matrox video card but no graphic driver.  I think a driver needs to be installed.

xserver-xorg-video-mga

This is my best and only suggestion I have for you.  Good luck

---

