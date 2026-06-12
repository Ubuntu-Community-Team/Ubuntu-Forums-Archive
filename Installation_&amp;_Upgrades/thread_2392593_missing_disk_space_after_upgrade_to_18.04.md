---
title: "missing disk space after upgrade to 18.04?"
date: 2018-05-23
forum: Installation &amp; Upgrades
---

### Post by clepsdyrae on 2018-05-23
Howdy -- I have a dinky laptop (old HP Stream) with minimal disk space. I upgraded from Lubuntu 17.10 to 18.04 and lost a couple GB of disk space along the way. It's painful.

[edit: the answer was that the btrfs filesystem had a snapshot auto-created on the upgrade from 17.10 to 18.04. See my post for how I deleted the snapshots, but only do so with an understanding of btrfs snapshots]

I have tried:

# apt-get autoclean
# apt-get clean
# apt-get autoremove

I have localepurge installed.

I have used synaptic to check for residual config files.

There are no kernel source packages installed or extra kernels lying around.

I have baobab'ed around looking for sources of disk usage and find nothing obvious.

18.04 can't really need that much more disk space than 17.10, right? So where has this mystery disk space gone to? I heard that there is now a swap file instead of partition, so maybe that's contributing? However, last I checked I had disabled swap on the machine (due to minimal disk space.) I will have to check that.

The 17.10 install was a fresh install over an older 16.10 install, and it freed a bunch of disk space up on /, which was awesome. I'd rather not do a fresh install again as I have a fair amount of weird custom stuff going on and don't want to go through it all over again. If I can somehow reclaim the missing space, that'd be super.

Thanks for any ideas!

---

### Post by TheFu on 2018-05-23
You've described many things. Facts are required. I don't trust GUI tools when it comes to storage.  Been burned.
**du**
**df**
and 
**find** 
are how I look for wasted space.  There is also the file system tuning tool, but that shouldn't be used on the file system where the OS sits. The default tuning parameters are there to protect us from doing stupid things. Running out of storage on OS partitions is bad, really bad. OTOH, for non-OS partitions removing the reserved-for-root 5% space isn't a bad idea.  On a 4TB drive, that is hundreds of GB of storage "reserved" for little good reason.

Being able to backup files, settings and packages, then restoring those to a new system is a core skill to have.  **Aptik** might be all you need to accomplish that. Just depends on your specific uses.

---

### Post by clepsdyrae on 2018-05-23
Thanks -- here are some more details:

/ is a 7.5GB partition
/home is a 1GB partition
/data is a 20G parition

Before upgrading to 18.04, I had ~2GB free on /. It was insufficient to perform the upgrade, so I cleaned up a bunch of stuff and offloaded some things to /data via symlinks:

/var/cache/apt
/var/lib/apt/lists
/usr/share/locale

I then had something like 4.2GB free. I did the upgrade. Now I have ~1GB free (with those directories still offloaded), implying that the upgrade is using an additional ~3GB. (These are rough numbers, from memory.)

baobab shows about 4.5GB usage on /. "du -cxsh /" shows 4.2GB usage. But "df -h" shows 6.7GB usage.

I do have a separate swap partition (1GB) and no swap file in use, so that's not it... [I realize now that I probably shouldn't have installed that way, but it doesn't affect the present issue.]

/ is btrfs -- is the something that I don't understand about how btrfs deals with free space that could be causing this?

I wondered too if mounted partitions were covering up "hidden" usage, so I did "mount -o bind / /mnt" and "du -cxsh /mnt" and got the same 4.2GB. (got that trick from [here]("https://serverfault.com/questions/275206/disk-full-du-tells-different-how-to-further-investigate?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa").)

"btrfs filesystem usage /" reports ~1GB free. But interestingly "btrfs subvolume list /" shows a "@apt-snapshot-release-upgrade-bionic-2018-05-15_16:33:40", and other reading I've done implies that upgrading the OS takes a btrfs snapshot... is that what is happening?

I can't seem to google up a simple way to see how much disk usage snapshots are taking, but I will keep researching.

---

### Post by QIII on 2018-05-23
Hello!

Could you please post the full output of du and df?

Using the option --max-depth=2 may also be informative.

Thanks.

---

### Post by clepsdyrae on 2018-05-23
Sure!

