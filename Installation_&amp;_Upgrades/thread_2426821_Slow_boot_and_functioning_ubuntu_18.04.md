---
title: "Slow boot and functioning ubuntu 18.04"
date: 2019-09-13
forum: Installation &amp; Upgrades
---

### Post by actuday on 2019-09-13
Hello!
i bought an acer aspire A51515 about a month back.It has a core i5 8th gen processor, 8 gigs of ram, and ask me if you need something else. It came preinstalled with Ubuntu, but for some reason the retailer installed windows 10 after i bought it. So i installed Ubuntu 18.04 LTS with USB installation, completely erasing the disk first in the installation options menu. The problem now is that where people say Ubuntu takes 10 seconds to boot, my laptop takes about 5 minutes.I'm relatively new to Linux so i have'nt really tried much except reinstalling Ubuntu 3 times or so.

---

### Post by Skaperen on 2019-09-13
can you get data from it and post it in pastebin once it has booted up?  i'd like to the output of "dmesg" and "inxi -F" (that's an UPPER CASE F).

---

### Post by actuday on 2019-09-14
it only this over and over again a couple hundred times. The first number changes each time -

[ 2342.150225] i2c_hid i2c-ELAN0501:01: i2c_hid_get_input: incomplete report (14/65535)

oh and this is the output to systemd-analyze critical-chain-

graphical.target @9min 54.149s
&#9492;&#9472;multi-user.target @9min 54.149s
  &#9492;&#9472;snapd.seeded.service @3min 20.246s +6min 33.902s
    &#9492;&#9472;basic.target @2min 34.839s
      &#9492;&#9472;sockets.target @2min 34.839s
        &#9492;&#9472;snapd.socket @2min 34.839s +461us
          &#9492;&#9472;sysinit.target @2min 34.773s
            &#9492;&#9472;cryptsetup.target @2min 34.773s
              &#9492;&#9472;systemd-ask-password-wall.path @9.550s
                &#9492;&#9472;-.mount @9.546s
                  &#9492;&#9472;system.slice @9.550s
                    &#9492;&#9472;-.slice @9.546s


and inxi-F-

System:    Host: PUTER Kernel: 4.18.0-15-generic x86_64 bits: 64 Desktop: Gnome 3.28.3
           Distro: Ubuntu 18.04.2 LTS
Machine:   Device: laptop System: Acer product: Aspire A515-51 v: V1.17 serial: N/A
           Mobo: KBL model: Charmander_KL v: V1.17 serial: N/A UEFI [Legacy]: Insyde v: V1.17 date: 03/20/2018
Battery    BAT1: charge: 37.5 Wh 82.2% condition: 45.6/48.9 Wh (93%)
CPU:       Quad core Intel Core i5-8250U (-MT-MCP-) cache: 6144 KB
           clock speeds: max: 1600 MHz 1: 820 MHz 2: 1115 MHz 3: 1094 MHz 4: 822 MHz 5: 1078 MHz 6: 1106 MHz
           7: 1056 MHz 8: 1166 MHz
Graphics:  Card: Intel UHD Graphics 620
           Display Server: x11 (X.Org 1.20.1 ) driver: i915 Resolution: 1366x768@59.97hz
           OpenGL: renderer: Mesa DRI Intel UHD Graphics 620 (Kabylake GT2) version: 4.5 Mesa 18.2.2
Audio:     Card Intel Sunrise Point-LP HD Audio driver: snd_hda_intel Sound: ALSA v: k4.18.0-15-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
           IF: enp1s0f1 state: down mac: 98:29:a6:3f:37:f9
           Card-2: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter driver: ath10k_pci
           IF: wlp2s0 state: up mac: e8:2a:44:6b:de:33
Drives:    HDD Total Size: 1000.2GB (0.7% used)
           ID-1: /dev/sda model: WDC_WD10SPZX size: 1000.2GB
Partition: ID-1: / size: 916G used: 6.3G (1%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 268 Uptime: 48 min Memory: 1337.3/7852.2MB Client: Shell (bash) inxi: 2.3.56

---

### Post by Skaperen on 2019-09-14
once it is up can you do "**[COLOR=#0000cd][FONT=courier new]sudo apt-get update && sudo apt-get -y dist-upgrade[/FONT][/COLOR]**" to get the latest kernel?  apparently, a driver in 4.15 has a bug that causes it to output a flood of those messages.

more info [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1784152").

---

### Post by actuday on 2019-09-14
alright so i ran **[COLOR=#0000cd][FONT=courier new]"sudo apt-get update && sudo apt-get -y dist-upgrade " [/FONT][/COLOR]**[COLOR=#0000cd][FONT=courier new][/FONT][/COLOR][FONT=courier new]but it still takes 5 minutes to boot.
dmseg now outputs-

**[COLOR=#0000cd][FONT=courier new]https://paste.ubuntu.com/p/f7fdjcjDhr/[/FONT][/COLOR]**
[/FONT]

---

### Post by oldfred on 2019-09-14
Are you using snaps? It is the first thing I remove. I prefer standard apps.
       snapd.seeded.service @3min 20.246s [COLOR=#ff0000]+6min 33.902s [/COLOR]

      
 boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) & 
[https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead](https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead)

---

