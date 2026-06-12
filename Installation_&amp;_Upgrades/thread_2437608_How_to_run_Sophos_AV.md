---
title: "How to run Sophos AV"
date: 2020-02-26
forum: Installation &amp; Upgrades
---

### Post by hanswurst98 on 2020-02-26
Hi everybody

After some trial and error I managed to install Sophos AV.

At least the terminal said "installation complete" and so I closed it.

I doublechecked /opt and there are plenty of folders and files.

However, how can I run Sophos and an anti-virus scan now?

Thanks

---

### Post by EuclideanCoffee on 2020-02-26
Please provide the following information.

stdout (output) for the command:

tree /opt/

Thanks!

---

### Post by hanswurst98 on 2020-02-27
If I have installed tree correctly and ran the command right there seems to be an issue:


> /opt/
|___ sophos [error opening dir]

1 directory, 0 files

---

### Post by hanswurst98 on 2020-02-27
I managed to learn how to start Sophos. It's as simple as 

> savscan /

Sorry for bothering, however, I have two new questions.

First, after I have scanned the system, I get a lot of lines in the terminal saying 

> Can't open /xyz/...

and after the scan is completed I get some 300 errors.

Am I right to assume this is normal?

Second, is there an option to let's say scan an external drive or USB as opposed to the entire system?

---

### Post by yancek on 2020-02-27
You need to post the entire line you get with the 'can't open' and also at least a few of the errors or we are just guessing.  Have you gone to the Sophos site or do you have a README file that came with Sophos?

---

### Post by hanswurst98 on 2020-02-28
Thanks. The following lines are listed as "couldn't open" plus a few as "couldn't scan". According to the scan summary 293 errors (and 0 viruses).