```
du -cxsh / > du.txt 2>&1

4.2G  /
4.2G  total

df -h / > df.txt 2>&1

Filesystem     Size Used Avail Use% Mounted on
/dev/mmcblk0p1 7.5G 6.7G  658M  92% / 

```
I discovered and installed [apt-btrfs-snapshot]("https://www.howtoforge.com/rollback-to-a-working-state-with-btrfs-plus-apt-btrfs-snapshot-on-ubuntu-12.10"). I'm tempted to  run apt-btrfs-snapshot delete, but still being ignorant in the ways of  btrfs, I continue research...

---

### Post by QIII on 2018-05-23
See my edit about the max-depth option.

---

### Post by clepsdyrae on 2018-05-23
Output of du -chx --max-depth=2 / > du.txt (3.9GB now instead of 4.2GB because I just removed an unused kernel):

```
28K    /etc/NetworkManager
8.0K    /etc/PackageKit
4.0K    /etc/UPower
236K    /etc/X11
52K    /etc/acpi
756K    /etc/alternatives
8.0K    /etc/apm
12K    /etc/apparmor
1.8M    /etc/apparmor.d
32K    /etc/apport
108K    /etc/apt
8.0K    /etc/avahi
24K    /etc/bash_completion.d
0    /etc/binfmt.d
16K    /etc/bluetooth
4.0K    /etc/ca-certificates
4.0K    /etc/calendar
12K    /etc/chatscripts
164K    /etc/console-setup
16K    /etc/cron.d
56K    /etc/cron.daily
4.0K    /etc/cron.hourly
8.0K    /etc/cron.monthly
20K    /etc/cron.weekly
32K    /etc/cups
12K    /etc/cupshelpers
132K    /etc/dbus-1
112K    /etc/default
4.0K    /etc/depmod.d
28K    /etc/dhcp
4.0K    /etc/dictionaries-common
20K    /etc/dpkg
12K    /etc/emacs
4.0K    /etc/firefox
772K    /etc/fonts
24K    /etc/ghostscript
12K    /etc/gnome
16K    /etc/gnome-system-tools
8.0K    /etc/groff
80K    /etc/grub.d
0    /etc/gss
4.0K    /etc/gtk-2.0
8.0K    /etc/gtk-3.0
0    /etc/guest-session
4.0K    /etc/hp
4.0K    /etc/ifplugd
16K    /etc/init
164K    /etc/init.d
16K    /etc/initramfs-tools
44K    /etc/iproute2
24K    /etc/kernel
8.0K    /etc/ld.so.conf.d
4.0K    /etc/ldap
8.0K    /etc/libnl-3
0    /etc/libpaper.d
28K    /etc/lightdm
12K    /etc/logcheck
36K    /etc/logrotate.d
4.0K    /etc/lxdm
4.0K    /etc/menu-methods
28K    /etc/modprobe.d
8.0K    /etc/modules-load.d
4.0K    /etc/netplan
52K    /etc/network
8.0K    /etc/newt
20K    /etc/openal
0    /etc/opt
108K    /etc/pam.d
4.0K    /etc/pcmcia
8.0K    /etc/perl
4.0K    /etc/pm
12K    /etc/polkit-1
68K    /etc/ppp
24K    /etc/profile.d
20K    /etc/pulse
4.0K    /etc/purple
4.0K    /etc/python2.7
4.0K    /etc/python3
4.0K    /etc/python3.6
52K    /etc/rc0.d
52K    /etc/rc1.d
92K    /etc/rc2.d
92K    /etc/rc3.d
92K    /etc/rc4.d
92K    /etc/rc5.d
52K    /etc/rc6.d
52K    /etc/rcS.d
8.0K    /etc/resolvconf
12K    /etc/rsyslog.d
328K    /etc/sane.d
48K    /etc/security
4.0K    /etc/selinux
0    /etc/sensors.d
12K    /etc/skel
580K    /etc/ssh
1.3M    /etc/ssl
4.0K    /etc/sudoers.d
40K    /etc/sysctl.d
304K    /etc/systemd
4.0K    /etc/terminfo
0    /etc/tmpfiles.d
4.0K    /etc/udev
4.0K    /etc/udisks2
56K    /etc/ufw
8.0K    /etc/update-manager
44K    /etc/update-motd.d
0    /etc/update-notifier
0    /etc/usb_modeswitch.d
8.0K    /etc/vim
40K    /etc/wpa_supplicant
436K    /etc/xdg
4.0K    /etc/cryptsetup-initramfs
0    /etc/request-key.d
260K    /etc/ImageMagick-6
40K    /etc/sgml
1.3M    /etc/mono
56K    /etc/xml
8.0K    /etc/emacs25
8.0K    /etc/lighttpd
4.0K    /etc/apache2
12K    /etc/mysql
20K    /etc/wireshark
4.0K    /etc/insserv.conf.d
116K    /etc/postfix
8.0K    /etc/smartmontools
12K    /etc/sysstat
4.0K    /etc/thunderbird
4.0K    /etc/python
8.0K    /etc/gconf
4.0K    /etc/geoclue
0    /etc/glvnd
8.0K    /etc/timidity
24K    /etc/fwupd
20K    /etc/pki
4.0K    /etc/libblockdev
8.0K    /etc/wildmidi
16K    /etc/neofetch
12M    /etc
0    /media
109M    /var/cache
4.7M    /var/backups
0    /var/crash
94M    /var/lib
0    /var/local
65M    /var/log
0    /var/mail
0    /var/metrics
0    /var/opt
0    /var/snap
24K    /var/spool
0    /var/tmp
273M    /var
16M    /bin
7.2M    /boot/grub
138M    /boot
12K    /lib/apparmor
8.0K    /lib/console-setup
48K    /lib/crda
257M    /lib/firmware
12K    /lib/hdparm
12K    /lib/init
28K    /lib/lsb
20K    /lib/modprobe.d
463M    /lib/modules
44K    /lib/recovery-mode
8.8M    /lib/systemd
164K    /lib/terminfo
17M    /lib/udev
24K    /lib/ufw
21M    /lib/x86_64-linux-gnu
92K    /lib/cryptsetup
20K    /lib/security
68K    /lib/netplan
766M    /lib
4.0K    /lib64
0    /mnt
0    /opt
8.0K    /root/.cache
4.0K    /root/.ssh
0    /root/.nano
4.0K    /root/.ecryptfs
4.0K    /root/.dbus
4.0K    /root/.local
8.0K    /root/.config
0    /root/.emacs.d
8.0K    /root/.synaptic
4.0K    /root/.gconf
68K    /root
12M    /sbin
4.0K    /snap
0    /srv
187M    /usr/bin
4.0K    /usr/games
12M    /usr/include
1.4G    /usr/lib
4.0K    /usr/local
17M    /usr/sbin
990M    /usr/share
224M    /usr/src
2.8G    /usr
0    /cdrom
3.9G    /
3.9G    total

```

