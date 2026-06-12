---
title: "[SOLVED] manually run 'dpkg --configure -a'  failed"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by umairsaeed219 on 2008-02-15
unfortunately i was trying to install intel536 ep modem in my ubuntu 7.10
 from where the problem starts 
by mistake i downoad the deb package of **intel 537**not **536ep** 

when i run the driver of intel 537 it starts installing itself after some time installer stops and computer stoped responding 
i restart my pc and try to install it again remember that so for i have not realized that i was installing the wrong modem driver
it happend aging and installer stops working 

no when ever i try to install actual modem that is 536ep or try to update or refresh packages list(i also have dsl connection fo rlimited period) following message appears

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i have tried 
> dpkg --configure -a
but it stops at 

> umair@umair-desktop:~$ sudo dpkg --configure -a[sudo] password for umair:
Setting up intel537ep-gutsy (1.0) ...
Intel537EP Modem Driver and Boot Scripts copied successfully
Updating modules (/sbin/depmod)
Installing boot scripts
 System startup links for /etc/init.d/537_boot already exist.
Loading 537EP driver

what should i do  know?

---

### Post by taurus on 2008-02-15
What happens if you run these two commands from a terminal?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by umairsaeed219 on 2008-02-15
it produced the following out put

> umair@umair-desktop:~$ sudo apt-get update
[sudo] password for umair:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                 
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources                   
Fetched 4B in 6s (1B/s)                                                        
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
umair@umair-desktop:~$ 

---

### Post by Rocket2DMn on 2008-02-15
Do you have Synaptic open?  You can't run these commands when another package manager is running.

---

### Post by umairsaeed219 on 2008-02-15
not at all i was running firefox and teminal only nothing else

---

### Post by Rocket2DMn on 2008-02-15
Something is holding the lock, so you can't proceed until it releases.  You could try logging out and logging back in, or simply rebooting to free the lock.
It might've happened b/c your dpkg command froze up.

---

### Post by taurus on 2008-02-15
Or post the output of this command from a terminal to see which process is using adept.

```
ps -A
```

---

### Post by umairsaeed219 on 2008-02-15
I have restart my system as well as log off but nothing happend 
same response

i think you should look at this out put closely

> umair@umair-desktop:~$ sudo dpkg --configure -a
Setting up intel537ep-gutsy (1.0) ...
Intel537EP Modem Driver and Boot Scripts copied successfully
Updating modules (/sbin/depmod)
Installing boot scripts
 System startup links for /etc/init.d/537_boot already exist.
Loading 537EP driver

it stops at loading the driver 537 ep which is wrong actually i hav eintel 536ep
i have also tried this command as well but same problem 
> sudo rm /var/lib/dpkg/lock

---

### Post by umairsaeed219 on 2008-02-15
> **taurus said:**
> Or post the output of this command from a terminal to see which process is using adept.

```
ps -A
```
its ouput is