> 
/run/wpa_supplicant (errno is 13)
/run/gdm3 (errno is 13)
/run/udisks2 (errno is 13)
/run/cups/certs (errno is 13)
/run/user/1000/gvfs
/run/sudo (errno is 13)
/run/systemd/unit-root (errno is 13)
/run/systemd/resolve/netif (errno is 13)
/run/systemd/dynamic-uid/direct:systemd-timesync
/run/systemd/dynamic-uid/direct:62583
/run/systemd/dynamic-uid/62583
/run/systemd/journal/streams/9:30046
/run/systemd/journal/streams/9:29925
/run/systemd/journal/streams/9:29923
/run/systemd/journal/streams/9:29896
/run/systemd/journal/streams/9:29895
/run/systemd/journal/streams/9:29877
/run/systemd/journal/streams/9:28536
/run/systemd/journal/streams/9:28514
/run/systemd/journal/streams/9:28513
/run/systemd/journal/streams/9:27982
/run/systemd/journal/streams/9:27942
/run/systemd/journal/streams/9:27924
/run/systemd/journal/streams/9:27923
/run/systemd/journal/streams/9:27900
/run/systemd/journal/streams/9:27899
/run/systemd/journal/streams/9:27798
/run/systemd/journal/streams/9:27797
/run/systemd/journal/streams/9:27790
/run/systemd/journal/streams/9:27788
/run/systemd/journal/streams/9:27760
/run/systemd/journal/streams/9:27758
/run/systemd/journal/streams/9:27733
/run/systemd/journal/streams/9:27732
/run/systemd/journal/streams/9:27726
/run/systemd/journal/streams/9:27723
/run/systemd/journal/streams/9:27702
/run/systemd/journal/streams/9:27701
/run/systemd/journal/streams/9:27695
/run/systemd/journal/streams/9:27694
/run/systemd/journal/streams/9:28689
/run/systemd/journal/streams/9:28688
/run/systemd/journal/streams/9:26575
/run/systemd/journal/streams/9:26573
/run/systemd/journal/streams/9:26550
/run/systemd/journal/streams/9:26548
/run/systemd/journal/streams/9:27627
/run/systemd/journal/streams/9:27624
/run/systemd/journal/streams/9:27600
/run/systemd/journal/streams/9:27596
/run/systemd/journal/streams/9:27575
/run/systemd/journal/streams/9:27574
/run/systemd/journal/streams/9:27570
/run/systemd/journal/streams/9:27569
/run/systemd/journal/streams/9:27565
/run/systemd/journal/streams/9:27564
/run/systemd/journal/streams/9:27562
/run/systemd/journal/streams/9:27560
/run/systemd/journal/streams/9:27538
/run/systemd/journal/streams/9:27536
/run/systemd/journal/streams/9:27513
/run/systemd/journal/streams/9:27381
/run/systemd/journal/streams/9:27339
/run/systemd/journal/streams/9:26443
/run/systemd/journal/streams/9:27181
/run/systemd/journal/streams/9:27180
/run/systemd/journal/streams/9:27178
/run/systemd/journal/streams/9:27140
/run/systemd/journal/streams/9:26392
/run/systemd/journal/streams/9:27061
/run/systemd/journal/streams/9:27050
/run/systemd/journal/streams/9:27034
/run/systemd/journal/streams/9:27022
/run/systemd/journal/streams/9:27021
/run/systemd/journal/streams/9:27006
/run/systemd/journal/streams/9:27005
/run/systemd/journal/streams/9:26016
/run/systemd/journal/streams/9:25977
/run/systemd/journal/streams/9:26667
/run/systemd/journal/streams/9:25519
/run/systemd/journal/streams/9:25518
/run/systemd/journal/streams/9:25701
/run/systemd/journal/streams/9:25673
/run/systemd/journal/streams/9:25376
/run/systemd/journal/streams/9:25267
/run/systemd/journal/streams/9:24454
/run/systemd/journal/streams/9:24453
/run/systemd/journal/streams/9:24933
/run/systemd/journal/streams/9:24789
/run/systemd/journal/streams/9:24729
/run/systemd/journal/streams/9:24728
/run/systemd/journal/streams/9:23726
/run/systemd/journal/streams/9:21465
/run/systemd/journal/streams/9:22645
/run/systemd/journal/streams/9:20726
/run/systemd/journal/streams/9:22317
/run/systemd/journal/streams/9:20720
/run/systemd/journal/streams/9:22170
/run/systemd/journal/streams/9:20717
/run/systemd/journal/streams/9:20715
/run/systemd/journal/streams/9:21721
/run/systemd/journal/streams/9:21720
/run/systemd/journal/streams/9:21516
/run/systemd/journal/streams/9:20417
/run/systemd/journal/streams/9:20344
/run/systemd/journal/streams/9:20536
/run/systemd/journal/streams/9:19439
/run/systemd/journal/streams/9:19351
/run/systemd/journal/streams/9:16512
/run/systemd/journal/streams/9:15438
/run/systemd/journal/streams/9:14939
/run/systemd/inaccessible (errno is 13)
/run/lock/whoopsie/lock
/var/spool/rsyslog (errno is 13)
/var/spool/cron/crontabs (errno is 13)
/var/spool/cups (errno is 13)
/var/lib/update-notifier/updates-available
/var/lib/update-notifier/package-data-downloads/partial (errno is 13)
/var/lib/snapd/void (errno is 13)
/var/lib/snapd/cookie (errno is 13)
/var/lib/snapd/device/private-keys-v1/0KGA2WKMWWFMjgT4eb5TH8Dr-Nb5baI3fd61htfYULwT1VqBQjFCEGQAALbVxDjn
/var/lib/whoopsie/whoopsie-id
/var/lib/polkit-1 (errno is 13)
/var/lib/fwupd/gnupg (errno is 13)
/var/lib/systemd/random-seed
/var/lib/dpkg/triggers/Lock
/var/lib/dpkg/lock
/var/lib/dpkg/lock-frontend
/var/lib/udisks2 (errno is 13)
/var/lib/NetworkManager/secret_key
/var/lib/ureadahead/pack
/var/lib/colord/.cache (errno is 13)
/var/lib/private (errno is 13)
/var/lib/geoclue/.cache (errno is 13)
/var/lib/apt/lists/partial (errno is 13)
/var/lib/apt/lists/lock
/var/lib/gdm3/.gnupg (errno is 13)
/var/lib/gdm3/.config/gnome-session (errno is 13)
/var/lib/gdm3/.local (errno is 13)
/var/cache/ldconfig (errno is 13)
/var/cache/apt/archives/partial (errno is 13)
/var/cache/apt/archives/lock
/var/cache/cups (errno is 13)
/var/log/speech-dispatcher (errno is 13)
/var/log/btmp
/var/log/tallylog
/var/log/installer/version
/var/log/installer/debug
/var/log/installer/partman
/var/log/installer/syslog
/var/log/gdm3 (errno is 13)
/var/tmp/systemd-private-f6c2765ecde640c1abed55dfdf14d467-ModemManager.service-aS8zNb (errno is 13)
/var/tmp/systemd-private-f6c2765ecde640c1abed55dfdf14d467-rtkit-daemon.service-E0cjx3 (errno is 13)
/var/tmp/systemd-private-f6c2765ecde640c1abed55dfdf14d467-colord.service-EYKQpp (errno is 13)
/var/tmp/systemd-private-f6c2765ecde640c1abed55dfdf14d467-systemd-timesyncd.service-FHPtOP (errno is 13)
/var/tmp/systemd-private-f6c2765ecde640c1abed55dfdf14d467-fwupd.service-1vbxRW (errno is 13)
/var/tmp/systemd-private-f6c2765ecde640c1abed55dfdf14d467-systemd-resolved.service-YgabmW (errno is 13)
/var/tmp/systemd-private-f6c2765ecde640c1abed55dfdf14d467-bolt.service-Y3cVGL (errno is 13)
/vmlinuz
/lib/modules/5.3.0-28-generic/build/net/strparser/Makefile
/lib/modules/5.3.0-28-generic/build/net/strparser/Kconfig
/lib/modules/5.3.0-28-generic/build/net/tls/Makefile
/lib/modules/5.3.0-28-generic/build/net/tls/Kconfig
/lib/modules/5.3.0-28-generic/build/net/sunrpc/xprtrdma/Makefile
/lib/modules/5.3.0-28-generic/build/net/sunrpc/Makefile
/lib/modules/5.3.0-28-generic/build/net/sunrpc/Kconfig
/opt/sophos-av/uncdownload (errno is 13)
/opt/sophos-av/include (errno is 13)
/opt/sophos-av/doc (errno is 13)
/opt/sophos-av/engine (errno is 13)
/opt/sophos-av/var (errno is 13)
/opt/sophos-av/lib64 (errno is 13)
/opt/sophos-av/lib (errno is 13)
/opt/sophos-av/.smb (errno is 13)
/opt/sophos-av/log (errno is 13)
/opt/sophos-av/update (errno is 13)
/opt/sophos-av/share (errno is 13)
/opt/sophos-av/tmp (errno is 13)
/opt/sophos-av/talpa (errno is 13)
/opt/sophos-av/uninstall.sh
/opt/sophos-av/bin (errno is 13)
/opt/sophos-av/etc/sophosav (errno is 13)
/opt/sophos-av/etc/free_version
/snap/core/8689/dev/core
/snap/core/8689/etc/gshadow
/snap/core/8689/etc/hostname
/snap/core/8689/etc/mtab
/snap/core/8689/etc/ppp/chap-secrets
/snap/core/8689/etc/ppp/pap-secrets
/snap/core/8689/etc/rc2.d/S03grub-common
/snap/core/8689/etc/rc3.d/S03grub-common
/snap/core/8689/etc/rc4.d/S03grub-common
/snap/core/8689/etc/rc5.d/S03grub-common
/snap/core/8689/etc/security/opasswd
/snap/core/8689/etc/shadow
/snap/core/8689/etc/ssl/private (errno is 13)
/snap/core/8689/etc/sudoers
/snap/core/8689/etc/sudoers.d/README
/snap/core/8689/root (errno is 13)
/snap/core/8689/usr/lib/ssl/private (errno is 13)
/snap/core/8689/usr/sbin/dpkg-divert
/snap/core/8689/usr/sbin/dpkg-statoverride
/snap/core/8689/usr/share/doc/openssl/copyright
/snap/core/8689/var/cache/ldconfig (errno is 13)
/snap/core/8689/var/lib/extrausers/gshadow
/snap/core/8689/var/lib/extrausers/shadow
/snap/core/8689/var/lib/machines (errno is 13)
/snap/core/8689/var/lib/snapd/void (errno is 13)
/snap/core/8689/var/lib/waagent (errno is 13)
/snap/core/8689/var/log/btmp
/snap/core/8689/var/spool/cron/crontabs (errno is 13)
/snap/core/8689/var/spool/rsyslog (errno is 13)
/snap/core/8268/dev/core
/snap/core/8268/etc/gshadow
/snap/core/8268/etc/hostname
/snap/core/8268/etc/mtab
/snap/core/8268/etc/ppp/chap-secrets
/snap/core/8268/etc/ppp/pap-secrets
/snap/core/8268/etc/rc2.d/S03grub-common
/snap/core/8268/etc/rc3.d/S03grub-common
/snap/core/8268/etc/rc4.d/S03grub-common
/snap/core/8268/etc/rc5.d/S03grub-common
/snap/core/8268/etc/security/opasswd
/snap/core/8268/etc/shadow
/snap/core/8268/etc/ssl/private (errno is 13)
/snap/core/8268/etc/sudoers
/snap/core/8268/etc/sudoers.d/README
/snap/core/8268/root (errno is 13)
/snap/core/8268/usr/sbin/dpkg-divert
/snap/core/8268/usr/sbin/dpkg-statoverride
/snap/core/8268/usr/share/doc/openssl/copyright
/snap/core/8268/var/cache/ldconfig (errno is 13)
/snap/core/8268/var/lib/extrausers/gshadow
/snap/core/8268/var/lib/extrausers/shadow
/snap/core/8268/var/lib/machines (errno is 13)
/snap/core/8268/var/lib/snapd/void (errno is 13)
/snap/core/8268/var/lib/waagent (errno is 13)
/snap/core/8268/var/log/btmp
/snap/core/8268/var/spool/cron/crontabs (errno is 13)
/snap/core/8268/var/spool/rsyslog (errno is 13)
/snap/core18/current/etc/gshadow
/snap/core18/current/etc/mtab
/snap/core18/current/etc/security/opasswd
/snap/core18/current/etc/shadow
/snap/core18/current/etc/ssl/private (errno is 13)
/snap/core18/current/etc/sudoers
/snap/core18/current/etc/sudoers.d/README
/snap/core18/current/root (errno is 13)
/snap/core18/current/usr/bin/snap
/snap/core18/current/usr/bin/snapctl
/snap/core18/current/var/cache/ldconfig (errno is 13)
/snap/core18/current/var/lib/extrausers/gshadow
/snap/core18/current/var/lib/extrausers/shadow
/snap/core18/current/var/lib/private (errno is 13)
/snap/core18/current/var/lib/snapd/void (errno is 13)
/usr/lib/cups/backend/cups-brf
/usr/local/bin/savscan
/usr/local/bin/sweep
/usr/local/etc/sav (errno is 13)
/root (errno is 13)
/tmp/systemd-private-f6c2765ecde640c1abed55dfdf14d467-systemd-resolved.service-rfaoDu (errno is 13)
/tmp/systemd-private-f6c2765ecde640c1abed55dfdf14d467-ModemManager.service-xxk1Nv (errno is 13)
/tmp/systemd-private-f6c2765ecde640c1abed55dfdf14d467-fwupd.service-vDEI29 (errno is 13)
/tmp/systemd-private-f6c2765ecde640c1abed55dfdf14d467-bolt.service-Chq6Bp (errno is 13)
/tmp/systemd-private-f6c2765ecde640c1abed55dfdf14d467-rtkit-daemon.service-1JKgrV (errno is 13)
/tmp/systemd-private-f6c2765ecde640c1abed55dfdf14d467-systemd-timesyncd.service-xEHj5n (errno is 13)
/tmp/systemd-private-f6c2765ecde640c1abed55dfdf14d467-colord.service-qvQ0AW (errno is 13)
/swapfile
/lost+found (errno is 13)
/etc/security/opasswd
/etc/polkit-1/localauthority (errno is 13)
/etc/gshadow-
/etc/ppp/chap-secrets
/etc/ppp/pap-secrets
/etc/sudoers.d/README
/etc/init.d/sav-protect
/etc/init.d/sav-update
/etc/init.d/sav-rms
/etc/sudoers
/etc/shadow-
/etc/rc4.d/S01sav-protect
/etc/rc4.d/K01sav-rms
/etc/gshadow
/etc/rc3.d/S01sav-protect
/etc/rc3.d/K01sav-rms
/etc/NetworkManager/system-connections/Honeypot
/etc/shadow
/etc/rc5.d/S01sav-protect
/etc/rc5.d/K01sav-rms
/etc/rc2.d/S01sav-protect
/etc/rc2.d/K01sav-rms
/etc/cups/subscriptions.conf.O
/etc/cups/ssl (errno is 13)


---

### Post by CelticWarrior on 2020-02-28
Please check the software manual or tech support to confirm.

I think that it can't check root owned files. It shouldn't matter anyway because antivirus in Linux is almost always to check for Windows malware that may be present in your personal files only (and innocuous as long as they're kept in Linux but harmful if shared with Windows users).

---

### Post by yancek on 2020-02-28
Error 13 means the user running the program didn't have permission to access the files/folders.  Generally in Ubuntu, that means you need to use sudo to run it.  I've never used Sophos so my suggestion would be to go to their site or look at the README or other files you downloaded for instructions.

---

### Post by EuclideanCoffee on 2020-03-04
You can use sudo to use that tree file on folders with root permissions. Sorry for not clarifying earlier.

---