---

### Post by QIII on 2018-05-23
Oddly, it almost looks like /usr is living in /srv, unless the formatting is off. :) If that is actually a higher level, then that is probably about right.  I'm going to go with /usr being at the same level as /srv above it and the oddity being attributed to the differing length of the size string.

I'm assuming that the storage is eMMC?  With something that small, I wonder if a minimal installation built up with only the things you really need might be more conservative.

(edit:  OK.  Ya.  I just noticed /dev/mmcblk0p1)

---

### Post by clepsdyrae on 2018-05-23
> **QIII said:**
> It looks like something on the order of 5G is used up in /srv.

Thanks -- it's just the formatting, yes; /srv is 0 bytes in size. /usr is mounted at / as normal.

Am I off base on the btrfs idea? I tried:

# btrfs quota enable /

And then:

```
# btrfs subvolume list /
ID 257 gen 29072 top level 5 path @
ID 268 gen 11682 top level 5 path @apt-snapshot-release-upgrade-bionic-2018-05-15_16:33:40
ID 270 gen 29016 top level 5 path @apt-snapshot-2018-05-23_10:48:54
# btrfs qgroup show /
qgroupid         rfer         excl 
--------         ----         ---- 
0/5          16.00KiB     16.00KiB 
0/257         3.73GiB      6.44MiB 
0/268         3.21GiB      2.56GiB 
0/270         4.01GiB     56.57MiB 

```

...which seems to imply that the upgrade snapshot is taking 2.56GB?

---

### Post by QIII on 2018-05-23
I'm not at all well-versed in btrfs, so I can't advise there.

---

### Post by TheFu on 2018-05-23
btrfs lies about space used. To get the real numbers, you have to use btrfs tools.
[https://askubuntu.com/questions/464074/ubuntu-thinks-btrfs-disk-is-full-but-its-not](https://askubuntu.com/questions/464074/ubuntu-thinks-btrfs-disk-is-full-but-its-not)

This is 1 of the reasons I won't use  that file system.

---

### Post by clepsdyrae on 2018-05-23
I went ahead and deleted the snapshots using:

# mount /dev/mmcblk0p1 /mnt
# btrfs subvolume delete /mnt/@apt-yadda-yadda-yadda
# btrfs subvolume delete /mnt/@apt-yadda-yadda-yadda
# umount /mnt

and now df -h shows 3.4G free.

Thanks for the help,
-c

---

