---
title: "Gnome/X Window/Graphical Interface doesn't start after upgrading to 11.04"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by yeagle on 2011-04-30
Hello everyone,
i am new to Ubuntu, but already a big fan of it :). I have the following problem:

I just updated my Notebook (Lenovo y560 with i7) to the newest Ubuntu version 11.04 from 10.10. The upgrade process went fine - no problems. BUT after the restart, the booting process freezes after "checking battery state [ok]". the login screen doesn't come up - so no graphical interface :(. I restarted the system, but it still freezes (at the same point). Also bevor that happens, the screen flashes 3 or 4 times.
The good thing is - i can still acess tty1-6 and do things there.
So i tried to change my xorg.conf back to the old one (i had a backup of it), but that didn't help.

Hardware info (lspci) of my Notebook:
```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Madison [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
03:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
03:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)
05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
```I don't have a clue how to fix this problem ... hope someone can help :)

---

### Post by dino99 on 2011-04-30
try to boot in recovery mode ("shift" key down at bios end process to get grub menu) and select "repair packages"

---

### Post by lechien73 on 2011-04-30
What happens if you try Ctrl-Alt-F8, instead of F7?

From a terminal does ps show the GUI as running?

---

### Post by yeagle on 2011-04-30
First of all - thanks for you help :)
I always tried to enter the grub by pressing ESC (and that didn't work).

Ok, so I entered the grub and tried to repair the packages: The command doesn't make any changes to the system (0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded).
(I wanted to add a log file... but i didn't find out if there is one and where it is located - didn't find one in /var/log)

Now, since i can access the grub (thanks to you) i tried to start in failsafeX - and that works.

But, I still get the same error, when I start my Notebook normally and I still don't know why...

Here is my boot.log:
```
fsck from util-linux-ng 2.17.2 
/dev/sda1: clean, 289281/18808832 files, 30421684/75219968 blocks 
 * Stopping Flush boot log to disk[74G[ OK ] 
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
 * Starting AppArmor profiles       [80G  [74G[ OK ] 
 * Setting sensors limits       [80G  [74G[ OK ] 
 * Stopping System V initialisation compatibility[74G[ OK ] 
 * Starting System V runlevel compatibility[74G[ OK ] 
 [COLOR=Red]* Stopping automatic crash report generation[74G[[31mfail[39;49m][/COLOR] 
 * Starting eCryptfs[74G[ OK ] 
 * Starting restore sound card(s') mixer state(s)[74G[ OK ] 
 * Starting ACPI daemon[74G[ OK ] 
 * Starting save kernel messages[74G[ OK ] 
 * Stopping cold plug devices[74G[ OK ] 
 * Stopping log initial device creation[74G[ OK ] 
 * Starting CPU interrupts balancing daemon[74G[ OK ] 
 * Starting load fallback graphics devices[74G[ OK ] 
 * Starting enable remaining boot-time encrypted block devices[74G[ OK ] 
 * Starting configure network device security[74G[ OK ] 
 * Starting configure virtual network devices[74G[ OK ] 
 * Stopping configure virtual network devices[74G[ OK ] 
 * Starting save udev log and update rules[74G[ OK ] 
 * Stopping restore sound card(s') mixer state(s)[74G[ OK ] 
 * Stopping enable remaining boot-time encrypted block devices[74G[ OK ] 
 * Starting anac(h)ronistic cron[74G[ OK ] 
 * Stopping eCryptfs[74G[ OK ] 
 * Starting regular background program processing daemon[74G[ OK ] 
 * Starting deferred execution scheduler[74G[ OK ] 
 * Stopping load fallback graphics devices[74G[ OK ] 
 * Starting GNOME Display Manager[74G[ OK ] 
 * Stopping save udev log and update rules[74G[ OK ] 
 * Stopping save kernel messages[74G[ OK ] 
 * Starting ClamAV virus database updater freshclam       [128G  [122G[ OK ] 
speech-dispatcher disabled; edit /etc/default/speech-dispatcher 
 * Stopping anac(h)ronistic cron[74G[ OK ]
```the only unusual thing is the one i marked red. But I think that is not the reason, why gnome/xwindow (or whatever it is, that doesn't work) doesn't start...

---

### Post by yeagle on 2011-04-30
> **lechien73 said:**
> What happens if you try Ctrl-Alt-F8, instead of F7?

From a terminal does ps show the GUI as running?

sry - i didn't see your reply...
Thank you for your help :)

Ctrl-Alt-F8 doesn't do anything.

ps -A show's the following:
```
  PID TTY          TIME CMD
    1 ?        00:00:02 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 ksoftirqd/0
    6 ?        00:00:00 migration/0
    7 ?        00:00:00 migration/1
    9 ?        00:00:00 ksoftirqd/1
   11 ?        00:00:00 migration/2
   12 ?        00:00:00 kworker/2:0
   13 ?        00:00:00 ksoftirqd/2
   14 ?        00:00:00 migration/3
   16 ?        00:00:06 ksoftirqd/3
   17 ?        00:00:00 migration/4
   19 ?        00:00:00 ksoftirqd/4
   20 ?        00:00:00 migration/5
   21 ?        00:00:00 kworker/5:0
   22 ?        00:00:00 ksoftirqd/5
   23 ?        00:00:00 migration/6
   25 ?        00:00:00 ksoftirqd/6
   26 ?        00:00:00 migration/7
   28 ?        00:00:00 ksoftirqd/7
   29 ?        00:00:00 cpuset
   30 ?        00:00:00 khelper
   31 ?        00:00:00 netns
   33 ?        00:00:00 sync_supers
   34 ?        00:00:00 bdi-default
   35 ?        00:00:00 kintegrityd
   36 ?        00:00:00 kblockd
   37 ?        00:00:00 kacpid
   38 ?        00:00:00 kacpi_notify
   39 ?        00:00:00 kacpi_hotplug
   40 ?        00:00:00 ata_sff
   41 ?        00:00:00 khubd
   42 ?        00:00:00 md
   43 ?        00:00:05 kworker/0:2
   44 ?        00:00:01 kworker/1:1
   45 ?        00:00:00 kworker/2:1
   46 ?        00:00:00 kworker/3:1
   47 ?        00:00:01 kworker/4:1
   48 ?        00:00:01 kworker/5:1
   49 ?        00:00:03 kworker/6:1
   52 ?        00:00:00 khungtaskd
   53 ?        00:00:13 kswapd0
   54 ?        00:00:00 ksmd
   55 ?        00:00:00 fsnotify_mark
   56 ?        00:00:00 aio
   57 ?        00:00:00 ecryptfs-kthrea
   58 ?        00:00:00 crypto
   62 ?        00:00:00 kthrotld
   63 ?        00:00:00 kmpathd
   64 ?        00:00:00 kmpath_handlerd
   65 ?        00:00:00 kondemand
   66 ?        00:00:00 kconservative
  144 ?        00:00:00 kworker/6:2
  217 ?        00:00:01 kworker/3:2
  218 ?        00:00:00 scsi_eh_0
  219 ?        00:00:00 scsi_eh_1
  220 ?        00:00:00 scsi_eh_2
  221 ?        00:00:00 scsi_eh_3
  222 ?        00:00:00 scsi_eh_4
  223 ?        00:00:00 scsi_eh_5
  228 ?        00:00:03 kworker/u:6
  301 ?        00:00:00 jbd2/sda1-8
  302 ?        00:00:00 ext4-dio-unwrit
  354 ?        00:00:00 upstart-udev-br
  360 ?        00:00:00 udevd
  566 ?        00:00:00 edac-poller
  571 ?        00:00:00 cfg80211
  575 ?        00:00:00 kmemstick
  629 ?        00:00:00 kpsmoused
  757 ?        00:00:00 upstart-socket-
  766 ?        00:00:00 hci0
  767 ?        00:00:00 kworker/1:2
  787 ?        00:00:00 hd-audio0
  790 ?        00:00:00 hd-audio1
  870 ?        00:00:00 rsyslogd
  889 ?        00:00:00 dbus-daemon
  898 ?        00:00:00 NetworkManager
  899 ?        00:00:00 avahi-daemon
  900 ?        00:00:00 avahi-daemon
  917 ?        00:00:00 modem-manager
  928 ?        00:00:00 polkitd
  949 ?        00:00:00 cupsd
[COLOR=Lime]  958 ?        00:00:00 gdm-binary[/COLOR]
  962 ?        00:00:00 console-kit-dae
 1084 ?        00:00:00 wpa_supplicant
 1090 tty4     00:00:00 login
 1094 tty5     00:00:00 getty
 1120 tty6     00:00:00 getty
 1134 ?        00:00:00 acpid
 1157 ?        00:00:00 cron
 1158 ?        00:00:00 irqbalance
 1159 ?        00:00:00 atd
 1238 ?        00:00:00 freshclam
 1305 ?        00:00:00 bluetoothd
 1308 ?        00:00:00 l2cap
 1314 ?        00:00:00 kworker/4:2
 1317 ?        00:00:00 krfcommd
 1328 ?        00:00:00 atieventsd
 1445 ?        00:00:00 flush-8:0
 1492 tty1     00:00:00 login
 1495 tty2     00:00:00 login
 1655 tty2     00:00:01 bash
 2144 ?        00:00:00 udevd
 2145 ?        00:00:00 scsi_eh_6
 2146 ?        00:00:08 usb-storage
 2149 ?        00:00:00 udevd
 2854 ?        00:09:59 mount.ntfs
 2859 ?        00:00:07 flush-8:16
 4223 tty2     00:27:16 rsync
 4224 tty2     00:00:00 rsync
 4225 tty2     00:05:07 rsync
 4802 tty1     00:00:01 bash
 8021 ?        00:00:01 kworker/u:1
 8071 ?        00:00:00 kworker/7:0
 8367 ?        00:00:00 anacron
 9437 ?        00:00:00 sh
 9438 ?        00:00:00 run-parts
 9444 ?        00:00:00 apt
 9492 ?        00:00:00 sleep
 9493 tty3     00:00:00 login
 9617 tty3     00:00:00 bash
 9957 ?        00:00:01 kworker/0:3
10894 tty4     00:00:00 bash
11389 ?        00:00:00 kworker/7:2
12191 ?        00:00:00 kworker/0:0
12648 ?        00:00:00 kworker/u:0
12649 tty3     00:00:00 ps
```I was thinking that maybe someone was going to ask this - so i copied this yesterday, while backing up my files (so don't wonder about the rsync process).
I don't know which processes are needed for the gui to work, but there is one (makred green) called gdm-binary and it seems to be running.

EDIT: On booting it also says: Starting GNOME Dislpay Manager [ OK ]

---

### Post by nschubach on 2011-04-30
I think there's something terribly wrong with the upgrade process...

I was finally able to get to a browser after going to CTRL-ALT-F1, logging in and manually running 'unity' then ctrl-alt-f7 back to the gui session.  It doesn't seem to be starting up on boot.

If I 'killall -u <user>' on that prompt I can get the gui session to log out, but trying to load classic or any of the other options I still get nothing to load up besides recovery mode which only loads the command prompt.

This is with auto-login enabled... if I were a novice user, I'd be staring at a black screen with no options to run anything or clue on what I was supposed to do.

---

### Post by yeagle on 2011-04-30
Ok I solved the problem:

I started in failsafeX mode and reinstalled the ati graphics driver.

Now everythings works again as usual.

Thank you all for your help :)

---

