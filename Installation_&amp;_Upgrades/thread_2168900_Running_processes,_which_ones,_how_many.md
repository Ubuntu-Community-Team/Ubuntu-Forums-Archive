---
title: "Running processes, which ones, how many"
date: 2013-08-19
forum: Installation &amp; Upgrades
---

### Post by bob17 on 2013-08-19
I	an a new user of Ubuntu, and it is working very well. I did a UNIX	terminal command “ps -ef” and found about 250 processes running.	I am concerned that in the process of learning, I have loaded and	*NOT* unloaded software which needs to be cleaned up.



[LIST=1]	
[*]	[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Is	there an easy way to determine what should and shouldn't be running? This, of course, depends on the software loaded.[/FONT][/COLOR]

[*]	[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Is	there a Ubuntu tool to help newbies clean up their machines?
[/FONT][/COLOR]

[*]Should	one expect this many processes?
[/LIST]


[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Aforum search yielded a post by MikeCyber “what processes are normalon 13.04?” In his example, there are also a significant number ofrunning processes; however, his question and the answer is particularto a Union Bank process, and does not address the large number ofprocesses also running on his machine. 

I have reviewed many other postswhich are unrelated to my question.[/FONT][/COLOR]

---

### Post by sudodus on 2013-08-20
I have 160 processes running in a 32-bit installation of Ubuntu 12.04.2 LTS running lubuntu-desktop as found by

```
 ps -ef|wc -l
```

The corresponding figure for a 64-bit installation of Ubuntu 12.04.2 LTS running Unity is 166 (in another computer).

It could be perfectly normal with 250 processes, but if you are more specfic, you can get a better reply. How are you using the computer?

It will make a difference what computer it is (what hardware has drivers etc) and of course what services you have running. So please post the specification of your computer: Brand name and model, cpu, ram, graphics, network. And please post the list file that you get from the command

```
ps -ef > psef.txt
```

if there are no secrets there (for example: you can change the user name) or post the output of 

```
ps -A > psA.txt
```

Please post the output between code tags like this
 
[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

I might not be able to give a good answer afterwards, but I think ***someone***, who sees that information can.

You can install ***htop*** with the command line

```
sudo apt-get install htop
```

and run it in a terminal window.

```
htop
```

---

### Post by bob17 on 2013-08-20
Well, here it is, I have installed htop, but haven't run it yet, thanks Bob

Computer: 
Homebrew ASUS mother board rampage iii exterme (?), 
intel I7 processor, 
8GB ram, 
GeForce GTX260 graphics one hi res monotor attached, 
only one Western Digtial 500GB drive, 
only one OS, Ubuntu 12.04.2 AMD64, 
CD-DVD blueray
a single 100 base T network, not a server, connected hardwire to a router
have used Synaptic, load lots of stuff, it has worked perfectly and no errors, except once it failed to load, reboot solved problem.
KDE kickoff desk top
user, administrator "kels"


```

UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 08:13 ?        00:00:00 /sbin/init
root         2     0  0 08:13 ?        00:00:00 [kthreadd]
root         3     2  0 08:13 ?        00:00:02 [ksoftirqd/0]
root         6     2  0 08:13 ?        00:00:01 [migration/0]
root         7     2  0 08:13 ?        00:00:00 [watchdog/0]
root         8     2  0 08:13 ?        00:00:04 [migration/1]
root        10     2  0 08:13 ?        00:00:01 [ksoftirqd/1]
root        11     2  0 08:13 ?        00:00:00 [watchdog/1]
root        12     2  0 08:13 ?        00:00:01 [migration/2]
root        14     2  0 08:13 ?        00:00:01 [ksoftirqd/2]
root        15     2  0 08:13 ?        00:00:00 [watchdog/2]
root        16     2  0 08:13 ?        00:00:04 [migration/3]
root        18     2  0 08:13 ?        00:00:01 [ksoftirqd/3]
root        19     2  0 08:13 ?        00:00:00 [watchdog/3]
root        20     2  0 08:13 ?        00:00:00 [migration/4]
root        22     2  0 08:13 ?        00:00:00 [ksoftirqd/4]
root        23     2  0 08:13 ?        00:00:00 [watchdog/4]
root        24     2  0 08:13 ?        00:00:00 [migration/5]
root        26     2  0 08:13 ?        00:00:00 [ksoftirqd/5]
root        27     2  0 08:13 ?        00:00:00 [watchdog/5]
root        28     2  0 08:13 ?        00:00:00 [migration/6]
root        30     2  0 08:13 ?        00:00:00 [ksoftirqd/6]
root        31     2  0 08:13 ?        00:00:00 [watchdog/6]
root        32     2  0 08:13 ?        00:00:00 [migration/7]
root        34     2  0 08:13 ?        00:00:00 [ksoftirqd/7]
root        35     2  0 08:13 ?        00:00:00 [watchdog/7]
root        36     2  0 08:13 ?        00:00:00 [cpuset]
root        37     2  0 08:13 ?        00:00:00 [khelper]
root        38     2  0 08:13 ?        00:00:00 [kdevtmpfs]
root        39     2  0 08:13 ?        00:00:00 [netns]
root        41     2  0 08:13 ?        00:00:00 [sync_supers]
root        42     2  0 08:13 ?        00:00:00 [bdi-default]
root        43     2  0 08:13 ?        00:00:00 [kintegrityd]
root        44     2  0 08:13 ?        00:00:00 [kblockd]
root        45     2  0 08:13 ?        00:00:00 [ata_sff]
root        46     2  0 08:13 ?        00:00:00 [khubd]
root        47     2  0 08:13 ?        00:00:00 [md]
root        50     2  0 08:13 ?        00:00:07 [kworker/2:1]
root        51     2  0 08:13 ?        00:00:07 [kworker/3:1]
root        52     2  0 08:13 ?        00:00:01 [kworker/4:1]
root        55     2  0 08:13 ?        00:00:01 [kworker/7:1]
root        57     2  0 08:13 ?        00:00:00 [khungtaskd]
root        58     2  0 08:13 ?        00:00:00 [kswapd0]
root        59     2  0 08:13 ?        00:00:00 [ksmd]
root        60     2  0 08:13 ?        00:00:00 [khugepaged]
root        61     2  0 08:13 ?        00:00:00 [fsnotify_mark]
root        62     2  0 08:13 ?        00:00:00 [ecryptfs-kthrea]
root        63     2  0 08:13 ?        00:00:00 [crypto]
root        72     2  0 08:13 ?        00:00:00 [kthrotld]
root        74     2  0 08:13 ?        00:00:00 [scsi_eh_0]
root        75     2  0 08:13 ?        00:00:00 [scsi_eh_1]
root        76     2  0 08:13 ?        00:00:04 [kworker/u:2]
root        77     2  0 08:13 ?        00:00:00 [scsi_eh_2]
root        78     2  0 08:13 ?        00:00:00 [scsi_eh_3]
root        81     2  0 08:13 ?        00:00:00 [scsi_eh_4]
root        82     2  0 08:13 ?        00:00:00 [scsi_eh_5]
root        85     2  0 08:13 ?        00:00:00 [binder]
root       105     2  0 08:13 ?        00:00:00 [deferwq]
root       106     2  0 08:13 ?        00:00:00 [charger_manager]
root       107     2  0 08:13 ?        00:00:00 [devfreq_wq]
root       253     2  0 08:13 ?        00:00:00 [scsi_eh_6]
root       254     2  0 08:13 ?        00:00:00 [scsi_eh_7]
root       255     2  0 08:13 ?        00:00:00 [firewire]
root       303     2  0 08:13 ?        00:00:01 [jbd2/sda1-8]
root       304     2  0 08:13 ?        00:00:00 [ext4-dio-unwrit]
root       386     1  0 08:13 ?        00:00:00 upstart-udev-bridge --daemon
root       390     1  0 08:13 ?        00:00:00 /sbin/udevd --daemon
root       624     2  0 08:13 ?        00:00:00 [edac-poller]
root       675     2  0 08:13 ?        00:00:00 [kvm-irqfd-clean]
root       756     2  0 08:13 ?        00:00:00 [kpsmoused]
root       759     1  0 08:13 ?        00:00:00 upstart-socket-bridge --daemon
root       777     2  0 08:13 ?        00:00:00 [hd-audio0]
root       821     2  0 08:13 ?        00:00:00 [ttm_swap]
syslog     851     1  0 08:13 ?        00:00:00 rsyslogd -c5
root       874     2  0 08:13 ?        00:00:00 [rc0]
102        912     1  0 08:13 ?        00:00:03 dbus-daemon --system --fork --activation=upstart
root       938     1  0 08:13 ?        00:00:00 /usr/sbin/modem-manager
root       940     1  0 08:13 ?        00:00:00 /usr/sbin/bluetoothd
root       983     2  0 08:13 ?        00:00:00 [krfcommd]
root       984     1  0 08:13 ?        00:00:00 /usr/sbin/cupsd -F
root       999     1  0 08:13 ?        00:00:00 NetworkManager
root      1010     1  0 08:13 ?        00:00:01 /usr/lib/policykit-1/polkitd --no-debug
avahi     1014     1  0 08:13 ?        00:00:00 avahi-daemon: running [kels-ASUS.local]
avahi     1015  1014  0 08:13 ?        00:00:00 avahi-daemon: chroot helper
root      1025     1  0 08:13 tty4     00:00:00 /sbin/getty -8 38400 tty4
root      1032     1  0 08:13 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1043     1  0 08:13 tty2     00:00:00 /sbin/getty -8 38400 tty2
root      1044     1  0 08:13 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1051     1  0 08:13 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1072     1  0 08:13 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
whoopsie  1082     1  0 08:13 ?        00:00:00 whoopsie
root      1083     1  0 08:13 ?        00:00:07 /usr/sbin/irqbalance
root      1091     1  0 08:13 ?        00:00:00 lightdm
root      1114     1  0 08:13 ?        00:00:00 cron
daemon    1115     1  0 08:13 ?        00:00:00 atd
root      1118  1091  0 08:13 tty7     00:05:56 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
colord    1154     1  0 08:13 ?        00:00:00 /usr/lib/x86_64-linux-gnu/colord/colord
root      1317  1091  0 08:13 ?        00:00:00 lightdm --session-child 12 15
root      1328     1  0 08:13 tty1     00:00:00 /sbin/getty -8 38400 tty1
root      1330     1  0 08:13 ?        00:00:00 /usr/lib/accountsservice/accounts-daemon
root      1355     1  0 08:13 ?        00:00:00 /usr/sbin/console-kit-daemon --no-daemon
kels      1430  1317  0 08:13 ?        00:00:00 /bin/sh /usr/bin/startkde
root      1458   999  0 08:13 ?        00:00:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/sendsigs.omit.d/network-manager.dhclient-eth0.pid -lf /var/lib/dhcp/dhclient-7eac0a1c-f865-4a5d-b670-16b3c348be90-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
kels      1475  1430  0 08:13 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/kels/.gnupg/gpg-agent-info-kels-ASUS /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
kels      1476  1430  0 08:13 ?        00:00:00 /usr/bin/gpg-agent --daemon --sh --write-env-file=/home/kels/.gnupg/gpg-agent-info-kels-ASUS /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
kels      1479     1  0 08:13 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
kels      1480     1  0 08:13 ?        00:00:13 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
kels      1522     1  0 08:13 ?        00:00:00 /usr/lib/kde4/libexec/start_kdeinit +kcminit_startup
kels      1523     1  0 08:13 ?        00:00:00 kdeinit4: kdeinit4 Running...                  
kels      1524  1523  0 08:13 ?        00:00:02 kdeinit4: klauncher [kdeinit] --fd=9           
root      1528     2  0 08:13 ?        00:00:01 [flush-8:0]
nobody    1529   999  0 08:13 ?        00:00:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.0.1 --conf-file=/var/run/nm-dns-dnsmasq.conf --cache-size=0 --proxy-dnssec
kels      1562     1  0 08:13 ?        00:00:03 kdeinit4: kded4 [kdeinit]                      
kels      1566     1  0 08:13 ?        00:00:00 /usr/bin/kglobalaccel
kels      1568     1  0 08:13 ?        00:00:00 /usr/bin/kwalletd
kels      1573     1  0 08:13 ?        00:00:00 /usr/bin/kactivitymanagerd
root      1575     1  0 08:13 ?        00:00:00 /usr/lib/upower/upowerd
kels      1594  1430  0 08:13 ?        00:00:00 kwrapper4 ksmserver
kels      1595  1523  0 08:13 ?        00:00:00 kdeinit4: ksmserver [kdeinit]                  
root      1620     1  0 08:13 ?        00:00:05 /usr/lib/udisks/udisks-daemon
root      1625  1620  0 08:13 ?        00:00:00 udisks-daemon: not polling any devices
kels      1631  1595  0 08:13 ?        00:02:55 kwin
kels      1780     1  0 08:13 ?        00:00:01 /usr/bin/knotify4
kels      1783     1  0 08:13 ?        00:05:31 /usr/bin/plasma-desktop
kels      1787     1  0 08:13 ?        00:00:00 /usr/bin/kuiserver
kels      1809  1783  0 08:13 ?        00:00:00 ksysguardd
kels      1812     1  0 08:13 ?        00:00:02 /usr/bin/akonadi_control
kels      1814  1812  0 08:13 ?        00:00:03 akonadiserver
kels      1817  1814  0 08:13 ?        00:00:07 /usr/sbin/mysqld --defaults-file=/home/kels/.local/share/akonadi/mysql.conf --datadir=/home/kels/.local/share/akonadi/db_data/ --socket=/home/kels/.local/share/akonadi/socket-kels-ASUS/mysql.socket
kels      1831     1  0 08:13 ?        00:00:01 /usr/bin/kaccess
kels      1845  1523  0 08:13 ?        00:00:00 /usr/bin/nepomukserver
kels      1848  1845  0 08:13 ?        00:00:04 /usr/bin/nepomukservicestub nepomukstorage
kels      1849  1523  0 08:13 ?        00:00:00 /usr/lib/deja-dup/deja-dup/deja-dup-monitor
kels      1854  1523  0 08:13 ?        00:00:00 /usr/bin/zeitgeist-datahub
kels      1857  1523  0 08:13 ?        00:00:01 python /usr/bin/printer-applet
kels      1864     1  0 08:13 ?        00:00:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     1868     1  0 08:13 ?        00:00:00 /usr/lib/rtkit/rtkit-daemon
kels      1869     1  0 08:13 ?        00:00:18 /usr/bin/krunner
kels      1870     1  0 08:13 ?        00:00:00 /usr/lib/kde4/libexec/polkit-kde-authentication-agent-1
kels      1873     1  0 08:13 ?        00:00:00 /usr/bin/akonaditray
kels      1877     1  0 08:13 ?        00:00:05 /usr/bin/zeitgeist-daemon
kels      1879     1  0 08:13 ?        00:00:00 /usr/bin/korgac --icon korgac
kels      1881     1  0 08:13 ?        00:00:01 /usr/bin/nepomukcontroller
kels      1883     1  0 08:13 ?        00:00:00 /usr/bin/klipper
kels      1885     1  0 08:13 ?        00:00:00 /usr/bin/kmix
kels      1890     1  0 08:13 ?        00:00:05 /usr/lib/zeitgeist/zeitgeist-fts
kels      1898  1890  0 08:13 ?        00:00:00 /bin/cat
kels      1901     1  0 08:13 ?        00:00:01 /usr/lib/gvfs/gvfsd
kels      1903     1  0 08:13 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon -f /home/kels/.gvfs
kels      1905     1  0 08:13 ?        00:00:00 /usr/lib/gvfs/gvfsd-http --spawner :1.46 /org/gtk/gvfs/exec_spaw/0
kels      1918     1  0 08:13 ?        00:00:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
kels      1920     1  0 08:13 ?        00:00:01 /usr/lib/gvfs/gvfs-afc-volume-monitor
kels      1923     1  0 08:13 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
kels      1931  1864  0 08:13 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
kels      1933     1  0 08:13 ?        00:00:00 /usr/lib/x86_64-linux-gnu/gconf/gconfd-2
kels      1941  1848  0 08:13 ?        00:00:11 /usr/bin/virtuoso-t +foreground +configfile /tmp/virtuoso_hX1848.ini +wait
kels      1953  1812  0 08:13 ?        00:00:00 /usr/bin/akonadi_agent_launcher akonadi_akonotes_resource akonadi_akonotes_resource_0
kels      1954  1812  0 08:13 ?        00:00:00 /usr/bin/akonadi_agent_launcher akonadi_ical_resource akonadi_ical_resource_0
kels      1955  1812  0 08:13 ?        00:00:00 /usr/bin/akonadi_agent_launcher akonadi_maildir_resource akonadi_maildir_resource_0
kels      1956  1812  0 08:13 ?        00:00:00 /usr/bin/akonadi_maildispatcher_agent --identifier akonadi_maildispatcher_agent
kels      1957  1812  0 08:13 ?        00:00:00 /usr/bin/akonadi_mailfilter_agent --identifier akonadi_mailfilter_agent
kels      1958  1812  0 08:13 ?        00:00:00 /usr/bin/akonadi_nepomuk_feeder --identifier akonadi_nepomuk_feeder
kels      2017  1845  0 08:13 ?        00:00:03 /usr/bin/nepomukservicestub nepomukfileindexer
kels      2018  1845  0 08:13 ?        00:00:01 /usr/bin/nepomukservicestub nepomukfilewatch
kels      2019  1845  0 08:13 ?        00:00:00 /usr/bin/nepomukservicestub nepomukbackupsync
kels      2020  1845  0 08:13 ?        00:00:00 /usr/bin/nepomukservicestub nepomukqueryservice
kels      2096     1  0 08:17 ?        00:00:00 /home/kels/Eclipse/eclipse/eclipse Kepler
kels      2097  2096  0 08:17 ?        00:02:45 /usr/bin/java -jar /home/kels/Eclipse/eclipse/plugins/org.eclipse.equinox.launcher_1.3.0.v20130327-1440.jar -os linux -ws gtk -arch x86_64 -showsplash -launcher /home/kels/Eclipse/eclipse/eclipse Kepler -name Eclipse Kepler --launcher.library /home/kels/Eclipse/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.v20130521-0416/eclipse_1506.so -startup /home/kels/Eclipse/eclipse/plugins/org.eclipse.equinox.launcher_1.3.0.v20130327-1440.jar --launcher.overrideVmargs -exitdata 178027 -vm /usr/bin/java -vmargs -jar /home/kels/Eclipse/eclipse/plugins/org.eclipse.equinox.launcher_1.3.0.v20130327-1440.jar
root      2617     2  0 08:54 ?        00:00:00 [kworker/2:0]
root      2631     2  0 08:55 ?        00:00:00 [kworker/5:0]
kels      2856  1783  0 09:03 ?        00:00:12 /usr/bin/nautilus
kels      2862     1  0 09:03 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.46 /org/gtk/gvfs/exec_spaw/1
kels      2866     1  0 09:03 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.46 /org/gtk/gvfs/exec_spaw/2
kels      2868     1  0 09:03 ?        00:00:00 /usr/lib/dconf/dconf-service
kels      2873     1  0 09:03 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
root      2888     2  0 09:06 ?        00:00:00 [kworker/7:0]
root      3030     2  0 09:21 ?        00:00:01 [kworker/6:2]
kels      3248  1523  0 09:40 ?        00:00:00 /usr/lib/kde4/libexec/kio_http_cache_cleaner
kels     10375     1  0 10:21 ?        00:00:06 /usr/bin/khelpcenter
root     15976     2  0 14:31 ?        00:00:00 [kworker/4:0]
root     16034     2  0 14:33 ?        00:00:00 [kworker/1:2]
root     16078     2  0 14:35 ?        00:00:00 [kworker/5:2]
root     16145     2  0 14:38 ?        00:00:09 [kworker/1:0]
root     16176     2  0 14:40 ?        00:00:00 [kworker/3:0]
kels     16255  1523  0 14:47 ?        00:00:01 /usr/bin/dolphin --icon system-file-manager -caption Dolphin
root     16497     2  0 16:16 ?        00:00:00 [scsi_eh_17]
root     16498     2  0 16:16 ?        00:00:00 [usb-storage]
root     16501     2  0 16:16 ?        00:00:00 [kworker/u:1]
root     16502   390  0 16:16 ?        00:00:00 /sbin/udevd --daemon
root     16503   390  0 16:16 ?        00:00:00 /sbin/udevd --daemon
root     16515     2  0 16:16 ?        00:00:00 [kworker/6:1]
kels     16524  1523  0 16:16 ?        00:00:06 /usr/bin/dolphin --icon system-file-manager -caption Dolphin /media/28C8-4B54
kels     16552  1523  0 16:17 ?        00:00:42 /opt/google/chrome/chrome       
kels     16557 16552  0 16:17 ?        00:00:00 /opt/google/chrome/chrome       
kels     16558 16552  0 16:17 ?        00:00:00 /opt/google/chrome/chrome-sandbox /opt/google/chrome/chrome --type=zygote
kels     16559 16558  0 16:17 ?        00:00:00 /opt/google/chrome/chrome --type=zygote
kels     16563 16559  0 16:17 ?        00:00:00 /opt/google/chrome/nacl_helper_bootstrap /opt/google/chrome/nacl_helper --reserved_at_zero=0x0000000000000000 --r_debug=0x0000000000213000
kels     16564 16559  0 16:17 ?        00:00:00 /opt/google/chrome/chrome --type=zygote
kels     16641 16564  0 16:17 ?        00:00:23 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AsyncDns/AsyncDnsA/ForceCompositingMode/disable/InfiniteCache/No/OmniboxStopTimer/UseStopTimer/Prerender/PrerenderEnabled/SendFeedbackLinkLocation/alt-location/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Control/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_03/UMA-Uniformity-Trial-1-Percent/group_43/UMA-Uniformity-Trial-10-Percent/group_03/UMA-Uniformity-Trial-20-Percent/group_04/UMA-Uniformity-Trial-5-Percent/group_01/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --disable-webgl --disable-pepper-3d --disable-gl-multisampling --disable-accelerated-compositing --disable-accelerated-2d-canvas --disable-accelerated-video-decode --channel=16552.1.1812550338
kels     16700  1523  0 16:18 ?        00:00:03 /usr/lib/kde4/libexec/kdesu -u root -c /usr/sbin/synaptic
kels     16702     1  0 16:18 ?        00:00:00 /usr/lib/kde4/libexec/kdesud
root     16705 16700  0 16:18 pts/1    00:00:00 /usr/bin/sudo -u root /usr/lib/kde4/libexec/kdesu_stub -
root     16710 16700  0 16:18 pts/2    00:00:00 /usr/bin/sudo -u root /usr/lib/kde4/libexec/kdesu_stub -
root     16711 16710  0 16:18 pts/2    00:00:00 /usr/lib/kde4/libexec/kdesu_stub -
root     16714 16711  0 16:18 ?        00:00:00 sh -c /usr/sbin/synaptic
root     16715 16714  0 16:18 ?        00:00:10 /usr/sbin/synaptic
root     16720     1  0 16:18 ?        00:00:00 dbus-launch --autolaunch=82a25e2145f13c205076674500000006 --binary-syntax --close-stderr
root     16721     1  0 16:18 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
root     16739 16715  0 16:20 ?        00:00:00 [synaptic] <defunct>
kels     17302  1783  0 16:37 ?        00:00:05 /usr/bin/pdfedit
kels     17374 16564  0 16:52 ?        00:00:09 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AsyncDns/AsyncDnsA/ForceCompositingMode/disable/InfiniteCache/No/OmniboxStopTimer/UseStopTimer/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderEnabled/SendFeedbackLinkLocation/alt-location/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Control/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_03/UMA-Uniformity-Trial-1-Percent/group_43/UMA-Uniformity-Trial-10-Percent/group_03/UMA-Uniformity-Trial-20-Percent/group_04/UMA-Uniformity-Trial-5-Percent/group_01/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --disable-webgl --disable-pepper-3d --disable-gl-multisampling --disable-accelerated-compositing --disable-accelerated-2d-canvas --disable-accelerated-video-decode --channel=16552.7.1676980507
kels     17499     1  0 17:07 ?        00:00:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
root     18025     2  0 19:57 ?        00:00:00 [kworker/0:2]
kels     18140 16564  0 20:43 ?        00:00:00 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AsyncDns/AsyncDnsA/ForceCompositingMode/disable/InfiniteCache/No/OmniboxStopTimer/UseStopTimer/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderEnabled/SendFeedbackLinkLocation/alt-location/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Control/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_03/UMA-Uniformity-Trial-1-Percent/group_43/UMA-Uniformity-Trial-10-Percent/group_03/UMA-Uniformity-Trial-20-Percent/group_04/UMA-Uniformity-Trial-5-Percent/group_01/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --disable-webgl --disable-pepper-3d --disable-gl-multisampling --disable-accelerated-compositing --disable-accelerated-2d-canvas --disable-accelerated-video-decode --channel=16552.14.792576213
kels     18160 16564  1 20:44 ?        00:00:08 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AsyncDns/AsyncDnsA/ForceCompositingMode/disable/InfiniteCache/No/OmniboxStopTimer/UseStopTimer/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderEnabled/SendFeedbackLinkLocation/alt-location/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Control/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_03/UMA-Uniformity-Trial-1-Percent/group_43/UMA-Uniformity-Trial-10-Percent/group_03/UMA-Uniformity-Trial-20-Percent/group_04/UMA-Uniformity-Trial-5-Percent/group_01/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --disable-webgl --disable-pepper-3d --disable-gl-multisampling --disable-accelerated-compositing --disable-accelerated-2d-canvas --disable-accelerated-video-decode --channel=16552.16.1577193365
kels     18168 16564  0 20:44 ?        00:00:01 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AsyncDns/AsyncDnsA/ForceCompositingMode/disable/InfiniteCache/No/OmniboxStopTimer/UseStopTimer/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderEnabled/SendFeedbackLinkLocation/alt-location/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Control/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_03/UMA-Uniformity-Trial-1-Percent/group_43/UMA-Uniformity-Trial-10-Percent/group_03/UMA-Uniformity-Trial-20-Percent/group_04/UMA-Uniformity-Trial-5-Percent/group_01/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --disable-webgl --disable-pepper-3d --disable-gl-multisampling --disable-accelerated-compositing --disable-accelerated-2d-canvas --disable-accelerated-video-decode --channel=16552.17.1410378084
root     18186     2  0 20:47 ?        00:00:00 [kworker/0:1]
kels     18196 16564  0 20:49 ?        00:00:01 /opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AsyncDns/AsyncDnsA/ForceCompositingMode/disable/InfiniteCache/No/OmniboxStopTimer/UseStopTimer/Prerender/PrerenderEnabled/PrerenderFromOmnibox/OmniboxPrerenderEnabled/SendFeedbackLinkLocation/alt-location/Test0PercentDefault/group_01/UMA-Dynamic-Binary-Uniformity-Trial/default/UMA-New-Install-Uniformity-Trial/Control/UMA-Session-Randomized-Uniformity-Trial-5-Percent/group_03/UMA-Uniformity-Trial-1-Percent/group_43/UMA-Uniformity-Trial-10-Percent/group_03/UMA-Uniformity-Trial-20-Percent/group_04/UMA-Uniformity-Trial-5-Percent/group_01/UMA-Uniformity-Trial-50-Percent/default/ --renderer-print-preview --disable-webgl --disable-pepper-3d --disable-gl-multisampling --disable-accelerated-compositing --disable-accelerated-2d-canvas --disable-accelerated-video-decode --channel=16552.19.333639441
kels     18632  1523  0 20:51 ?        00:00:00 /usr/lib/libreoffice/program/oosplash --writer
kels     18649 18632  0 20:51 ?        00:00:00 /usr/lib/libreoffice/program/soffice.bin --writer --splash-pipe=6
kels     18663  1523  0 20:51 ?        00:00:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-kels/klauncherhX1524.slave-socket local:/tmp/ksocket-kels/dolphinW16255.slave-socket
kels     18664  1523  0 20:51 ?        00:00:00 kdeinit4: kio_file [kdeinit] file local:/tmp/ksocket-kels/klauncherhX1524.slave-socket local:/tmp/ksocket-kels/dolphinh16524.slave-socket
kels     18668     1  0 20:51 ?        00:00:00 /usr/bin/konsole
kels     18670 18668  0 20:51 pts/7    00:00:00 /bin/bash
root     18728     2  0 20:52 ?        00:00:00 [kworker/0:0]
kels     18729 18670  0 20:52 pts/7    00:00:00 ps -ef

```

---

### Post by sudodus on 2013-08-21
I see that you have a lot of KDE stuff running. Do I understand correctly, that you have installed Ubuntu, and are running KDE kickoff desk top (not any 'standard Ubuntu' desktop like Unity)? In that case I think the high number of processes is because of that. 

You could check if a clean Kubuntu install would result in fewer processes, but on the other hand, if your system is doing fine, I don't see any reason to worry.

-o-

As usual, take backups regularly, so that you can at least restore all your personal files. If you don't want to reinstall your system, you should consider a full backup of your personal files as well as the system.

Edit: You can also install Ubuntu-Tweak according to this link
 [http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-0-7-0-in-ubuntu-12-04-precise.html](http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-0-7-0-in-ubuntu-12-04-precise.html)

---

### Post by VMC on 2013-08-21
I'm not running kubuntu right now, but my ubuntu 12.04 has 159 processes. I'll kubuntu later on. For one thing, I noticed, you have [FONT=arial]"[COLOR=#000000]ibreoffice, klipper, dolphin" and several other programs running.

I have disabled "[/COLOR][COLOR=#000000]nepomukserver, [/COLOR][COLOR=#000000]akonadi, [/COLOR][COLOR=#000000]zeitgeist" on my system, so they are not running.

Ok, I'm on Kubuntu Saucy right now, and I have **144** processes. Several are from Chrome.[/COLOR][/FONT]

---

### Post by tgalati4 on 2013-08-21
From your GRUB menu boot into a Rescue  Console--which is a root terminal.  Run htop and look through the processes--those would be the bare minimum for your setup.  Be mindful that Chrome spins out a lot of threads (processes).  Each tab is a jail and gets its own thread.  Most linux machines will do OK until you get to around 4,000 processes, then things fall apart quickly.

---

### Post by bob17 on 2013-08-21
Thanks everyone for spending time on this thread, I think looking forward i need the following:
1) a link for a manual for "htop" describing the column meanings and etc. (perhaps a "top" is what i should search for)
2) a link describing Ubuntu start up scripting.
With this info i think i can work on my own and if necessary request more information with a better description.

---

### Post by sudodus on 2013-08-22
You can find a lot browsing the internet for ***htop tutorial*** for example

[http://xahlee.info/linux/linux_monitor_processes.html](http://xahlee.info/linux/linux_monitor_processes.html)

[http://xahlee.info/linux/linux_monitor_processes_htop.html](http://xahlee.info/linux/linux_monitor_processes_htop.html)

I'll pass on the second question.

---

### Post by SeijiSensei on 2013-08-22
I don't see anything out of line in that list you presented above.  I'm using Kubuntu 13.04, and top reports I have about 235 processes running.  You can see which processes belong to you in that listing above since they have user "kels" listed as their owner rather than "root."

To see the minimal number of processes you would use in a standard session, close all the programs currently running in the task bar, then reboot.  After you log in, open Konsole and run "top".  I'd bet you'll see a number in the 150-200 range even before running any desktop applications like Chrome or LibreOffice.

As for startup scripts, you should begin by reading about [Upstart](http://upstart.ubuntu.com/), Ubuntu's replacement for the traditional SysV init system used on *nix.  You can also browse the scripts that came with your machine for hints about structure; they are stored in /etc/init.d/.

However [many processes are managed by KDE itself]("http://techbase.kde.org/KDE_System_Administration/Startup"), not Upstart.  You can also specify scripts to run when KDE starts up using its [Autostart](http://docs.kde.org/stable/en/kde-workspace/kcontrol/autostart/) functionality.

---

### Post by vasa1 on 2013-08-22
> **SeijiSensei said:**
> I don't see anything out of line in that list you presented above. ....
OP has processes for both Nautilus and Dolphin. Then there's zeitgeist and nepomuk (the KDE equivalent)? It's almost as if OP has two DEs going at one time. At least that's the impression I get going through the list.

---

### Post by SeijiSensei on 2013-08-23
So zeitgeist is some GNOME-based program?  Nepomuk is a desktop search engine that comes by default with KDE.

We're still not talking about many processes, though, from his 250 or so.  My earlier comment had more to do with whether there were any suspect processes running.  While I didn't recognize zeitgeist and didn't notice Nautilus, I didn't see anything disturbing.

Yes, it would probably be better if he didn't run both GNOME and KDE applications that duplicate functions, like Dolphin and Nautilus do, since it would limit the number of libraries in use.  I use Firefox and Thunderbird by default, so I'm used to running GTK+ applications in a KDE environment and don't think of it as all that unusual.

---

