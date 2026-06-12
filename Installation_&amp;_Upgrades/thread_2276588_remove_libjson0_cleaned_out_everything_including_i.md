---
title: "remove libjson0 cleaned out everything including internet acces. How to resintall?"
date: 2015-05-03
forum: Installation &amp; Upgrades
---

### Post by ffrr on 2015-05-03
"dpkg -C" reported libjson0 was inconsistent.
"apt-get install libjson0" says "already newest version".
"apt-get update"
"dpkg -C" libjson0 is still inconsistent.
"apt-get upgrade"
"dpkg -C' libjson0 is still inconsistent, What is one to do? Remove and install. What else?
"apt-get remove libjson0" Goes on for about five minutes cleanign out an awful lot of stuff, so much, everything but the active terminal disappears from the screen one by one. Finally everythong stops. No more keyboard.
"Shift-Ctr-F3" opens an X terminal. 
"root" password
"apt-get install libjson0" produces the error messages below the line.

Craving rescue with the production machine knocked out.

Frederic


-----------------------------------------------------------------------------------------------------

stdout:

```
Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-flickr account-plugin-windows-live alacarte attr
  cracklib-runtime crda cups-browsed cups-pk-helper cups-server-common
  diffstat gdisk gir1.2-gconf-2.0 gir1.2-panelapplet-4.0 gir1.2-secret-1
  gir1.2-udisks-2.0 git git-man gkbd-capplet gnome-contacts
  gnome-control-center-shared-data gnome-exe-thumbnailer gnome-panel
  gnome-panel-data gnome-settings-daemon-schemas gsettings-ubuntu-schemas
  gstreamer1.0-nice guile-2.0-libs hardening-includes icoutils iw libaio1
  libapparmor-perl libapparmor1 libapt-pkg-perl libarchive-zip-perl
  libautodie-perl libbonobo2-0 libbonobo2-common libcapi20-3 libcolorhug1
  libcrack2 libemail-valid-perl liberror-perl libestr0 libexiv2-12
  libfarstream-0.2-2 libfftw3-single3 libfriends0 libgc1c2 libgexiv2-2
  libglamor0 libglew1.10 libglewmx1.10 libgnomekbd8 libgusb2 libhdb9-heimdal
  libio-pty-perl libipc-run-perl libipc-system-simple-perl libkdc2-heimdal
  libkeybinder0 liblist-moreutils-perl libnatpmp1 libnet-dns-perl
  libnet-domain-tld-perl libnet-ip-perl libnux-4.0-0 libnux-4.0-common
  libosmesa6 libp11-kit-gnome-keyring libperlio-gzip-perl libpwquality-common
  libpwquality1 libraw9 libreadline5 libsub-identify-perl libsystemd-daemon0
  libsystemd-journal0 libtelepathy-farstream3 libtext-levenshtein-perl
  libudisks2-0 libupstart1 liburl-dispatcher1 libxatracker2 lintian
  mysql-server-core-5.5 oneconf-common p11-kit p11-kit-modules
  plainbox-secure-policy python-commandnotfound python-dnspython
  python-keybinder python-oneconf python-prctl python3-aptdaemon.gtk3widgets
  python3-chardet python3-debian python3-feedparser python3-httplib2
  python3-lxml python3-mako python3-markupsafe python3-oneconf
  python3-piston-mini-client python3-pyparsing python3-requests python3-six
  python3-urllib3 python3-xkit qtdeclarative5-localstorage-plugin
  samba-dsdb-modules samba-vfs-modules shotwell-common
  signon-keyring-extension signon-plugin-password systemd-shim t1utils
  tdb-tools ubuntuone-client-data unity-lens-friends unity-lens-photos
  unity-scope-audacious unity-scope-calculator unity-scope-chromiumbookmarks
  unity-scope-clementine unity-scope-colourlovers unity-scope-devhelp
  unity-scope-firefoxbookmarks unity-scope-gmusicbrowser unity-scope-gourmet
  unity-scope-guayadeque unity-scope-home unity-scope-manpages
  unity-scope-musique unity-scope-openclipart unity-scope-texdoc
  unity-scope-tomboy unity-scope-virtualbox unity-scope-yelp
  unity-scope-zotero unity-scopes-master-default wine-gecko2.21 wine-mono0.0.8
  winetricks wireless-regdb
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cryptsetup-bin dmsetup ifupdown initramfs-tools initscripts libcryptsetup4
  libdevmapper1.02.1 libjson0 libudev1 mountall plymouth
  plymouth-theme-ubuntu-text procps udev upstart
Suggested packages:
  ppp rdnssd graphviz upstart-monitor
The following NEW packages will be installed:
  cryptsetup-bin dmsetup ifupdown initramfs-tools initscripts libcryptsetup4
  libdevmapper1.02.1 libjson0 mountall plymouth plymouth-theme-ubuntu-text
  procps udev upstart
The following packages will be upgraded:
  libudev1
1 upgraded, 14 newly installed, 0 to remove and 370 not upgraded.
Need to get 1,877 kB/1,912 kB of archives.
After this operation, 10.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] Err [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/) trusty-updates/main plymouth i386 0.8.8-0ubuntu17.1
  Could not resolve 'mirror.switch.ch'
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates/main plymouth i386 0.8.8-0ubuntu17.1
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty/main mountall i386 2.53
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates/main ifupdown i386 0.7.47.2ubuntu4.1
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates/main upstart i386 1.12.1-0ubuntu4.2
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates/main initscripts i386 2.88dsf-41ubuntu6.1
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates/main procps i386 1:3.3.9-1ubuntu2.2
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates/main udev i386 204-5ubuntu20.11
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates/main initramfs-tools all 0.103ubuntu4.2
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty/main dmsetup i386 2:1.02.77-6ubuntu2
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/) trusty/main libdevmapper1.02.1 i386 2:1.02.77-6ubuntu2
  Could not resolve 'mirror.switch.ch'
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty/main libdevmapper1.02.1 i386 2:1.02.77-6ubuntu2
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates/main plymouth-theme-ubuntu-text i386 0.8.8-0ubuntu17.1
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty/main libcryptsetup4 i386 2:1.6.1-1ubuntu1
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty/main cryptsetup-bin i386 2:1.6.1-1ubuntu1
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates/main libjson0 i386 0.11-3ubuntu1.2
  Could not resolve 'ch.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libjson0 i386 0.11-3ubuntu1.2
  Could not resolve 'security.ubuntu.com'
(END)


stderr:

E: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth_0.8.8-0ubuntu17.1_i386.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth_0.8.8-0ubuntu17.1_i386.deb)  Could not resolve 'ch.archive.ubuntu.com'

E: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.53_i386.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.53_i386.deb)  Could not resolve 'ch.archive.ubuntu.com'

E: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/pool/main/i/ifupdown/ifupdown_0.7.47.2ubuntu4.1_i386.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/i/ifupdown/ifupdown_0.7.47.2ubuntu4.1_i386.deb)  Could not resolve 'ch.archive.ubuntu.com'

E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/j/json-c/libjson0_0.11-3ubuntu1.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/j/json-c/libjson0_0.11-3ubuntu1.2_i386.deb)  Could not resolve 'security.ubuntu.com'

E: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart_1.12.1-0ubuntu4.2_i386.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart_1.12.1-0ubuntu4.2_i386.deb)  Could not resolve 'ch.archive.ubuntu.com'

E: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.88dsf-41ubuntu6.1_i386.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.88dsf-41ubuntu6.1_i386.deb)  Could not resolve 'ch.archive.ubuntu.com'

E: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.3.9-1ubuntu2.2_i386.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.3.9-1ubuntu2.2_i386.deb)  Could not resolve 'ch.archive.ubuntu.com'

E: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/pool/main/s/systemd/udev_204-5ubuntu20.11_i386.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/s/systemd/udev_204-5ubuntu20.11_i386.deb)  Could not resolve 'ch.archive.ubuntu.com'

E: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.103ubuntu4.2_all.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.103ubuntu4.2_all.deb)  Could not resolve 'ch.archive.ubuntu.com'

E: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/pool/main/l/lvm2/dmsetup_1.02.77-6ubuntu2_i386.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/l/lvm2/dmsetup_1.02.77-6ubuntu2_i386.deb)  Could not resolve 'ch.archive.ubuntu.com'

E: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/pool/main/l/lvm2/libdevmapper1.02.1_1.02.77-6ubuntu2_i386.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/l/lvm2/libdevmapper1.02.1_1.02.77-6ubuntu2_i386.deb)  Could not resolve 'ch.archive.ubuntu.com'

E: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth-theme-ubuntu-text_0.8.8-0ubuntu17.1_i386.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth-theme-ubuntu-text_0.8.8-0ubuntu17.1_i386.deb)  Could not resolve 'ch.archive.ubuntu.com'

E: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/pool/main/c/cryptsetup/libcryptsetup4_1.6.1-1ubuntu1_i386.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/c/cryptsetup/libcryptsetup4_1.6.1-1ubuntu1_i386.deb)  Could not resolve 'ch.archive.ubuntu.com'

E: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/pool/main/c/cryptsetup/cryptsetup-bin_1.6.1-1ubuntu1_i386.deb](http://ch.archive.ubuntu.com/ubuntu/pool/main/c/cryptsetup/cryptsetup-bin_1.6.1-1ubuntu1_i386.deb)  Could not resolve 'ch.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by matt_symes on 2015-05-04
Hi

That's a pretty important package you removed.

```
matthew-laptop:/var/log:2 % acsh libjson0 | head -n2
Package: libjson0
Priority: required
matthew-laptop:/var/log:2 %
```

It looks like many packages were dependent on it and it was low in the dependency chain.

You've lost most of your desktop and goodness knows what other packages along the way.

Honestly, i think a reinstall is the quickest solution here. Backup your data from the drive using a LiveCD/USB.

To attempt to fix your original problem, i would have downloaded the deb file if it was not in apt package cache and then tried something like the below to just try to reinstall that single package.

```
sudo dpkg -i --force-remove-reinstreq /var/cache/apt/archives/*libjson0*.deb
```

The above command assumes a glob and you could use tab completion to get the correct deb file. 

No guarantees the above command would work but it would only address the singular package that was giving you the problem.

EDIT:

> Craving rescue with the production machine knocked out.

Somehow i missed reading this line when i added code tags to you post.

Restore from backup is your quickest solution.

Kind regards

---

### Post by ffrr on 2015-05-04
Hi Mathew,
   This is going to be an experience to remember. Thanks for your recommendations. With the help of Dell I just got the machine to boot into a recovery menu, a huge improvement from a black screen and endless squeak. The menu says: 
 
Ubuntu
Advanced options for Ubuntu
(a memory test)
(some other memory test)

The selection Ubuntu displays "Kernel panic - not syncing: Attempted fo kill init!
(A few more lines)
(Auto-shutdown)

The selection Advanced options for Ubuntu brings up another menu:

Ubuntu, with Linux 3.0.0-23-generic-pae
Ubuntu, with Linux 3.0.0-23-generic-pae (recovery mode) 
Ubuntu, with Linux 3.0.0-23-generic
Ubuntu, with Linux 3.0.0-23-generic (recovery mode)
Ubuntu, with Linux 2.6.38-15-generic-pae
Ubuntu, with Linux 2.6.38-15-generic-pae (recovery mode)

All selections report a kernel panic and shut down. I would now run my recovery disk, if I could find it. I do have a recovery disk for another very similar machine. It is 12 point something LTS when the broken machine was 14 point something LTS, upgraded from initially 9 point something. I would run that other recovery disk, it if I didn't fear for my data, if things got worse. Perhaps you know whether there is a way to fix "inside out", starting with the kernel and preserving as much as remains of the tooling. If I could at least start a terminal, I could go from there. Is there a way to preserve at least the data if I do a complete OS reinstall? It may not necessarily involve formatting the disk.

Regards

Frederic

---

### Post by matt_symes on 2015-05-04
Hi

You may be abe to boot to a root shell by changing init in the grub command line.

From there you may have luck fixing it.

boot into the grub menu and select a kernel. Press the 'e' key to edit the **kernel** command line and add

```
init=/bin/bash
```

and then press ctrl +c or f10 (i forget which) to continue booting. 

If that boots it'll get you to an absolute minimum root shell with nothing running, as it'll bypass upstart (or systemd) where you'll be able to poke around your system and see what state it's in. However if may not work due to your grub error.

To find the Ubuntu version

```
cat /etc/lsb-release && uname -a
```

From there you'll know which iso to download to create a liveCD/USB.

EDIT: 

I forgot i ask some basic questions.

You're not using software RAID, LVM, encryption or a non default file system are you ?

Kind regards

---

### Post by ffrr on 2015-05-05
Mathew,

I wrote an answer yesterday, first of all to thank you for your suggestions. Apparently my message didn't go out. So I try again.

It turned out that "apt-get" did such a good cleaning job, that I couldn't even start the machine the next day. It beeped fearfully loud and sustained. With the help of Dell Support I managed to restore some sanity to the point of being presented a menu, some items of which offered a "recovery mode". All options go through a few actions, too quickly to grasp. Only before they do an auto-shutdown the scrolling stops for five seconds and one particularly uncryptic line meets the eye: Kernel panic - not syncing: Attempted to kill init!

That "apt-get remove (anything)" would destroy the kernel is certainly a malfunction of a magnitude one doesn't expect. Anyway, I believe the thing to do now is to somehow make a bootable CD. That shouldn't be all too difficult for the well-versed. As I am only moderately well-versed, I would greatly appreciate guidance.

Frederic

---

### Post by ffrr on 2015-05-05
I'm sorry. I'm a little out of sync. (Messages crossing?). How do I get the GRUB menu? Is it some key combination after turning on?

Frederic

---

### Post by ffrr on 2015-05-05
Progress report

Downloaded ubuntu-14.04.2-desktop-amd64.iso.
Making bootable DVD fails. Drive doesn't work.
Diagnostics find no fault with drive.
Dell Support suspects a driver problem, but cannot provide Linux drivers.
Inoperative DVD drives are a fairly common topic on this forum. No conclusive threads found.
Googling "ubuntu download dvd drivers" yields no actionable info.

Isn't there a repository for drivers somewhere?

Frederic

---

### Post by mörgæs on 2015-05-06
Hunting for a CD driver here and there is a bad Windows habit. It's not necessary for Buntu despite what the Dell guy said.

Have you tried booting from USB?

---

### Post by ffrr on 2015-05-08
By my experience, Dell's support is excellent. I called again the next day and spoke to another assistant. He said, there is no driver. It must be the drive. You'll have a new one tomorrow. And so I did. UPS brought a free replacement to my door. The bootable disk was made and although the making ended with an error message to the effect that I didn't have permission to use the drive, the disk works. When I run it I have the choice between booting and installing. I would install only as a last desperate resort, because I am sure my working environment and user accounts, including all data, wouldn't survive the experience. So I booted to see if I could regain access and go from there. The boot makes a new environment from scratch. It seems to be an unadministered single-user environment. A file viewer shows the pre-crash environment which I try to access as a Volume under the heading Devices. So the DVD boot mounts the hard disk as a device. Using the file viewer I can see that everything is still there. I can even access data, but only those that have read permission for everyone.       

It I open a terminal and display 'mount', I see this:

buntu@ubuntu:~$ mount -l
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime) [Ubuntu 14.04.2 LTS amd64]
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/ubuntu/NEW_VOLUME type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096) [NEW_VOLUME]
/dev/sda5 on /media/ubuntu/04238fe3-34b9-40d1-a410-7cecde32b59f type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda2 on /media/ubuntu/OS type vfat (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2) [OS]

/dev/sr0 is the DVD
NEW_VOLUME is an external hard disk
OS was made by the DVD boot
The rest looks fairly cryptic. In particular, I can't make out anything that looks like a mounted internal hard disk. And if I did, I would expect to just walk in, although I know the passwords. So, the question a dedicated hacker might be able answer is how to sneak into the pre-crash environment from here. 

Thanks for any suggestions

Frederic

---

### Post by make-it-fast on 2015-06-16
hello , ffrr !

i have the same problem as you: i deleted [B] libjson0:amd64 
[/B]
after that everything disappeared , only option was to force reboot .

I even coudn't load desktop - only linux 3.0.5 recovery  mode, using BusyBox.

Now i'm using usb slax linux system at my laptop , i checked hdd with e2fsck , no bad blocks there .. 

First, when i deleted this package, i didn't even know its name! so i had to find log files on hdd so i found this topic at the end :)

So i figured out that it is possible to  restore system trough making a live&#1057;D with the same distributive that u  had at your machine (i have ubuntu 14.04)

Also, there are some utilities to restore deleted files , i want to try one of them first... 

Do u have any news on that topic ?

---

