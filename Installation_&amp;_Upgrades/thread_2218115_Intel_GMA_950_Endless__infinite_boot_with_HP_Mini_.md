---
title: "Intel GMA 950: Endless / infinite boot with HP Mini 2140 and Lubuntu 13.10"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by chatnoir2 on 2014-04-19
I am really a linux/ubuntu newbie and can't solve this issue. I  installed Lubuntu 13.10 on my old HP Mini 2140 netbook. It's running  Windows XP and I gave Lubuntu 30 GB of the same hard disk drive.  Everything is running fine and I even got the wireless broadcom running.  Unfortunately, the boot process during start-up usually ends up in an  infinite cycle. I have been reading tons of posts here and in other  forums and tried different GRUB settings but without success. The  Lubuntu splash screen is switching back and forth between endless debug  messages shown on the screen, i.e. it's flickering. If I press various key combinations (such  as ALT-CTRL-F8), it sometimes works and I get to the login screen. But  this only works in 50% of the cases, otherwise I have to restart the  netbook. If it works, however, Lubuntu runs absolutely flawless and,  yes, it's so much better and smoother than Windows!!! I already tried various options in GRUB, such as nosplash, i915.modeset=0, i915.modeset=1, nomodeset, and so on, but nothing keeps the splash screen from flickering.

  The boot.log in /var/logs look like this:

-------[FONT=system]
* Starting mDNS/DNS-SD daemon[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting CUPS printing spooler/server[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Starting Failsafe Boot Delay[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Stopping Failsafe Boot Delay[74G[ OK ]
 * Starting System V initialisation compatibility[74G[ OK ]
 * Starting modem connection manager[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting configure network device[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting network connection manager[74G[ OK ]
 * Starting configure network device[74G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting userspace bootsplash[74G[ OK ]
 * Starting Send an event to indicate plymouth is up[74G[ OK ]
 * Starting Bridge socket events into upstart[74G[ OK ]
 * Starting Bridge file events into upstart[74G[ OK ]
 * Stopping userspace bootsplash[74G[ OK ]
 * Stopping cold plug devices[74G[ OK ]
 * Stopping log initial device creation[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting save udev log and update rules[74G[ OK ]
 * Stopping save udev log and update rules[74G[ OK ]
 * Starting configure virtual network devices[74G[ OK ]
 * Starting AppArmor profiles       [128G 
[122G[ OK ]
 * Setting up X socket directories...       [128G 
[122G[ OK ]
 * Starting NTP server ntpd       [128G 
[122G[ OK ]
 * Restoring resolver state...       [128G 
[122G[ OK ]
 * Stopping System V initialisation compatibility[74G[ OK ]
 * Starting System V runlevel compatibility[74G[ OK ]
 * Starting [74G[ OK ]
 * Starting automatic crash report generation[74G[ OK ]
 * Starting [74G[ OK ]
 * Starting ACPI daemon[74G[ OK ]
 * Starting anac(h)ronistic cron[74G[ OK ]
 * Starting [74G[ OK ]
 * Starting [74G[ OK ]
 * Starting save kernel messages[74G[ OK ]
 * Starting [74G[ OK ]
 * Starting [74G[ OK ]
 * Starting Initializes zram swaping[74G[ OK ]
 * Starting crash report submission daemon[74G[ OK ]
 * Starting regular background program processing daemon[74G[ OK ]
 * Starting CPU interrupts balancing daemon[74G[ OK ]
 * Stopping System V runlevel compatibility[74G[ OK ]
 * Stopping save kernel messages[74G[ OK ][/FONT]
-------

Please let me know, if I need provide any other information such as dmesg, syslog and so on.
  Thanks for your help, it's highly appreciated.
  ChatNoir2

Edit: this might be important information. the laptop features an Intel GMA 950 graphics accelerator. Thx!!!

---

### Post by mörgæs on 2014-04-20
Hi, welcome to the fora.

How does it work if you install Lubuntu 14.04 having wired internet access during the install?

---

### Post by chatnoir2 on 2014-04-24
Hi ,
Unfortunately that did not help either. I tried to boot Lubuntu 14.04 with wired LAN and the splash screen was still flickering. Could it be that this is related to the graphics adapter in my HP Mini 2140? It's an an Intel GMA 950 and if I boot and use nosplash in GRUB it works perfectly (well I end up in the console and can't do much... if I start xwindows it won't run because it says it cannot find a geaphics adapter). 

Could it be that it's a problem that the HP Mini only has a max. resolution of 1024 x 576 ?

Thanks & best regards
CharNoir

---

### Post by mörgæs on 2014-04-24
Yes, the GMA 950 has always been a problem, and the only suggestion I have is googling. There are many threads on the topic but I can't judge which are worth trying, as I have not used the card myself. 
I'm sorry that I can't be of more help.

---