> umair@umair-desktop:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   26 ?        00:00:00 kblockd/0
   27 ?        00:00:00 kacpid
   28 ?        00:00:00 kacpi_notify
  116 ?        00:00:00 kseriod
  138 ?        00:00:00 pdflush
  139 ?        00:00:00 pdflush
  140 ?        00:00:00 kswapd0
  191 ?        00:00:00 aio/0
 2250 ?        00:00:00 ksuspend_usbd
 2251 ?        00:00:00 khubd
 2307 ?        00:00:01 ata/0
 2308 ?        00:00:00 ata_aux
 2324 ?        00:00:00 scsi_eh_0
 2325 ?        00:00:01 scsi_eh_1
 2617 ?        00:00:00 kjournald
 2894 ?        00:00:00 udevd
 3724 ?        00:00:00 kpsmoused
 4388 tty4     00:00:00 getty
 4389 tty5     00:00:00 getty
 4392 tty2     00:00:00 getty
 4400 tty3     00:00:00 getty
 4403 tty1     00:00:00 getty
 4404 tty6     00:00:00 getty
 4569 ?        00:00:00 acpid
 4611 ?        00:00:00 kondemand/0
 4682 ?        00:00:00 syslogd
 4739 ?        00:00:00 dd
 4741 ?        00:00:00 klogd
 4762 ?        00:00:00 dbus-daemon
 4778 ?        00:00:00 NetworkManager
 4792 ?        00:00:00 NetworkManagerD
 4805 ?        00:00:00 system-tools-ba
 4806 ?        00:00:00 dbus-daemon
 4825 ?        00:00:00 hald
 4826 ?        00:00:00 hald-runner
 4866 ?        00:00:00 hald-addon-keyb
 4867 ?        00:00:00 hald-addon-keyb
 4868 ?        00:00:00 hald-addon-keyb
 4871 ?        00:00:00 hald-addon-acpi
 4953 ?        00:00:00 cupsd
 4988 ?        00:00:00 hald-addon-stor
 5665 ?        00:00:02 clamd
 5874 ?        00:00:00 freshclam
 5993 ?        00:00:00 console-kit-dae
 6144 ?        00:00:00 avahi-daemon
 6145 ?        00:00:00 avahi-daemon
 6226 ?        00:00:00 dhcdbd
 6265 ?        00:00:00 hcid
 6280 ?        00:00:00 krfcommd
 6290 ?        00:00:00 bluetoothd-serv
 6310 ?        00:00:00 bluetoothd-serv
 6372 ?        00:00:00 dhclient
 6735 ?        00:00:00 gdm
 6736 ?        00:00:00 gdm
 6780 ?        00:00:00 atd
 6794 ?        00:00:00 cron
 7509 ?        00:00:00 dpkg
 7510 ?        00:00:00 intel537ep-guts
 7513 ?        00:00:00 537_boot
 7518 ?        00:00:00 bash
 7519 ?        00:00:03 modprobe
 7646 tty7     00:00:25 Xorg
 7666 ?        00:00:00 gnome-keyring-d
 7669 ?        00:00:00 x-session-manag
 7704 ?        00:00:00 ssh-agent
 7706 ?        00:00:00 gconfd-2
 7710 ?        00:00:00 dbus-daemon
 7712 ?        00:00:00 gnome-settings-
 7718 ?        00:00:00 compiz
 7723 ?        00:00:02 gnome-panel
 7727 ?        00:00:01 nautilus
 7730 ?        00:00:00 bonobo-activati
 7732 ?        00:00:00 gnome-volume-ma
 7736 ?        00:00:00 gnome-vfs-daemo
 7818 ?        00:00:00 gtk-window-deco
 7819 ?        00:00:03 compiz.real
 7823 ?        00:00:00 gnome-screensav
 7824 ?        00:00:00 vino-session
 7831 ?        00:00:00 bluetooth-apple
 7835 ?        00:00:00 update-notifier
 7839 ?        00:00:00 evolution-alarm
 7841 ?        00:00:00 trackerd
 7846 ?        00:00:00 python
 7850 ?        00:00:00 mapping-daemon
 7856 ?        00:00:00 nm-applet
 7858 ?        00:00:00 gnome-power-man
 7861 ?        00:00:00 trashapplet
 7882 ?        00:00:00 deskbar-applet
 7884 ?        00:00:00 gweather-applet
 7886 ?        00:00:00 evolution-data-
 7895 ?        00:00:00 evolution-excha
 7918 ?        00:00:00 mixer_applet2
 7923 ?        00:00:00 fast-user-switc
 7991 ?        00:00:00 multiload-apple
 8047 ?        00:00:00 firefox
 8059 ?        00:00:00 run-mozilla.sh
 8063 ?        00:00:45 firefox-bin
 8066 ?        00:00:00 notification-da
 8164 ?        00:00:00 gnome-terminal
 8167 ?        00:00:00 gnome-pty-helpe
 8168 pts/1    00:00:00 bash
 8185 pts/1    00:00:00 ps
umair@umair-desktop:~$

---

### Post by Dr Small on 2008-02-15
```
kill 7509
```

---

### Post by umairsaeed219 on 2008-02-16
how to kill it idont knw the commands

---

### Post by blackvd on 2008-02-16
in a terminal

```
kill -10 7509
```

---

### Post by tlsmith1138 on 2008-02-16
Same problem here after an install froze.

---

