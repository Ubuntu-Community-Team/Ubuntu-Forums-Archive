---
title: "Upgrade error again"
date: 2017-02-08
forum: Installation &amp; Upgrades
---

### Post by Alligator on 2017-02-08
Error doing the latest upgrade.  What have I done now?

Ron

```


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-62-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-62-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-4.4.0-62-generic; however:
  Package linux-image-extra-4.4.0-62-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.62.65); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up libnettle6:amd64 (3.2-1ubuntu0.16.04.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                           Setting up libnettle6:i386 (3.2-1ubuntu0.16.04.1) ...
Setting up libhogweed4:amd64 (3.2-1ubuntu0.16.04.1) ...
Setting up libhogweed4:i386 (3.2-1ubuntu0.16.04.1) ...
Setting up nettle-dev (3.2-1ubuntu0.16.04.1) ...
Setting up krb5-locales (1.13.2+dfsg-5ubuntu2) ...
Setting up libkrb5support0:i386 (1.13.2+dfsg-5ubuntu2) ...
Setting up libkrb5support0:amd64 (1.13.2+dfsg-5ubuntu2) ...
Setting up libk5crypto3:i386 (1.13.2+dfsg-5ubuntu2) ...
Setting up libk5crypto3:amd64 (1.13.2+dfsg-5ubuntu2) ...
Setting up libkrb5-3:i386 (1.13.2+dfsg-5ubuntu2) ...
Setting up libkrb5-3:amd64 (1.13.2+dfsg-5ubuntu2) ...
Setting up libgssapi-krb5-2:i386 (1.13.2+dfsg-5ubuntu2) ...
Setting up libgssapi-krb5-2:amd64 (1.13.2+dfsg-5ubuntu2) ...
Setting up epiphany-browser-data (3.18.10-0ubuntu1) ...
Setting up libjavascriptcoregtk-4.0-18:amd64 (2.14.3-0ubuntu0.16.04.1) ...
Setting up libgstreamer1.0-0:amd64 (1.8.3-1~ubuntu0.1) ...
Setcap worked! gst-ptp-helper is not suid!
Setting up libwebkit2gtk-4.0-37:amd64 (2.14.3-0ubuntu0.16.04.1) ...
Setting up epiphany-browser (3.18.10-0ubuntu1) ...
Setting up libwebkit2gtk-4.0-37-gtk2:amd64 (2.14.3-0ubuntu0.16.04.1) ...
Setting up firefox (51.0.1+build2-0ubuntu0.16.04.2) ...
Installing new version of config file /etc/apparmor.d/usr.bin.firefox ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (51.0.1+build2-0ubuntu0.16.04.2) ...
Setting up firefox-locale-en (51.0.1+build2-0ubuntu0.16.04.2) ...
Setting up gir1.2-gstreamer-1.0 (1.8.3-1~ubuntu0.1) ...
Setting up gir1.2-javascriptcoregtk-4.0:amd64 (2.14.3-0ubuntu0.16.04.1) ...
Setting up gir1.2-webkit2-4.0:amd64 (2.14.3-0ubuntu0.16.04.1) ...
Setting up gstreamer1.0-libav:amd64 (1.8.3-1ubuntu0.1) ...
Setting up gstreamer1.0-tools (1.8.3-1~ubuntu0.1) ...
Setting up libgssrpc4:amd64 (1.13.2+dfsg-5ubuntu2) ...
Setting up libkdb5-8:amd64 (1.13.2+dfsg-5ubuntu2) ...
Setting up libkadm5srv-mit9:amd64 (1.13.2+dfsg-5ubuntu2) ...
Setting up libgstreamer-plugins-bad1.0-0:amd64 (1.8.3-1ubuntu0.2) ...
Setting up gstreamer1.0-plugins-bad-videoparsers:amd64 (1.8.3-1ubuntu0.2) ...
Setting up gstreamer1.0-plugins-bad-faad:amd64 (1.8.3-1ubuntu0.2) ...
Setting up gstreamer1.0-plugins-bad:amd64 (1.8.3-1ubuntu0.2) ...
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-62-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-62-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin (2.23-0ubuntu5) ...
Errors were encountered while processing:
 linux-image-extra-4.4.0-62-generic
 linux-image-generic
 linux-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

____________________________________
uname -r
4.4.0-59-generic
__________________________________
df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           785M   18M  767M   3% /run
/dev/md0        720G  296G  388G  44% /
tmpfs           3.9G  5.3M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sdb1       331M  295M   18M  95% /boot
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           785M  112K  785M   1% /run/user/1001
tmpfs           785M   92K  785M   1% /run/user/1000
/dev/sdb2       661G  4.9G  656G   1% /media/ron/Data
______________________________

df -i
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             998949     584   998365    1% /dev
tmpfs           1004001     932  1003069    1% /run
/dev/md0       47947776 1124748 46823028    3% /
tmpfs           1004001      27  1003974    1% /dev/shm
tmpfs           1004001       6  1003995    1% /run/lock
tmpfs           1004001      18  1003983    1% /sys/fs/cgroup
/dev/sdb1         88352     328    88024    1% /boot
cgmfs           1004001      14  1003987    1% /run/cgmanager/fs
tmpfs           1004001      46  1003955    1% /run/user/1001
tmpfs           1004001      40  1003961    1% /run/user/1000
/dev/sdb2             0       0        0     - /media/ron/Data
_________________________________________________

sudo dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                             Version               Architecture          Description
+++-================================-=====================-=====================-=====================================================================
un  linux-image                      <none>                <none>                (no description available)
un  linux-image-3.0                  <none>                <none>                (no description available)
rc  linux-image-4.2.0-34-generic     4.2.0-34.39           amd64                 Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-28-generic     4.4.0-28.47           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-31-generic     4.4.0-31.50           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-34-generic     4.4.0-34.53           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-36-generic     4.4.0-36.55           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic     4.4.0-38.57           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-42-generic     4.4.0-42.62           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-43-generic     4.4.0-43.63           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-45-generic     4.4.0-45.66           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-47-generic     4.4.0-47.68           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-51-generic     4.4.0-51.72           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-53-generic     4.4.0-53.74           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-57-generic     4.4.0-57.78           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-59-generic     4.4.0-59.80           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-generic     4.4.0-62.83           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-34-gener 4.2.0-34.39           amd64                 Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-28-gener 4.4.0-28.47           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-31-gener 4.4.0-31.50           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-34-gener 4.4.0-34.53           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-36-gener 4.4.0-36.55           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-gener 4.4.0-38.57           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-42-gener 4.4.0-42.62           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-43-gener 4.4.0-43.63           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-45-gener 4.4.0-45.66           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-47-gener 4.4.0-47.68           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-51-gener 4.4.0-51.72           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-53-gener 4.4.0-53.74           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-57-gener 4.4.0-57.78           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-59-gener 4.4.0-59.80           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-62-gener 4.4.0-62.83           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic              4.4.0.62.65           amd64                 Generic Linux kernel image




```

