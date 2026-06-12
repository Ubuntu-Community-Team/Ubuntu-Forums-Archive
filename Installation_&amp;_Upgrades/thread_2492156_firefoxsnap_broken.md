---
title: "firefox/snap broken"
date: 2023-11-01
forum: Installation &amp; Upgrades
---

### Post by mv-879 on 2023-11-01
hello.

i have broken my snap-whatever by deleting /usr/lib/snap (i think) which after some googling i assumed to be leftover packages after installation process that seemed safe to be deleted (there were multiple versions of each file and the folder was quite big).

most significant result of this unwise action is broken firefox that i can't get back to work. any advice, please?

```
# snap remove firefox
error: cannot perform the following tasks:
- Remove data for snap "firefox" (3290) (unlinkat /var/snap/firefox/common/host-hunspell/en_GB.dic: read-only file system)

# snap install firefox
snap "firefox" is already installed, see 'snap help refresh'

# snap refresh firefox
error: cannot refresh "firefox": refreshing disabled snap "firefox" not supported

# snap enable firefox
error: cannot perform the following tasks:
- Setup snap "firefox" (3290) security profiles (cannot find installed snap "firefox" at revision 3290: missing file /snap/firefox/3290/meta/snap.yaml)

#

```

---

### Post by #&amp;thj^% on 2023-11-01
NOTE: Deleting /usr is pretty much the equivalent of deleting the OS.
ie:
```
ls /usr
bin    include  lib32  libexec  local  share
games  lib      lib64  libx32   sbin   src
### And
*me*&#57520;*~*&#57520;*ls /usr/lib
apg                                   libxnee.so.0
apparmor                              libxnee.so.0.0.0
apt                                   lightdm
aspell                                linux
bfd-plugins                           linux-boot-probes
binfmt.d                              linux-sound-base
bluetooth                             locale
casper                                lp_solve
chroot-setup.sh                       lsb
cnf-update-db                         man-db
command-not-found                     memtest86+
compat-ld                             menu
compiz                                mime
conky                                 mintstick
console-setup                         modprobe.d
cpp                                   modules
crda                                  modules-load.d
cryptsetup                            msttcorefonts
cups                                  netplan
dbus-1.0                              networkd-dispatcher
debug                                 NetworkManager
dhcpcd                                nvidia
discover                              openssh
dkms                                  openvpn
dpkg                                  os-probes
dracut                                os-release
emacsen-common                        p7zip
environment.d                         pam.d
fetch-url                             partconf
file                                  partman
finalrd                               pcmciautils
firefox                               pkgconfig
firefox-addons                        pm-utils
firetools                             policykit-1
firewalld                             policykit-1-gnome
firmware                              polkit-1
gcc                                   post-base-installer.d
gimp                                  pppd
girepository-1.0                      printer-driver-escpr
gnome-settings-daemon-3.0             python3
gnupg                                 python3.10
gnupg2                                python3.11
gold-ld                               python3.12
groff                                 recovery-mode
grub                                  rsyslog
grub-installer                        ruby
grub-legacy                           sasl2
gvfs                                  shim
hdparm                                software-properties
i386-linux-gnu                        speech-dispatcher-modules
ifupdown                              ssl
indicators3                           sysctl.d
init                                  syslinux
initramfs-tools                       SYSLINUX
ISOLINUX                              systemd
ispell                                sysusers.d
jvm                                   tasksel
kernel                                tcltk
klibc                                 thunderbird
klibc-qrjdleQmVUSXMeCB-fuBoSLiQ0A.so  thunderbird-addons
ld-linux.so.2                         tmpfiles.d
libau.so                              ubiquity
libau.so.2                            ubuntu-advantage
libau.so.2.10                         ubuntu-release-upgrader
libdvd-pkg                            udev
libfreecell-solver.so.0               udisks2
libfreecell-solver.so.0.6.0           unity-settings-daemon-1.0
libhardsid-builder.so.0               update-notifier
libhardsid-builder.so.0.0.1           user-setup
libnetpbm.so.10                       usrmerge
libnetpbm.so.10.0                     valgrind
libreoffice                           w3m
libresid-builder.so.0                 WolfLandBuilder
libresid-builder.so.0.0.1             X11
libsidplay2.so.1                      x86_64-linux-gnu
libsidplay2.so.1.0.1                  xorg
libtcp-portmon.a                      xpra
libxmmsclient.so.6                    xserver-xorg-video-intel
libxmmsclient.so.6.0.0                zfs-linux

```

---

### Post by deadflowr on 2023-11-01
Not sure about  /usr/lib/snap but there is the snapd folder there.
Maybe try reinstalling snapd
```
sudo apt install --reinstall snapd
```
Can also try refreshing into a newer snap channel like beta or edge
```
snap refresh --channel=beta firefox
```