### Post by tlsmith1138 on 2008-02-16
PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
   25 ?        00:00:00 kblockd/0
   26 ?        00:00:00 kacpid
   27 ?        00:00:00 kacpi_notify
  172 ?        00:00:00 kseriod
  195 ?        00:00:00 pdflush
  196 ?        00:00:00 pdflush
  197 ?        00:00:00 kswapd0
  247 ?        00:00:00 aio/0
 2125 ?        00:00:00 ksuspend_usbd
 2126 ?        00:00:00 khubd
 2143 ?        00:00:00 ata/0
 2144 ?        00:00:00 ata_aux
 2462 ?        00:00:00 kjournald
 2521 ?        00:00:00 scsi_eh_1
 2522 ?        00:00:00 scsi_eh_2
 2559 ?        00:00:00 scsi_eh_3
 2560 ?        00:00:00 usb-storage
 2737 ?        00:00:00 udevd
 3711 ?        00:00:00 kpsmoused
 4308 tty4     00:00:00 getty
 4309 tty5     00:00:00 getty
 4312 tty2     00:00:00 getty
 4314 tty3     00:00:00 getty
 4315 tty1     00:00:00 getty
 4316 tty6     00:00:00 getty
 4476 ?        00:00:00 acpid
 4520 ?        00:00:00 kondemand/0
 4574 ?        00:00:00 syslogd
 4630 ?        00:00:00 dd
 4632 ?        00:00:00 klogd
 4653 ?        00:00:00 dbus-daemon
 4669 ?        00:00:00 NetworkManager
 4683 ?        00:00:00 NetworkManagerD
 4696 ?        00:00:00 system-tools-ba
 4697 ?        00:00:00 dbus-daemon
 4716 ?        00:00:00 hald
 4717 ?        00:00:00 hald-runner
 4767 ?        00:00:00 hald-addon-keyb
 4771 ?        00:00:00 hald-addon-keyb
 4772 ?        00:00:00 hald-addon-keyb
 4774 ?        00:00:00 hald-addon-cpuf
 4775 ?        00:00:00 hald-addon-acpi
 4804 ?        00:00:00 cupsd
 4807 ?        00:00:03 hald-addon-stor
 4809 ?        00:00:00 hald-addon-stor
 4821 ?        00:00:00 hald-addon-stor
 4837 ?        00:00:00 hald-addon-stor
 4840 ?        00:00:00 hald-addon-stor
 4860 ?        00:00:07 boinc_client
 4904 ?        00:00:00 gdomap
 5003 ?        00:00:00 xinetd
 5020 ?        00:00:00 console-kit-dae
 5118 ?        00:00:00 avahi-daemon
 5119 ?        00:00:00 avahi-daemon
 5133 ?        00:00:00 dhcdbd
 5168 ?        00:00:00 gdm
 5171 ?        00:00:09 gdm
 5176 tty7     00:07:23 Xorg
 5225 ?        00:00:00 dhclient
 5270 ?        00:00:00 atd
 5286 ?        00:00:00 cron
 5431 ?        00:00:00 timidity
 5716 ?        00:00:00 gnome-keyring-d
 5719 ?        00:00:00 x-session-manag
 5756 ?        00:00:00 ssh-agent
 5758 ?        00:00:01 gconfd-2
 5762 ?        00:00:00 dbus-daemon
 5764 ?        00:00:01 gnome-settings-
 5769 ?        00:00:00 sh
 5770 ?        00:00:00 esd
 5773 ?        00:00:00 compiz
 5775 ?        00:00:10 gnome-panel
 5777 ?        00:00:03 nautilus
 5779 ?        00:00:00 gnome-volume-ma
 5786 ?        00:00:00 bonobo-activati
 5831 ?        00:00:00 gnome-vfs-daemo
 5868 ?        00:00:01 gtk-window-deco
 5869 ?        00:00:14 compiz.real
 5870 ?        00:00:00 vino-session
 5871 ?        00:00:00 bluetooth-apple
 5873 ?        00:00:00 update-notifier
 5876 ?        00:00:00 evolution-alarm
 5883 ?        00:00:00 trackerd
 5885 ?        00:00:00 nm-applet
 5886 ?        00:00:00 python
 5890 ?        00:00:00 gnome-power-man
 5900 ?        00:00:07 gnome-screensav
 5911 ?        00:00:00 evolution-data-
 5919 ?        00:00:00 trashapplet
 5931 ?        00:00:00 evolution-excha
 5933 ?        00:00:00 mapping-daemon
 5955 ?        00:00:00 mixer_applet2
 5962 ?        00:00:01 deskbar-applet
 5986 ?        00:00:00 fast-user-switc
 9328 ?        00:00:00 firefox
 9340 ?        00:00:00 run-mozilla.sh
 9344 ?        00:00:58 firefox-bin
 9406 ?        00:00:00 gtk-gnash
 9425 ?        00:00:00 gnome-terminal
 9427 ?        00:00:00 gnome-pty-helpe
 9428 pts/0    00:00:00 bash
 9446 pts/0    00:00:00 ps

---

### Post by Rocket2DMn on 2008-02-16
umairsaeed219, the command for you would be
```
kill -9 7509
``` since 7509 is the process number of dpkg which is holding the lock.  You may have to end up rebooting anyway to free the lock.  You should not have run that rm command on the lock file, that could create major problems.  Please update us with the status of your problem - what works and what doesn't?

tlsmith1138, your problem seems to be different, you need to start a new thread to get help.  Post your problem on the forums and what you've tried and somebody will try and help you.

---