---

### Post by Impavidus on 2017-02-08
Your /boot partition is full. Try first purging kernel 4.4.0-57```
sudo dpkg -P linux-image-4.4.0-57-generic linux-image-extra-4.4.0-57-generic
```
then fixing the packages```
sudo apt-get install -f
```

---

### Post by Alligator on 2017-02-08
Thank you.  That went well, but with the next error.

```


The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer

The download will be attempted again later, or you can try the download again now. Running this command requires an active Internet connection.
___________________________________
Crash report
Problem occured while installing software
Package: linux-image-extra-4.4.0-62-generic 4.4.0-62.83

```

---

### Post by Impavidus on 2017-02-08
The first message (about ttf-mscorefonts-installer) is not important. There are several threads about that problem and it's just about some fonts.

For the second, we need to know the current status of your packages.```
dpkg -l linux-image\*
```If anything is listed as half-configured (F in the second column), then try to configure it with```
sudo dpkg --configure -a
```If there are error messages, show the complete output.

---

### Post by ajgreeny on 2017-02-08
RE: TTF-MSCOREFONTS-INS WON'T COMPLETE

    The script that the the package runs to download the fonts from sourceforge is pointing at the wrong location, so run command ```
sudo touch /var/lib/update-notifier/package-data-downloads/ttf-mscorefonts-installer
```
    You won't get any feedback in the terminal after entering the command but it will stop the prompts.

    I suggest also purging the 3.4 version of the package and install the 3.6 version instead as follows.
    ```
sudo apt purge ttf-mscorefonts-installer[code] and then [code]wget http://ftp.de.debian.org/debian/pool...er_3.6_all.deb -P ~/Downloads
``` which will download the package to your Downloads folder, and then ```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
``` to install the package.

---

### Post by Alligator on 2017-02-08
No failures from dpkg -l linux-image\*

Can't find ftp.de.debian.org

---

### Post by howefield on 2017-02-08
> **Alligator said:**
> Can't find ftp.de.debian.org

Temporary issue I'd suspect, but this one should work..

```
wget http://ftp.us.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```

---

### Post by Alligator on 2017-02-08
I tried the ca site with same error.

---

### Post by Alligator on 2017-02-08
Solved - Thank you.  One more error with cupsd.  I don't have my printer always plugged in or turned on. Error message on reboot.  HP laserjet P1006. This is only a slight pain.  Printer works when activated.

---