---

### Post by mv-879 on 2023-11-01
> **1fallen said:**
> NOTE: Deleting /usr is pretty much the equivalent of deleting the OS.

not whole /usr/, just that specific folder with "snaps"

---

### Post by mv-879 on 2023-11-01
> **deadflowr said:**
> 
Not sure about /usr/lib/snap but there is the snapd folder there.
Maybe try reinstalling snapd
Can also try refreshing into a newer snap channel like beta or edge



thank you. reinstall went through, but the refresh still refuse to refresh, because firefox is "disabled".






```

# sudo apt install --reinstall snapd
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 2 not upgraded.
Need to get 0 B/23,8 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 300111 files and directories currently installed.)
Preparing to unpack .../snapd_2.58+22.04.1_amd64.deb ...
Unpacking snapd (2.58+22.04.1) over (2.58+22.04.1) ...
Setting up snapd (2.58+22.04.1) ...
snapd.failure.service is a disabled or a static unit not running, not starting it.
snapd.snap-repair.service is a disabled or a static unit not running, not starting it.
Failed to restart snapd.mounts-pre.target: Operation refused, unit snapd.mounts-pre.target may be requested by dependency only (it is configured to refuse manual start/stop).
See system logs and 'systemctl status snapd.mounts-pre.target' for details.
Could not execute systemctl:  at /usr/bin/deb-systemd-invoke line 142.
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for dbus (1.12.20-2ubuntu4.1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.6+22.04.20220217-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...


# snap install firefox
snap "firefox" is already installed, see 'snap help refresh'


# snap refresh firefox
error: cannot refresh "firefox": refreshing disabled snap "firefox" not supported


# snap enable firefox
error: cannot perform the following tasks:
- Setup snap "firefox" (3290) security profiles (cannot find installed snap "firefox" at revision 3290: missing file /snap/firefox/3290/meta/snap.yaml)


# snap refresh --channel=beta firefox
error: cannot refresh "firefox": refreshing disabled snap "firefox" not supported

```


i found that there is download option for snap and for a moment it seemed it will fix the problem, but no.


```

# snap download firefox
Fetching snap "firefox"
2023/11/01 21:46:33.438774 store_download.go:142: no host system xdelta3 available to use deltas
Fetching assertions for "firefox"
Install the snap with:
   snap ack firefox_3290.assert
   snap install firefox_3290.snap


# snap ack firefox_3290.assert


# snap install firefox_3290.snap
error: cannot install snap file: cannot update disabled snap "firefox"


# snap enable firefox
error: cannot perform the following tasks:
- Setup snap "firefox" (3290) security profiles (cannot find installed snap "firefox" at revision 3290: missing file /snap/firefox/3290/meta/snap.yaml)


# apt-get install firefox
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
firefox is already the newest version (1:1snap1-0ubuntu2).
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


# snap enable firefox
error: cannot perform the following tasks:
- Setup snap "firefox" (3290) security profiles (cannot find installed snap "firefox" at revision 3290: missing file /snap/firefox/3290/meta/snap.yaml)

```

---

### Post by #&amp;thj^% on 2023-11-01
> **mv-879 said:**
> not whole /usr/, just that specific folder with "snaps"

