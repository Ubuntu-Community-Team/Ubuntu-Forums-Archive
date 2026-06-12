---
title: "help system freeze"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by timbosity on 2008-09-18
Hi,

my laptop (amd XP 1.6ghz, 256 ram), running xubuntu hardy (upgraded from gutsy back when it came out), started yesterday having a few problems with freezing up after about 10 minutes uptime. At first I thought it was firefox-2 cos it only happenned when i was using it (never managed to get ff3 going properly lots of hang time, slow, heavy). However this evening i have rebooted five times after complete freezes doing normal stuff. What could be causing this? how can I diagnose? I would really like to fix this and get my laptop back to its full reliable working capacity. I DONT want to go back to windoze please help

cheers,

tim

---

### Post by chriswyatt on 2008-09-18
Try typing these two commands into a terminal and posting the results here:

```
lspci
```
This will show all the devices on your computer.

```
ps -e
```
This will show all the running processes on your computer.

I'm guessing it could be caused by hardware that isn't well supported in Ubuntu or a piece of software.  Probably not likely but it might be worth making sure your BIOS is up-to-date as well.

---

### Post by timbosity on 2008-09-18
Hi thanks for reply there. Here are the outputs from commands. System specifications:

tim@tim-laptop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:08.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:08.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:11.0 ISA bridge: VIA Technologies, Inc. VT8231 [PCI-to-ISA Bridge] (rev 10)
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.4 Bridge: VIA Technologies, Inc. VT8235 ACPI (rev 10)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 40)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 20)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 51)
01:00.0 VGA compatible controller: S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK) (rev 01)


processes:

tim@tim-laptop:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   41 ?        00:00:00 kblockd/0
   44 ?        00:00:00 kacpid
   45 ?        00:00:00 kacpi_notify
  116 ?        00:00:00 kseriod
  151 ?        00:00:00 pdflush
  152 ?        00:00:00 pdflush
  153 ?        00:00:00 kswapd0
  196 ?        00:00:00 aio/0
 1421 ?        00:00:00 ata/0
 1425 ?        00:00:00 ksuspend_usbd
 1432 ?        00:00:00 ata_aux
 1435 ?        00:00:00 khubd
 1445 ?        00:00:00 scsi_eh_0
 1450 ?        00:00:00 scsi_eh_1
 2344 ?        00:00:00 kjournald
 2532 ?        00:00:00 udevd
 2819 ?        00:00:00 pccardd
 2830 ?        00:00:00 pccardd
 2836 ?        00:00:00 kpsmoused
 3081 ?        00:00:00 kgameportd
 3779 ?        00:00:00 ntos_wq
 3780 ?        00:00:00 ndis_wq
 3781 ?        00:00:00 wrapndis_wq
 4264 tty4     00:00:00 getty
 4265 tty5     00:00:00 getty
 4269 tty2     00:00:00 getty
 4270 tty3     00:00:00 getty
 4273 tty6     00:00:00 getty
 4453 ?        00:00:00 acpid
 4503 ?        00:00:00 kondemand/0
 4556 ?        00:00:00 syslogd
 4612 ?        00:00:00 dd
 4614 ?        00:00:00 klogd
 4636 ?        00:00:00 dbus-daemon
 4652 ?        00:00:00 NetworkManager
 4666 ?        00:00:00 NetworkManagerD
 4679 ?        00:00:00 system-tools-ba
 4704 ?        00:00:00 avahi-daemon
 4705 ?        00:00:00 avahi-daemon
 4733 ?        00:00:00 cupsd
 4858 ?        00:00:00 dhcdbd
 4877 ?        00:00:00 hald
 4880 ?        00:00:00 console-kit-dae
 4942 ?        00:00:00 hald-runner
 4955 ?        00:00:00 hald-addon-inpu
 4962 ?        00:00:00 hald-addon-cpuf
 4963 ?        00:00:00 hald-addon-acpi
 4982 ?        00:00:00 hald-addon-stor
 4990 ?        00:00:00 hald-addon-stor
 5063 ?        00:00:00 gdm
 5064 ?        00:00:00 gdm
 5071 tty7     00:00:05 Xorg
 5097 ?        00:00:00 anacron
 5111 ?        00:00:00 atd
 5125 ?        00:00:00 cron
 5208 tty1     00:00:00 getty
 5245 ?        00:00:00 x-session-manag
 5351 ?        00:00:00 ssh-agent
 5355 ?        00:00:00 xfce-mcs-manage
 5358 ?        00:00:00 gconfd-2
 5359 ?        00:00:00 gnome-keyring-d
 5360 ?        00:00:00 xfwm4
 5362 ?        00:00:00 Thunar
 5364 ?        00:00:00 gam_server
 5365 ?        00:00:01 xfdesktop
 5369 ?        00:00:00 dbus-launch
 5370 ?        00:00:00 dbus-daemon
 5378 ?        00:00:00 xfce4-panel
 5380 ?        00:00:00 xfce4-menu-plug
 5381 ?        00:00:00 orage
 5382 ?        00:00:00 gnome-power-man
 5384 ?        00:00:00 xfce4-screensho
 5385 ?        00:00:00 update-notifier
 5387 ?        00:00:00 xfce4-verve-plu
 5388 ?        00:00:00 xfce4-mixer-plu
 5394 ?        00:00:00 thunar-tpa
 5397 ?        00:00:00 xfce4-mount-plu
 5403 ?        00:00:00 python
 5405 ?        00:00:00 nm-applet
 5408 ?        00:00:00 conky
 5462 ?        00:00:00 gnome-keyring-d
 5489 ?        00:00:01 notification-da
 5528 ?        00:00:00 wpa_supplicant
 5538 ?        00:00:00 xterm
 5539 pts/0    00:00:00 bash
 5556 ?        00:00:00 dhclient
 5640 pts/0    00:00:00 ps




the xfce temrinal was being a bit odd when i went to use it so i used xterm and so far there seems to be no freezing up...

how do i make sure bios is up to date?
when i booted up into winodws XP it was slow and froze too... although thats sortof expected and part of the reaon why ubuntu has been my OS of choice since I tried it out last year...

and on the by the by, are there any processes running there that are completely superfluous? 


again, thanks for any help

---

