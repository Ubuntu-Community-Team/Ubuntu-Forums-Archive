---
title: "Slow boot after fresh install and update"
date: 2016-05-21
forum: Installation &amp; Upgrades
---

### Post by aeonoak on 2016-05-21
Sorry if i'm asking that in the wrong place.

I lost all the day trying to resolve that without success.

I have a desktop with 8 GB RAM DDR3, AMD Phenom x3 cores, Nvidia GTX 750, mechanical Seagate 1TB hard disk.

I have installed the xubuntu on /dev/sda1 and put my /home on /dev/sda6 with a swap on /dev/sda5.

After the install the system start normally and I have saved this dmesg log: [http://pastebin.com/aPfUM2Vx](http://pastebin.com/aPfUM2Vx)
The system seems to working very fine, so, I have make all the updates and installed some apps: vlc, chrome, plank dock (and themes), numix icons, qbittorrent, dbconf-editor, gimp, inkscape, gitg, oracle java 8 and the drivers for: Nvidia 361.42 (proprietary, tested) and Processor microcode firmware for AMD CPUs from amd64-microcode (proprietary).

But, after the first reboot the 5 minutes to boot started to happen like in this others dmesg:

[http://pastebin.com/CQ7De1DY](http://pastebin.com/CQ7De1DY)

and this is another one:

[http://pastebin.com/AxfugZKV](http://pastebin.com/AxfugZKV)

systemd-analyze blame

[http://pastebin.com/QAF9X4HW](http://pastebin.com/QAF9X4HW)

systemd-analyze critical-chain

[http://pastebin.com/2jV866BT](http://pastebin.com/2jV866BT)

After the boot the OS work like a charm without any problem.

So, I really don't know what I have to do to solve that 5+ minutes of boot.

Any help will be appreciated.

---

### Post by aeonoak on 2016-05-22
up!
Anyone?

---

