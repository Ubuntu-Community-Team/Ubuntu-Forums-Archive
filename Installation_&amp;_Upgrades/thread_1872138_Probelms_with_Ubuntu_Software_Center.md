---
title: "Probelms with Ubuntu Software Center"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by kurotmiedignat on 2011-10-30
Hi,
I haven't installed ubuntu on my hard disk yet but yesterday i began using Ubuntu11.10 from my usb stick. I managed to install flash player on my ubuntu. However, i had some problems with my battery and therefore my PC had a messy shutdown. Ever since, i could not start Ubuntu Software Center. I need this program because I need to reinstall Flash Player. I don't know why but apparently the installation wasn't permanent. Meanwhile, i have tried typing 

sudo apt-get upgrade

and I got this message: 

[COLOR=red]E: Could not open lock file /var/lib/apt/lists/lock - open (22: Invalid argument)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (22: Invalid argument)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/COLOR]

I have done some research on the Internet and I found a site that suggested deleting some lock files. So, I have tried doing:

[COLOR=red]ubuntu@ubuntu:~$ sudo rm /var/lib/dpkg/lock
rm: cannot remove `/var/lib/dpkg/lock': Invalid argument
ubuntu@ubuntu:~$ sudo rm /var/cache/apt/archives/lock
rm: cannot remove `/var/cache/apt/archives/lock': No such file or directory
ubuntu@ubuntu:~$ sudo rm /var/lib/apt/lists/lock
rm: cannot remove `/var/lib/apt/lists/lock': Invalid argument[/COLOR]

As you can see, I had some problems. Then, I found another site that said that probably these files are still in use cause my PC didn't terminate well. However, I am having problems on locating these processes. This is what I get when I do:

ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 09:20 ?        00:00:00 /sbin/init
root         2     0  0 09:20 ?        00:00:00 [kthreadd]
root         3     2  0 09:20 ?        00:00:01 [ksoftirqd/0]
root         6     2  0 09:20 ?        00:00:00 [migration/0]
root         7     2  0 09:20 ?        00:00:00 [migration/1]
root         9     2  0 09:20 ?        00:00:00 [ksoftirqd/1]
root        11     2  0 09:20 ?        00:00:00 [cpuset]
root        12     2  0 09:20 ?        00:00:00 [khelper]
root        13     2  0 09:20 ?        00:00:00 [netns]
root        15     2  0 09:20 ?        00:00:00 [sync_supers]
root        16     2  0 09:20 ?        00:00:00 [bdi-default]
root        17     2  0 09:20 ?        00:00:00 [kintegrityd]
root        18     2  0 09:20 ?        00:00:00 [kblockd]
root        19     2  0 09:21 ?        00:00:00 [ata_sff]
root        20     2  0 09:21 ?        00:00:00 [khubd]
root        21     2  0 09:21 ?        00:00:00 [md]
root        23     2  0 09:21 ?        00:00:00 [khungtaskd]
root        24     2  0 09:21 ?        00:00:00 [kswapd0]
root        25     2  0 09:21 ?        00:00:00 [ksmd]
root        26     2  0 09:21 ?        00:00:00 [khugepaged]
root        27     2  0 09:21 ?        00:00:00 [fsnotify_mark]
root        28     2  0 09:21 ?        00:00:00 [ecryptfs-kthrea]
root        29     2  0 09:21 ?        00:00:00 [crypto]
root        37     2  0 09:21 ?        00:00:00 [kthrotld]
root       166     2  0 09:21 ?        00:00:00 [scsi_eh_0]
root       182     2  0 09:21 ?        00:00:00 [scsi_eh_1]
root       185     2  0 09:21 ?        00:00:00 [scsi_eh_2]
root       188     2  0 09:21 ?        00:00:00 [scsi_eh_3]
root       204     2  0 09:21 ?        00:00:00 [kworker/u:3]
root       205     2  0 09:21 ?        00:00:00 [kworker/u:4]
root       222     2  0 09:21 ?        00:00:00 [ttm_swap]
root       251     2  0 09:21 ?        00:00:00 [scsi_eh_4]
root       253     2  0 09:21 ?        00:00:01 [usb-storage]
root       491     2  0 09:21 ?        00:00:00 [loop0]
root       704     2  0 09:21 ?        00:00:01 [loop1]
root       901     2  0 09:21 ?        00:00:00 [flush-7:1]
root       902     2  0 09:21 ?        00:00:00 [flush-8:16]
root      2314     1  0 09:21 ?        00:00:00 upstart-udev-bridge --daemon
syslog    2323     1  0 09:21 ?        00:00:00 rsyslogd -c5
root      2333     1  0 09:21 ?        00:00:00 udevd --daemon
103       2356     1  0 09:21 ?        00:00:02 dbus-daemon --system --fork --activation=upstart
root      2370     1  0 09:21 ?        00:00:00 /usr/sbin/modem-manager
avahi     2396     1  0 09:21 ?        00:00:00 avahi-daemon: running [ubuntu.local]
avahi     2403  2396  0 09:21 ?        00:00:00 avahi-daemon: chroot helper
root      2471     1  0 09:21 ?        00:00:00 NetworkManager
root      2489  2333  0 09:21 ?        00:00:00 udevd --daemon
root      2496  2333  0 09:21 ?        00:00:00 udevd --daemon
root      2526     1  0 09:21 ?        00:00:00 /usr/lib/policykit-1/polkitd
root      2576     2  0 09:21 ?        00:00:00 [kpsmoused]
root      2630     1  0 09:21 ?        00:00:00 upstart-socket-bridge --daemon
root      2698     1  0 09:21 tty4     00:00:00 /bin/login -f       
root      2702     1  0 09:21 tty5     00:00:00 /bin/login -f       
root      2724     1  0 09:21 tty2     00:00:00 /bin/login -f       
root      2726     1  0 09:21 tty3     00:00:00 /bin/login -f       
root      2729     1  0 09:21 tty6     00:00:00 /bin/login -f       
root      2784     1  0 09:21 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      2802     1  0 09:21 ?        00:00:00 lightdm
root      2812     1  0 09:21 ?        00:00:00 cron
root      2813     1  0 09:21 ?        00:00:01 /usr/sbin/irqbalance
daemon    2844     1  0 09:21 ?        00:00:00 atd
root      2872     2  0 09:21 ?        00:00:00 [hd-audio0]
root      2962  2802  6 09:21 tty7     00:04:48 /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
root      3148     1  0 09:21 ?        00:00:00 /usr/sbin/console-kit-daemon --no-daemon
root      3149     1  0 09:21 ?        00:00:00 /usr/sbin/bluetoothd
root      3221     2  0 09:21 ?        00:00:00 [l2cap]
root      3231     2  0 09:21 ?        00:00:00 [krfcommd]
ubuntu    3300  2726  0 09:21 tty3     00:00:00 -bash
ubuntu    3301  2702  0 09:21 tty5     00:00:00 -bash
ubuntu    3303  2724  0 09:21 tty2     00:00:00 -bash
ubuntu    3304  2729  0 09:21 tty6     00:00:00 -bash
ubuntu    3305  2698  0 09:21 tty4     00:00:00 -bash
root      3318  2471  0 09:21 ?        00:00:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-e
root      3376     1  0 09:21 ?        00:00:00 /usr/sbin/cupsd -F
root      3462     1  0 09:21 tty1     00:00:00 /bin/login -f       
ubuntu    3720  3462  0 09:21 tty1     00:00:00 -bash
root      3770     1  0 09:21 ?        00:00:00 /usr/lib/accountsservice/accounts-daemon
ubuntu    3859  2802  0 09:21 ?        00:00:00 gnome-session --session=ubuntu
ubuntu    4141  3859  0 09:21 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
ubuntu    4144     1  0 09:21 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
ubuntu    4145     1  0 09:21 ?        00:00:26 //bin/dbus-daemon --fork --print-pid 8 --print-address 10 --session
ubuntu    4188     1  0 09:21 ?        00:00:00 /usr/lib/gvfs/gvfsd
ubuntu    4198     1  0 09:21 ?        00:00:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/ubuntu/.gvfs
ubuntu    4211  3859  0 09:21 ?        00:00:06 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
ubuntu    4212     1  0 09:21 ?        00:00:00 /usr/bin/gnome-keyring-daemon --start --components=pkcs11
root      4221     1  0 09:21 ?        00:00:00 /usr/lib/upower/upowerd
ubuntu    4298     1  0 09:21 ?        00:00:02 /usr/lib/libgconf2-4/gconfd-2
ubuntu    4300     1  0 09:21 ?        00:00:00 /usr/lib/gnome-settings-daemon/gsd-printer
ubuntu    4304  3859  5 09:21 ?        00:04:03 compiz
ubuntu    4306     1  0 09:21 ?        00:00:00 /usr/bin/gnome-screensaver --no-daemon
colord    4308     1  0 09:21 ?        00:00:00 /usr/lib/i386-linux-gnu/colord/colord
ubuntu    4314     1  0 09:21 ?        00:00:02 syndaemon -i 0.5 -K -R
ubuntu    4317  3859  0 09:21 ?        00:00:17 nautilus -n
ubuntu    4318  3859  0 09:21 ?        00:00:00 nm-applet
ubuntu    4319  3859  0 09:21 ?        00:00:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
ubuntu    4322  3859  0 09:21 ?        00:00:00 bluetooth-applet
ubuntu    4324     1  0 09:21 ?        00:00:00 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     4326     1  0 09:21 ?        00:00:00 /usr/lib/rtkit/rtkit-daemon
ubuntu    4329  3859  0 09:21 ?        00:00:00 /usr/lib/gnome-settings-daemon/gnome-fallback-mount-helper
ubuntu    4335     1  0 09:21 ?        00:00:01 /usr/lib/gvfs/gvfs-gdu-volume-monitor
ubuntu    4340     1  0 09:21 ?        00:00:00 /usr/lib/notify-osd/notify-osd
root      4343     1  0 09:21 ?        00:00:00 /usr/lib/udisks/udisks-daemon
root      4345  4343  0 09:21 ?        00:00:00 udisks-daemon: polling /dev/sr0 /dev/sdb
ubuntu    4355     1  0 09:21 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
ubuntu    4359  4324  0 09:21 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
ubuntu    4361     1  0 09:21 ?        00:00:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
ubuntu    4365     1  0 09:21 ?        00:00:00 /usr/lib/d-conf/dconf-service
ubuntu    4370     1  0 09:21 ?        00:00:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.1 /org/gtk/gvfs/exec_spaw/0
ubuntu    4378     1  0 09:21 ?        00:00:00 /usr/lib/gvfs/gvfsd-metadata
ubuntu    4381     1  0 09:21 ?        00:00:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.1 /org/gtk/gvfs/exec_spaw/1
ubuntu    4389  4304  0 09:21 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decorator
ubuntu    4390  4389  0 09:21 ?        00:00:04 /usr/bin/unity-window-decorator
ubuntu    4396     1  0 09:21 ?        00:00:03 /usr/lib/bamf/bamfdaemon
ubuntu    4399     1  0 09:21 ?        00:00:08 /usr/lib/unity/unity-panel-service
ubuntu    4406     1  0 09:21 ?        00:00:00 /usr/lib/indicator-datetime/indicator-datetime-service
ubuntu    4407     1  0 09:21 ?        00:00:00 /usr/lib/indicator-application/indicator-application-service
ubuntu    4411     1  0 09:21 ?        00:00:00 /usr/lib/indicator-messages/indicator-messages-service
ubuntu    4415     1  0 09:21 ?        00:00:00 /usr/lib/indicator-session/indicator-session-service
ubuntu    4418     1  0 09:21 ?        00:00:00 /usr/lib/indicator-sound/indicator-sound-service
ubuntu    4439     1  0 09:21 ?        00:00:00 /usr/lib/geoclue/geoclue-master
ubuntu    4446  3859  0 09:21 ?        00:00:00 telepathy-indicator
ubuntu    4450     1  0 09:21 ?        00:00:00 /usr/lib/telepathy/mission-control-5
ubuntu    4457  3859  0 09:21 ?        00:00:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
ubuntu    4463     1  0 09:21 ?        00:00:01 /usr/lib/unity-lens-applications/unity-applications-daemon
ubuntu    4466     1  0 09:21 ?        00:00:00 /usr/lib/unity-lens-files/unity-files-daemon
ubuntu    4467     1  0 09:21 ?        00:00:00 /usr/lib/unity-lens-music/unity-music-daemon
ubuntu    4498     1  0 09:21 ?        00:00:00 /usr/lib/unity-lens-music/unity-musicstore-daemon
ubuntu    4541     1 14 09:22 ?        00:10:06 /usr/lib/firefox-7.0.1/firefox
ubuntu    4563  3859  0 09:22 ?        00:00:00 update-notifier
ubuntu    4594  3859  0 09:23 ?        00:00:00 /usr/lib/deja-dup/deja-dup/deja-dup-monitor
root      4620     1  0 09:24 ?        00:00:00 /sbin/mount.ntfs /dev/sda1 /media/FA90D83290D7F35D -o rw,nosuid,nodev,uhelper=udisks,uid=999,g
root      4637     1  0 09:24 ?        00:00:01 /sbin/mount.ntfs /dev/sda5 /media/82EAA3D4EAA3C2B1 -o rw,nosuid,nodev,uhelper=udisks,uid=999,g
ubuntu    4689     1  0 09:30 ?        00:00:09 banshee /usr/lib/banshee/Banshee.exe
ubuntu    4800     1  0 09:36 ?        00:00:22 gnome-terminal
ubuntu    4806  4800  0 09:36 ?        00:00:00 gnome-pty-helper
ubuntu    4807  4800  0 09:36 pts/0    00:00:00 bash
root      4943     1  0 09:38 ?        00:00:00 dbus-launch --autolaunch=8bd83eaef851cc3013d033440000001a --binary-syntax --close-stderr
root      4944     1  0 09:38 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
root      4949     1  0 09:38 ?        00:00:00 /usr/lib/d-conf/dconf-service
root      5025     2  0 09:51 ?        00:00:03 [kworker/0:2]
root      5173     2  0 10:16 ?        00:00:03 [kworker/1:1]
root      5195     2  0 10:21 ?        00:00:00 [kworker/1:2]
root      5199     2  0 10:23 ?        00:00:01 [kworker/0:0]
root      5206     2  0 10:27 ?        00:00:00 [kworker/1:0]
root      5211     2  0 10:28 ?        00:00:00 [kworker/0:1]
ubuntu    5215  4807  0 10:31 pts/0    00:00:00 ps -ef


I am afraid of killing important processes so I am asking for help. Do you recognize which processes should be killed or is this approach to resolving the problem completely wrong??? :'( 

Thx in advance  :)

---

### Post by raja.genupula on 2011-10-30
Hi  man 

open your terminal and then do this

```
sudo fuser -k -KILL /var/lib/dpkg/lock
```

then try again

---

### Post by kurotmiedignat on 2011-10-30
I tried it but I still can't delete the files. (Invalid argument). Ubunutu Software Center doesn't seem to be working either.

---

### Post by kurotmiedignat on 2011-10-30
I have another question: Do I really need Ubuntu Software Center to install Flash Player, cause when i am supposed to download it I am asked to choose an application to open Adobe with. The only application that is suggested is Ubuntu Software Center. However, can I install it without using Ubuntun Software Center???? Thx in advance

---

### Post by raja.genupula on 2011-10-30
> **kurotmiedignat said:**
> I have another question: Do I really need Ubuntu Software Center to install Flash Player, cause when i am supposed to download it I am asked to choose an application to open Adobe with. The only application that is suggested is Ubuntu Software Center. However, can I install it without using Ubuntun Software Center???? Thx in advance

Hi man 

go with this 

[https://launchpad.net/~sevenmachines/+archive/flash](https://launchpad.net/~sevenmachines/+archive/flash)


all the best

---

### Post by moldaviax on 2011-10-30
its always worth making a recovery system on a usb key if you have one. Do you have a usb key handy so that you could make it a live usb with whichever ubuntu version you are running with? Perhaps you could at least access the software centre that way?

M.

---

### Post by kurotmiedignat on 2011-10-30
I tried what the site said but this is what I obtained:

ubuntu@ubuntu:~$ sudo add-apt-repository ppa:sevenmachines/flash
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 8, in <module>
    from softwareproperties.SoftwareProperties import SoftwareProperties
ImportError: No module named softwareproperties.SoftwareProperties
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 111, in apport_excepthook
    os.O_WRONLY|os.O_CREAT|os.O_EXCL, 0o600), 'w')
OSError: [Errno 22] Invalid argument: '/var/crash/_usr_bin_add-apt-repository.0.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 8, in <module>
    from softwareproperties.SoftwareProperties import SoftwareProperties
ImportError: No module named softwareproperties.SoftwareProperties
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:sevenmachines/flash
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 8, in <module>
    from softwareproperties.SoftwareProperties import SoftwareProperties
ImportError: No module named softwareproperties.SoftwareProperties
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 111, in apport_excepthook
    os.O_WRONLY|os.O_CREAT|os.O_EXCL, 0o600), 'w')
OSError: [Errno 22] Invalid argument: '/var/crash/_usr_bin_add-apt-repository.0.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 8, in <module>
    from softwareproperties.SoftwareProperties import SoftwareProperties
ImportError: No module named softwareproperties.SoftwareProperties

Do you think that permanently installing ubuntu would fix the problem??

And thx very much for your help so far!!!:p

---

### Post by kurotmiedignat on 2011-10-30
Well that is definetly not a bad idea
 :)

---

### Post by kurotmiedignat on 2011-10-30
What I am going to do is delete this ubuntu from my USB stick and then reinstall it. Maybe I will get lucky the next time

---

