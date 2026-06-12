---
title: "Cant install anything, help please =)"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by noscript on 2011-08-28
Hello I am having a right problem at the moment,
I have setup everything just for lamp, struggled to get apache permissions
sorted but got there in the end, but by the looks of things I may have made things
a wee bit worse,

Whenever I try and install anything from Ubuntu software Center I get the following
message:
[B]
"Failed to download package files"
Check your internet connection.[/B]

Now I read somewhere that below will fix the problem

[B]" apt-get update
apt-get upgrade
apt-get clean
apt-get autoclean "[/B]

After trying anyone of those in terminal I get the following error:

**/var/lib/sudo/_"username"_ writable by non-owner (040777), should be mode 0700**

I would really appreciate some help please,
I just want to get to work in lamp =)

---

### Post by dino99 on 2011-08-28
> **noscript said:**
> 
[B]
"Failed to download package files"
Check your internet connection.[/B]

Seems to be due to a borked config.
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

After trying anyone of those in terminal I get the following error:

**/var/lib/sudo/_"username"_ writable by non-owner (040777), should be mode 0700**



040777 is clearly scarying, 700 or 644 or 770 should be used (sorry i'm not used with lamp :()
sudo chmod 700 thispathtochange

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by noscript on 2011-08-28
Hello
Its not so much to do with lamp,
apache and mysql are running sweet at the moment so those don't need any tweaking.

My issue is I cannot install anything, from ubuntu software center, or by sudo apt-get,

The reason I believe I have these errors are probably due to all the different attempts
to get the correct file permissions for /var/www <--- which I was originally having issues with

---

### Post by bruno9779 on 2011-08-28
it looks like you have changed the permission of the whole /var folder, and sudo does not like the change.

please execute the following commands and post the output:

```
cd /var/lib
ls -l
```

it should look like this (roughly)

```
ls -l
total 292
drwxr-xr-x  2 root          root          4096 2010-06-22 23:38 acpi-support
drwxr-xr-x  2 root          root          4096 2011-05-04 07:22 alsa
drwxr-xr-x  6 root          root          4096 2011-08-26 09:18 apt
drwxr-xr-x  2 root          root          4096 2011-07-28 00:48 aptitude
drwxr-xr-x  2 root          root          4096 2011-08-28 08:06 apt-xapian-index
drwxr-xr-x  2 avahi-autoipd avahi-autoipd 4096 2010-10-07 13:13 avahi-autoipd
drwxr-xr-x  2 root          root          4096 2011-08-09 10:16 belocs
drwxr-xr-x  2 root          root          4096 2011-08-12 23:33 binfmts
drwxr-xr-x  2 root          root          4096 2010-10-07 13:17 computer-janitor
drwxrwx---  3 couchdb       couchdb       4096 2011-08-09 01:30 couchdb
drwxr-xr-x  2 root          root          4096 2011-05-03 17:36 dbus
drwxr-xr-x  7 root          root          4096 2011-07-19 07:48 defoma
drwxr-xr-x  2 root          root          4096 2011-08-25 13:06 dhcp
drwxr-xr-x  2 root          root          4096 2011-06-25 11:15 dhcp3
drwxr-xr-x  4 root          root          4096 2011-05-04 08:07 dictionaries-common
drwxr-xr-x  2 root          root          4096 2011-08-20 19:38 dkms
drwxr-xr-x  5 root          root          4096 2010-10-07 13:05 doc-base
drwxr-xr-x  7 root          root          4096 2011-08-26 09:18 dpkg
drwxr-xr-x  2 root          root          4096 2011-06-17 11:00 emacsen-common
drwxr-xr-x  2 root          root          4096 2011-08-25 13:06 exim4
drwxr-xr-x  2 root          root          4096 2011-08-26 09:17 flashplugin-installer
drwxr-xr-x  5 root          root          4096 2010-10-07 13:00 gconf
drwxr-x--- 12 gdm           gdm           4096 2011-08-25 13:07 gdm
drwxr-xr-x  3 root          root          4096 2011-06-23 17:54 ghc-6.12.1
drwxr-xr-x  3 root          root          4096 2011-06-25 16:15 ghc-6.12.3
drwxr-xr-x  4 root          root          4096 2010-10-07 13:05 ghostscript
drwxr-xr-x  2 root          root          4096 2011-05-03 19:44 hp
drwxr-xr-x  2 root          root          4096 2011-07-28 00:38 initramfs-tools
drwxr-xr-x  2 root          root          4096 2010-09-24 17:17 initscripts
drwxr-xr-x  2 root          root          4096 2010-09-24 15:16 insserv
drwxr-xr-x  4 root          root          4096 2011-05-04 08:08 libreoffice
drwxrwsr-x  2 libuuid       libuuid       4096 2010-10-07 12:57 libuuid
drwxr-xr-x  3 root          root          4096 2011-05-09 12:11 libxml-sax-perl
drwxr-xr-x  3 root          root          4096 2011-05-05 01:14 lintian
drwxr-xr-x  3 root          root          4096 2010-10-07 12:57 locales
drwxr-xr-x  2 root          root          4096 2011-08-28 08:06 logrotate
drwxr-xr-x  2 root          root          4096 2010-10-07 06:15 misc
drwxr-xr-x  2 root          root          4096 2011-08-28 08:06 mlocate
drwxr-xr-x  3 root          root          4096 2011-05-03 22:43 mplayer
drwxr-xr-x  2 root          root          4096 2011-06-25 16:21 msttcorefonts
drwxr-xr-x  2 root          root          4096 2011-08-28 10:56 NetworkManager
drwxr-xr-x  2 root          root          4096 2010-08-06 21:36 ntpdate
drwx------  2 root          root          4096 2011-08-20 19:59 nvidia
drwxr-xr-x  2 root          root          4096 2011-08-03 15:51 os-prober
drwxr-xr-x  2 root          root          4096 2011-08-24 19:15 pam
drwxr-xr-x  2 root          root          4096 2011-05-03 17:36 plymouth
drwx------  3 root          root          4096 2010-10-07 13:01 polkit-1
drwxr-xr-x  2 root          root          4096 2010-10-06 01:35 pulseaudio
drwxr-xr-x  2 root          root          4096 2011-08-26 09:18 pycentral
drwxr-xr-x  2 root          root          4096 2011-08-12 23:33 python
lrwxrwxrwx  1 root          root            18 2011-06-25 16:24 python-support -> /usr/lib/pymodules
drwxr-xr-x  2 root          root          4096 2011-06-19 19:19 samba
drwxr-xr-x  2 root          root          4096 2010-10-07 12:59 sgml-base
drwxr-xr-x  2 root          root          4096 2010-08-25 14:38 snmp
drwx------  3 root          supabr1       4096 1985-01-01 00:00 sudo
drwxr-xr-x  2 root          root          4096 2010-09-20 21:27 synaptic
drwxr-xr-x  5 root          root          4096 2011-05-05 09:56 tex-common
drwxr-xr-x  5 root          root          4096 2011-06-25 17:54 texmf
drwxr-xr-x  2 root          root          4096 2011-05-03 17:01 ubiquity
drwxr-xr-x  3 root          root          4096 2011-07-31 21:02 ucf
drwxr-xr-x  2 root          root          4096 2011-08-28 10:02 udisks
drwxr-xr-x  2 root          root          4096 2011-05-04 10:57 update-manager
drwxr-xr-x  3 root          root          4096 2011-07-03 11:09 update-notifier
drwxr-xr-x  2 root          root          4096 2011-08-26 09:18 update-rc.d
drwxr-xr-x  2 root          root          4096 2010-10-06 07:08 upower
drwxr-xr-x  2 root          root          4096 2011-08-25 13:06 urandom
drwxr-xr-x  3 root          root          4096 2011-08-26 09:17 ureadahead
drwxr-xr-x  2 root          root          4096 2010-09-08 09:32 usb_modeswitch
drwxr-xr-x  2 root          root          4096 2011-06-25 16:11 usbutils
drwxr-xr-x  3 root          root          4096 2010-10-07 12:58 vim
drwxr-xr-x  2 root          root          4096 2011-06-25 16:32 xfonts
drwxr-xr-x  2 root          root          4096 2011-06-25 16:01 xine
drwxr-xr-x  2 root          root          4096 2011-06-25 19:10 xkb
drwxr-xr-x  2 root          root          4096 2011-06-25 16:32 xml-core

```

---

### Post by dino99 on 2011-08-28
maybe check users & groups settings

---

### Post by noscript on 2011-08-28
> **bruno9779 said:**
> it looks like you have changed the permission of the whole /var folder, and sudo does not like the change.

please execute the following commands and post the output:

```
cd /var/lib
ls -l
```it should look like this (roughly)

```
ls -l
total 292
drwxr-xr-x  2 root          root          4096 2010-06-22 23:38 acpi-support
drwxr-xr-x  2 root          root          4096 2011-05-04 07:22 alsa
drwxr-xr-x  6 root          root          4096 2011-08-26 09:18 apt
drwxr-xr-x  2 root          root          4096 2011-07-28 00:48 aptitude
drwxr-xr-x  2 root          root          4096 2011-08-28 08:06 apt-xapian-index
drwxr-xr-x  2 avahi-autoipd avahi-autoipd 4096 2010-10-07 13:13 avahi-autoipd
drwxr-xr-x  2 root          root          4096 2011-08-09 10:16 belocs
drwxr-xr-x  2 root          root          4096 2011-08-12 23:33 binfmts
drwxr-xr-x  2 root          root          4096 2010-10-07 13:17 computer-janitor
drwxrwx---  3 couchdb       couchdb       4096 2011-08-09 01:30 couchdb
drwxr-xr-x  2 root          root          4096 2011-05-03 17:36 dbus
drwxr-xr-x  7 root          root          4096 2011-07-19 07:48 defoma
drwxr-xr-x  2 root          root          4096 2011-08-25 13:06 dhcp
drwxr-xr-x  2 root          root          4096 2011-06-25 11:15 dhcp3
drwxr-xr-x  4 root          root          4096 2011-05-04 08:07 dictionaries-common
drwxr-xr-x  2 root          root          4096 2011-08-20 19:38 dkms
drwxr-xr-x  5 root          root          4096 2010-10-07 13:05 doc-base
drwxr-xr-x  7 root          root          4096 2011-08-26 09:18 dpkg
drwxr-xr-x  2 root          root          4096 2011-06-17 11:00 emacsen-common
drwxr-xr-x  2 root          root          4096 2011-08-25 13:06 exim4
drwxr-xr-x  2 root          root          4096 2011-08-26 09:17 flashplugin-installer
drwxr-xr-x  5 root          root          4096 2010-10-07 13:00 gconf
drwxr-x--- 12 gdm           gdm           4096 2011-08-25 13:07 gdm
drwxr-xr-x  3 root          root          4096 2011-06-23 17:54 ghc-6.12.1
drwxr-xr-x  3 root          root          4096 2011-06-25 16:15 ghc-6.12.3
drwxr-xr-x  4 root          root          4096 2010-10-07 13:05 ghostscript
drwxr-xr-x  2 root          root          4096 2011-05-03 19:44 hp
drwxr-xr-x  2 root          root          4096 2011-07-28 00:38 initramfs-tools
drwxr-xr-x  2 root          root          4096 2010-09-24 17:17 initscripts
drwxr-xr-x  2 root          root          4096 2010-09-24 15:16 insserv
drwxr-xr-x  4 root          root          4096 2011-05-04 08:08 libreoffice
drwxrwsr-x  2 libuuid       libuuid       4096 2010-10-07 12:57 libuuid
drwxr-xr-x  3 root          root          4096 2011-05-09 12:11 libxml-sax-perl
drwxr-xr-x  3 root          root          4096 2011-05-05 01:14 lintian
drwxr-xr-x  3 root          root          4096 2010-10-07 12:57 locales
drwxr-xr-x  2 root          root          4096 2011-08-28 08:06 logrotate
drwxr-xr-x  2 root          root          4096 2010-10-07 06:15 misc
drwxr-xr-x  2 root          root          4096 2011-08-28 08:06 mlocate
drwxr-xr-x  3 root          root          4096 2011-05-03 22:43 mplayer
drwxr-xr-x  2 root          root          4096 2011-06-25 16:21 msttcorefonts
drwxr-xr-x  2 root          root          4096 2011-08-28 10:56 NetworkManager
drwxr-xr-x  2 root          root          4096 2010-08-06 21:36 ntpdate
drwx------  2 root          root          4096 2011-08-20 19:59 nvidia
drwxr-xr-x  2 root          root          4096 2011-08-03 15:51 os-prober
drwxr-xr-x  2 root          root          4096 2011-08-24 19:15 pam
drwxr-xr-x  2 root          root          4096 2011-05-03 17:36 plymouth
drwx------  3 root          root          4096 2010-10-07 13:01 polkit-1
drwxr-xr-x  2 root          root          4096 2010-10-06 01:35 pulseaudio
drwxr-xr-x  2 root          root          4096 2011-08-26 09:18 pycentral
drwxr-xr-x  2 root          root          4096 2011-08-12 23:33 python
lrwxrwxrwx  1 root          root            18 2011-06-25 16:24 python-support -> /usr/lib/pymodules
drwxr-xr-x  2 root          root          4096 2011-06-19 19:19 samba
drwxr-xr-x  2 root          root          4096 2010-10-07 12:59 sgml-base
drwxr-xr-x  2 root          root          4096 2010-08-25 14:38 snmp
drwx------  3 root          supabr1       4096 1985-01-01 00:00 sudo
drwxr-xr-x  2 root          root          4096 2010-09-20 21:27 synaptic
drwxr-xr-x  5 root          root          4096 2011-05-05 09:56 tex-common
drwxr-xr-x  5 root          root          4096 2011-06-25 17:54 texmf
drwxr-xr-x  2 root          root          4096 2011-05-03 17:01 ubiquity
drwxr-xr-x  3 root          root          4096 2011-07-31 21:02 ucf
drwxr-xr-x  2 root          root          4096 2011-08-28 10:02 udisks
drwxr-xr-x  2 root          root          4096 2011-05-04 10:57 update-manager
drwxr-xr-x  3 root          root          4096 2011-07-03 11:09 update-notifier
drwxr-xr-x  2 root          root          4096 2011-08-26 09:18 update-rc.d
drwxr-xr-x  2 root          root          4096 2010-10-06 07:08 upower
drwxr-xr-x  2 root          root          4096 2011-08-25 13:06 urandom
drwxr-xr-x  3 root          root          4096 2011-08-26 09:17 ureadahead
drwxr-xr-x  2 root          root          4096 2010-09-08 09:32 usb_modeswitch
drwxr-xr-x  2 root          root          4096 2011-06-25 16:11 usbutils
drwxr-xr-x  3 root          root          4096 2010-10-07 12:58 vim
drwxr-xr-x  2 root          root          4096 2011-06-25 16:32 xfonts
drwxr-xr-x  2 root          root          4096 2011-06-25 16:01 xine
drwxr-xr-x  2 root          root          4096 2011-06-25 19:10 xkb
drwxr-xr-x  2 root          root          4096 2011-06-25 16:32 xml-core

```

Yup done that and got this result,
```

noscript@aurora:~$ cd /var/lib
noscript@aurora:/var/lib$ ls -l
total 252
drwxrwxrwx  2 root          root          4096 2010-11-22 14:25 acpi-support
drwxrwxrwx  2 root          root          4096 2011-08-27 23:33 alsa
drwxrwxrwx  6 root          root          4096 2011-08-28 03:11 apt
drwxrwxrwx  2 root          root          4096 2011-08-29 00:33 apt-xapian-index
drwxrwxrwx  2 root          root          4096 2011-04-26 10:55 aspell
drwxrwxrwx  2 avahi-autoipd avahi-autoipd 4096 2011-04-26 11:03 avahi-autoipd
drwxrwxrwx  2 root          root          4096 2011-08-27 22:35 belocs
drwxrwxrwx  2 root          root          4096 2011-08-27 23:51 binfmts
drwxrwxrwx  2 root          root          4096 2011-04-26 11:03 computer-janitor
drwxrwxrwx  2 root          root          4096 2011-08-27 22:52 dbus
drwxrwxrwx  6 root          root          4096 2011-04-26 11:05 defoma
drwxrwxrwx  2 root          root          4096 2011-08-27 22:53 dhcp
drwxrwxrwx  5 root          root          4096 2011-04-26 11:08 dictionaries-common
drwxr-xr-x  3 root          root          4096 2011-08-28 03:00 dkms
drwxrwxrwx  5 root          root          4096 2011-04-26 10:56 doc-base
drwxrwxrwx  7 root          root          4096 2011-08-28 03:11 dpkg
drwxrwxrwx  5 root          root          4096 2011-04-26 10:53 gconf
drwxrwxrwx 13 gdm           gdm           4096 2011-08-29 00:09 gdm
drwxrwxrwx  4 root          root          4096 2011-04-26 10:55 ghostscript
drwxrwxrwx  2 root          root          4096 2011-04-26 10:57 hp
drwxrwxrwx  2 root          root          4096 2011-08-27 22:41 initramfs-tools
drwxrwxrwx  2 root          root          4096 2011-03-29 09:10 initscripts
drwxrwxrwx  2 root          root          4096 2011-03-29 09:10 insserv
drwxrwxrwx  3 jetty         adm           4096 2011-08-27 23:50 jetty
drwxrwxrwx  4 root          root          4096 2011-04-26 10:58 libreoffice
drwxrwsrwx  2 libuuid       libuuid       4096 2011-04-26 10:51 libuuid
drwxrwxrwx  3 root          root          4096 2011-04-26 11:07 lintian
drwxrwxrwx  3 root          root          4096 2011-04-26 10:51 locales
drwxrwxrwx  2 root          root          4096 2011-08-29 00:33 logrotate
drwxrwxrwx  2 root          root          4096 2011-04-22 04:50 misc
drwxrwxrwx  2 root          root          4096 2011-08-29 00:34 mlocate
drwxrwxrwx  5 mysql         mysql         4096 2011-08-29 00:09 mysql
drwxrwxrwx  2 root          root          4096 2011-08-27 22:52 NetworkManager
drwxrwxrwx  2 root          root          4096 2011-03-11 10:16 ntpdate
drwxrwxrwx  2 root          root          4096 2011-08-27 22:41 os-prober
drwxrwxrwx  2 root          root          4096 2011-08-27 23:45 pam
drwxrwxrwt  2 root          root          4096 2011-08-29 00:26 php5
drwxrwxrwx  3 root          root          4096 2011-08-27 23:57 phpmyadmin
drwxrwxrwx  2 root          root          4096 2011-08-27 22:52 plymouth
drwxrwxrwx  3 root          root          4096 2011-04-26 10:53 polkit-1
drwxrwxrwx  2 root          root          4096 2011-04-11 19:40 pulseaudio
drwxrwxrwx  2 root          root          4096 2011-08-28 03:11 pycentral
lrwxrwxrwx  1 root          root            18 2011-08-27 22:29 python-support -> /usr/lib/pymodules
drwxrwxrwx  2 root          root          4096 2011-04-07 07:18 samba
drwxrwxrwx  2 root          root          4096 2011-08-27 23:51 security
drwxrwxrwx  2 root          root          4096 2011-04-26 10:52 sgml-base
drwxrwxrwx  2 root          root          4096 2011-02-03 07:15 snmp
drwx------  3 root          root          4096 1985-01-01 00:00 sudo
drwxrwxrwx  2 root          root          4096 2011-04-07 00:21 synaptic
drwxrwxrwx  2 root          root          4096 2011-08-27 22:38 ubiquity
drwxrwxrwx  3 root          root          4096 2011-08-27 23:57 ucf
drwxrwxrwx  2 root          root          4096 2011-08-29 00:10 udisks
drwxrwxrwx  2 root          root          4096 2011-08-28 11:04 update-manager
drwxrwxrwx  3 root          root          4096 2011-08-27 22:52 update-notifier
drwxrwxrwx  2 root          root          4096 2011-08-28 03:00 update-rc.d
drwxrwxrwx  2 root          root          4096 2011-04-15 07:16 upower
drwxrwxrwx  2 root          root          4096 2011-08-29 00:09 urandom
drwxrwxrwx  3 root          root          4096 2011-08-28 03:16 ureadahead
drwxrwxrwx  2 root          root          4096 2011-03-23 00:39 usb_modeswitch
drwxrwxrwx  2 root          root          4096 2011-04-26 10:54 usbutils
drwxrwxrwx  3 root          root          4096 2011-04-26 10:51 vim
drwxrwxrwx  2 root          root          4096 2011-04-26 11:05 xfonts
drwxrwxrwx  2 root          root          4096 2011-08-27 22:52 xkb
drwxrwxrwx  2 root          root          4096 2011-04-26 11:01 xml-core
noscript@aurora:/var/lib$ 

```

---

### Post by bruno9779 on 2011-08-28
It looks like an ownership issue, not a permissions one.

you can try setting the ownership for /var/lib/sudo with chown, but maybe the damage goes further. 

```
cd /var/lib
sudo chown -R root:$USERNAME sudo
```

---

### Post by noscript on 2011-08-28
Gave that a go with no success,

Just tried to install flash again through ubuntu software center,
this time it has completely locked up with the usual message:

**Failed to download package files**
**Check your Internet connection.**

This time it is completely unresponsive

---