### Post by umairsaeed219 on 2008-02-17
no benefit
problem wasnt solved 
i ran the command 
> [umair@umair-desktop:~$ kill -9 7509
bash: kill: (7509) - No such process


then i try to download updates but following message appaers again

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by umairsaeed219 on 2008-02-17
no benefit
problem wasnt solved
i ran the command
Quote:
[umair@umair-desktop:~$ kill -9 7509
bash: kill: (7509) - No such process

then i try to download updates but following message appaers again

Quote:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

---

### Post by Rocket2DMn on 2008-02-17
Try running the dpkg command again
```
sudo dpkg --configure -a
```

---

### Post by umairsaeed219 on 2008-02-17
it never moves ahead

> umair@umair-desktop:~$ sudo dpkg --configure -a
[sudo] password for umair:
Setting up intel537ep-gutsy (1.0) ...
Intel537EP Modem Driver and Boot Scripts copied successfully
Updating modules (/sbin/depmod)
Installing boot scripts
 System startup links for /etc/init.d/537_boot already exist.
Loading 537EP driver

---

### Post by Rocket2DMn on 2008-02-18
I think you need to try removing that driver.  Since you installed it from a deb, you should be able to remove it from Synaptic.  You can then install the correct driver for your modem.

---

### Post by umairsaeed219 on 2008-02-18
i am unable to run the synaptic 

following message appears when i run it 
i am posting the screen shot

---

### Post by Rocket2DMn on 2008-02-18
OK, something got really really messed up.
What happens when you run:
```
sudo modprobe -r 537EP
sudo dpkg --configure -a
```
If that doesn't work, please post the output of
```
lsmod
```

Also, try rebooting into recovery mode and running the configure command (at the root terminal it boots you in to):
```
dpkg --configure -a
```

---

### Post by trig on 2008-02-18
desktop:~$  sudo dpkg --configure -a
dpkg: error processing libpng12-0 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 libpng12-0
trig@trig-desktop
any ideas what to do
i am looking but i cant seem to find libpng12-0

---

### Post by jpeddicord on 2008-02-18
Try:
```
sudo apt-get install libpng12-0
sudo dpkg-reconfigure libpng12-0
```

Also, could you post the output of:
```
cat /etc/apt/sources.list
```

If libpng12-0 isn't found, you most likely have a missing repository.

---

### Post by trig on 2008-02-18
thank you for the help, trig

---

### Post by xeth_delta on 2008-02-18
Has the problem been solved? You could start by erasing the cache, then ask the installer to finish the las operation:
```
sudo apt-get clean
sudo apt-get install -f
```
Then try again the suggestions the previous users have suggested. Also make sure there isn't any other package management process locking the database.

---

### Post by umairsaeed219 on 2008-02-19
Hello mr Rocket2DMn following are the results of the commands you asked me to run 

> umair@umair-desktop:~$ sudo modprobe -r 537EP
[sudo] password for umair:
FATAL: Module 537EP not found.
umair@umair-desktop:~$ sudo dpkg --configure -a
Setting up intel537ep-gutsy (1.0) ...
Intel537EP Modem Driver and Boot Scripts copied successfully
Updating modules (/sbin/depmod)
Installing boot scripts
 System startup links for /etc/init.d/537_boot already exist.
Loading 537EP driver

Then i tried > lsmod
> 
 its output is as follows 
umair@umair-desktop:~$ lsmod
Module                  Size  Used by
isofs                  36412  0 
udf                    87204  1 
ipv6                  273892  8 
xt_limit                3584  8 
xt_tcpudp               4224  10 
ipt_LOG                 7552  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5760  1 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11136  0 
xt_state                3456  6 
i915                   25856  2 
drm                    83348  3 i915
Intel537             4148996  1 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_userspace       5280  0 
cpufreq_ondemand        9612  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
sbs                    19592  0 
video                  18060  0 
container               5504  0 
ac                      6148  0 
dock                   10656  0 
button                  8976  0 
battery                11012  0 
lp                     12580  0 
snd_intel8x0           34972  3 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
serio_raw               8068  0 
psmouse                39952  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
pcspkr                  4224  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 34580  0 
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
pci_hotplug            32704  1 shpchp
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
i2c_i810                5892  0 
i2c_algo_bit            7428  1 i2c_i810
i2c_core               26112  2 i2c_i810,i2c_algo_bit
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
evdev                  11136  3 
iptable_nat             8708  0 
nf_nat                 20140  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19724  8 iptable_nat
nf_conntrack           65288  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0 
iptable_filter          3968  1 
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sg                     36764  0 
sd_mod                 30336  3 
floppy                 60004  0 
ata_piix               17540  3 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  4 sr_mod,sg,sd_mod,libata
e100                   37644  0 
mii                     6528  1 e100
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  3 ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmo

however i did not test it in recovery mode so for
i will give a try to it as well

---

### Post by umairsaeed219 on 2008-02-19
> **xeth_delta said:**
> Has the problem been solved? You could start by erasing the cache, then ask the installer to finish the las operation:
```
sudo apt-get clean
sudo apt-get install -f
```
Then try again the suggestions the previous users have suggested. Also make sure there isn't any other package management process locking the database.

following were the results
> 
umair@umair-desktop:~$ sudo apt-get clean
umair@umair-desktop:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
umair@umair-desktop:~$ 

---

### Post by Rocket2DMn on 2008-02-19
OK, we'll try again to remove the modem module (since we have the correct name now - Intel537), then reconfigure.
```
sudo modprobe -r Intel537
sudo depmod -a
sudo dpkg --configure -a
```

---

### Post by umairsaeed219 on 2008-02-19
i ran the command but it didnt move ahead
> umair@umair-desktop:~$ sudo modprobe -r Intel537

---

### Post by Rocket2DMn on 2008-02-19
Did it not even complete that one command?  If it completed it, try rebooting.  You can also try removing it from System->Administration->Bootup Menu or System->Administration->Services
Ultimately, we should just need to disable the Intel537 module, you can try looking into other ways to do that.

Otherwise you may need to compile yourself a new kernel, or just do a fresh install.

---

### Post by Hidetsu on 2008-02-19
I'm having the same problem,,,

I'm running 6.06 dapper in my 64 bit ubuntu, but can't update and can't configure

Anyone got any suggestion?
thanks

---

### Post by umairsaeed219 on 2008-02-20
it didnot completed the command

> sudo modprobe -r Intel537

what i have to do in menue system---->admin---->services

which servics i gave to abke or dsable

---

### Post by Rocket2DMn on 2008-02-20
OK, we've tried pretty much everything I can think of to fix this problem without a reinstall, but it seems to have locked up dpkg and we can't remove the module manually, so I'm beginning to foresee a fresh install in your future.

However, I can think of one last hope.  Forget about the Services for right now, the guide I am about to send you is for speeding up the boot process through a variety of means.  You should follow it with the purpose of removing the Intel537 module if possible (like if it shows it as an option).  This guide requires reading and thinking, so it is not for the faint of heart.
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
You don't need to follow the guide to the letter - you can skip parts, for example there is a lot of stuff you don't need to disable, and in fact, I would suggest fiddling with stuff that you know about and nothing else.  If you really want to focus on speeding boot, do that another time, after this problem is fixed.  Remember, the primary goal here is to get rid of the Intel537 module.

---

### Post by umairsaeed219 on 2008-02-21
> **Rocket2DMn said:**
> OK, we've tried pretty much everything I can think of to fix this problem without a reinstall, but it seems to have locked up dpkg and we can't remove the module manually, so I'm beginning to foresee a fresh install in your future.

However, I can think of one last hope.  Forget about the Services for right now, the guide I am about to send you is for speeding up the boot process through a variety of means.  You should follow it with the purpose of removing the Intel537 module if possible (like if it shows it as an option).  This guide requires reading and thinking, so it is not for the faint of heart.
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
You don't need to follow the guide to the letter - you can skip parts, for example there is a lot of stuff you don't need to disable, and in fact, I would suggest fiddling with stuff that you know about and nothing else.  If you really want to focus on speeding boot, do that another time, after this problem is fixed.  Remember, the primary goal here is to get rid of the Intel537 module.

Thanks dear for such a cooperation with me.
After alll i  have successfully configure the dpkg again and now i am very happy 
This task was acomplished by the same command which you and every user were referring to me i.e. >  dpkg --configure -a 

But according to instruction in one of your previous post i ran this command in recovery mode
it produces  a lot of output which iw as unable to understand
however following things i remembered
insmod:canot read intel537: nosuch file or directory
error: loadig intel 537
error :module intel is in use 

please read fie /user/share/eloc/intel537ep-feisty/source.txt

some thing like that as i cant remember exactly what was i nrecovery mode

After that i reboot the system and try to update my system by and no error messag e appears 
every thing goes smothly

---

### Post by Rocket2DMn on 2008-02-21
w00t!  It took a week, but I'm glad we got it - that makes it all worth it :)
Best Wishes.

---

### Post by umairsaeed219 on 2008-02-21
it was't possible without your countinuous help.
otherwise i have to reinstall it which i does not want to do.

---

### Post by xeth_delta on 2008-02-21
Glad you sorted it out! Good luck!

---