I was aware and noticed the whole path, and as your aware "/usr" anything or Directory is not advised, unless you explicitly know what your doing there.
Enough said about that now ;) but will you show us this please:
```
systemctl status snapd.mounts-pre.target
```
FTR not a snap fan myself. :(
```
systemctl status snapd.mounts-pre.target
&#9675; snapd.mounts-pre.target
     Loaded: masked (Reason: Unit snapd.mounts-pre.target is masked.)
     Active: inactive (dead) since Wed 2023-11-01 17:53:15 MDT; 1min 13s ago

Nov 01 16:41:20 me-zfs systemd[1]: Reached target snapd.mounts-pre.target - Mou>
Nov 01 17:53:15 me-zfs systemd[1]: Stopped target snapd.mounts-pre.target - Mou>

```

---

### Post by mv-879 on 2023-11-01
> **1fallen said:**
> systemctl status snapd.mounts-pre.target

```
[FONT=monospace][COLOR=#000000]# systemctl status snapd.mounts-pre.target[/COLOR]
[COLOR=#54FF54]**&#9679;**[/COLOR][COLOR=#000000] snapd.mounts-pre.target - Mounting snaps[/COLOR]
     Loaded: loaded (/lib/systemd/system/snapd.mounts-pre.target; static)
     Active: [COLOR=#54FF54]**active**[/COLOR][COLOR=#000000] since Wed 2023-11-01 16:50:43 CET; 8h ago[/COLOR]

Notice: journal has been rotated since unit was started, output may be incomplete.
[/FONT]
```

---

### Post by #&amp;thj^% on 2023-11-01
This is not looking good my friend, might back-up now all important data you want to keep, and re-install.

There is a very *slight* chance you could try to copy " /usr/lib/snap" or just " /usr/lib/" off the live installer
Info here for that: [https://askubuntu.com/questions/1158169/access-files-in-home-directory-from-live-mode](https://askubuntu.com/questions/1158169/access-files-in-home-directory-from-live-mode)
Good Luck and keep us posted

---

### Post by mv-879 on 2023-11-01
> **1fallen said:**
> There is a very *slight* chance you could try to copy " /usr/lib/snap" or just " /usr/lib/" off the live installer


i will try that, thank you. if it comes to that, i guess reinstall is as good way to increase space in root as any. 

btw i realized i have the list of packages i deleted from that /usr/lib/snap folder, if it would be any help - [https://i.imgur.com/ZBSQW4M.jpg](https://i.imgur.com/ZBSQW4M.jpg)

(edit: it seems the folder was /usr/lib/snapd/snaps)

---

### Post by TheFu on 2023-11-01
The lesson here is to only use snap tools to manage snap packages.  By default, when a snap is loaded, 3 copies will be retained.  You can change that to be more or fewer, but 2 is the minimal number. Canonical decided we aren't responsible enough to decide that we only need 1 copy of a snap package, once we know it is working well.  Whatever.

If you are running out of space in /, there might easily be other culprits.  Open a new thread and post the output from these commands:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
sudo du -sh /* 2> /dev/null | sort -h |tail -n 10
```

The 2nd command might take some time.  It only shows the largest 10 areas.

When posting those things, use the forum  'code' tags, so the columns line up.
For example, on a system here:
```
$ sudo du -sh /* 2> /dev/null | sort -h |tail -n 10
333M    /tmp
335M    /opt
640M    /snap
6.0G    /home
6.7G    /usr
37G     /TV
128G    /Backups
135G    /var
384G    /raid2
1.7T    /raid1
```

Note that I sorted them from smallest to largest, so any directories not being shown are smaller than 333M.  The last 2 aren't on the OS storage, so those are completely unimportant.
/var/ is 135G (huge, but I know a Windows Virtual machine is there eating 130GB of that storage) ... and that is actually on a special mount /var/lib/libvirt/ because I knew the exact size needed.

```
6.0G    /home
6.7G    /usr
```

Those aren't abusively large. /home could be smaller.  For a desktop system, /usr is already fairly small compared to most users' setup that are using 20.04 and later versions.

335M  /opt isn't part of the OS ... ah ... that's where I put some driver packages BEFORE they get installed.  It is only 335MB, so all other directories have less space. That's the point of the **sort** command.  Let's me see what's important with little effort.

Almost always, /home and /var are the main places with bloat that can be better managed.  I do this by putting both on separate storage volumes, not shared with the OS.  BTW, my / (OS) volume is sized at 35G with 7.1G currently used.  That means 26G is still available.
```
Filesystem                               Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg01-root01                  ext4   35G  7.1G   26G  22% /
/dev/nvme0n1p3                           ext4  672M  283M  340M  46% /boot
/dev/mapper/vg01-home01                  ext4   20G  6.0G   13G  32% /home
/dev/mapper/vg01-tmp01                   ext4  3.9G  349M  3.4G  10% /tmp
/dev/mapper/vg01-var01                   ext4   20G  3.2G   16G  18% /var
/dev/nvme0n1p2                           vfat   50M  6.1M   44M  13% /boot/efi
/dev/mapper/vg01-libvirt--01             ext4  134G  131G  2.8G  98% /var/lib/libvirt

```
Those are all the volumes that the OS cares about.

See how nicely the code tags makes the terminal output columns?

---

### Post by mv-879 on 2023-11-02
[IMG]https://dwsaur.files.wordpress.com/2021/07/good-news-everyone.jpg[/IMG]

> **1fallen said:**
> There is a very *slight* chance you could try to copy " /usr/lib/snap" or just " /usr/lib/" off the live installer

i successfully copied the snaps from live usb:


```
# ls -lah /var/lib/snapd/snaps/ 
total 2,3G 
drwxr-xr-x  3 root root 4,0K lis  2 05:43 . 
drwxr-xr-x 24 root root 4,0K lis  2 05:48 .. 
-rw-------  1 root root 4,0K srp  8 00:58 bare_5.snap 
-rw-------  1 root root  64M srp  8 00:58 core20_1974.snap 
-rw-------  1 root root  64M lis  2 05:17 core20_2015.snap 
-rw-------  1 root root  74M srp  8 00:58 core22_858.snap 
-rw-------  1 root root  74M lis  2 05:17 core22_864.snap 
-rw-------  1 root root 238M srp  8 00:58 firefox_2987.snap 
-rw-------  1 root root 241M lis  2 05:16 firefox_3290.snap 
-rw-------  1 root root 350M srp  8 00:58 gnome-3-38-2004_143.snap 
-rw-------  1 root root 486M srp  8 00:58 gnome-42-2204_120.snap 
-rw-------  2 root root 497M lis  1 14:47 gnome-42-2204_141.snap 
-rw-------  1 root root  92M srp  8 00:58 gtk-common-themes_1535.snap 
-rw-------  1 root root  23M lis  2 05:22 mc-pasman_37.snap 
drwxr-xr-x  2 root root 4,0K kv&#283; 29 14:08 partial 
-rw-------  1 root root  54M srp  8 00:58 snapd_19457.snap 
-rw-------  1 root root  41M lis  2 05:18 snapd_20290.snap 
-rw-------  1 root root 452K srp  8 00:58 snapd-desktop-integration_83.snap 
-rw-------  1 root root  13M srp  8 00:58 snap-store_959.snap

```

and fixed the problem:

```
# snap refresh firefox
error: cannot refresh "firefox": refreshing disabled snap "firefox" not supported

# snap enable firefox
error: cannot perform the following tasks:
- Run hook connect-plug-host-hunspell of snap "firefox" (run hook "connect-plug-host-hunspell": cannot locate base snap core22: No such file or directory)

# snap download core22
Fetching snap "core22"
Fetching assertions for "core22"
Install the snap with:
   snap ack core22_864.assert
   snap install core22_864.snap

# snap ack core22_864.assert

# snap install core22_864.snap
core22 20230801 from Canonical&#10003; installed

# snap enable firefox
firefox enabled

# snap refresh firefox
firefox 119.0-2 from Mozilla&#10003; refreshed
```

i still lost the firefox profile, someone obviously thought it is great idea to move it from the location in home where it always was to some snap-folder - other than the one where i deleted the snaps - but it disappeared anyway. I have no civil words for this. luckily for me i had some 2 month old backup, so i only lost few recent bookmarks and some history.

**Thank you 1fallen for your help** and good luck to any future archeologist!

---

### Post by mv-879 on 2023-11-02
> **TheFu said:**
> 
If you are running out of space in /, there might easily be other culprits.  Open a new thread and post the output from these commands:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
sudo du -sh /* 2> /dev/null | sort -h |tail -n 10
```


thank you for your tips as well.

now look and see that i am clearly running out of space...

```
# df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type     Size  Used Avail Use% Mounted on
/dev/sdb4      ext4      43G   20G   22G  48% /
/dev/sda1      fuseblk  1,9T  1,9T  4,5G 100% /media/storage1
/dev/sdc2      fuseblk  3,7T  3,7T  683M 100% /media/storage2
/dev/sdd1      ext4     220G  158G   51G  76% /media/storage0
/dev/sdb3      ext4      67G   55G  8,6G  87% /home
/dev/sdb1      vfat     240M  6,1M  234M   3% /boot/efi
```

... and behold the respectable fifth position of the snap folder. now you have to understand i tried to clean it, right? :P

```
[FONT=monospace][COLOR=#000000]# sudo du -sh /* 2> /dev/null | sort -h |tail -n 10 [/COLOR]
11M     /run 
22M     /etc 
190M    /boot 
392M    /opt 
979M    /root 
3,7G    /snap 
4,6G    /var 
14G     /usr 
55G     /home 
5,5T    /media
[/FONT]
```

(when i was in the live system, i merged my root partition with 15 gb swap partition that i no longer need. it may now not be clear why i did so drastic cleaning with 20 gb of free space, but that is why, i was literally getting to zero free space before)

---

### Post by TheFu on 2023-11-02
I don't think /snap is where anything "real" is stored.  I think it is all under /var/snap/  in truth.  Inside /snap/README is explains.

```
DISK SPACE USAGE

The disk space consumed by the content under this directory is
minimal as the real snap content never leaves the .snap file.
[B]Snaps are *mounted* rather than unpacked.
[/B]
For further details please visit
https://forum.snapcraft.io/t/the-snap-directory/2817

```


I minimize my snap use.  FWIW, 
```
$ snap list
Name    Version        Rev    Tracking       Publisher   Notes
bare    1.0            5      latest/stable  canonical&#10003;  base
core20  20230801       2015   latest/stable  canonical&#10003;  base
lxd     4.0.9-a29c6f1  24061  4.0/stable/…   canonical&#10003;  -
snapd   2.60.4         20290  latest/stable  canonical&#10003;  snapd

```

I am a little confused with the LXD version installed.  On a nearly identical system, it has 
```
lxd     5.19-31ff7b6  26093  latest/stable  canonical&#10003;  -
```
Something smells bad.

---

