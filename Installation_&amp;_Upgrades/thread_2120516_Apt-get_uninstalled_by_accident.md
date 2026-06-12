---
title: "Apt-get uninstalled by accident"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by kjohnsting on 2013-02-26
HELP! I removed apt-get accidently. How do I get it back on? Is there a operating system repair that could shoot it back in?

[B]$sudo uname -a
Linux hostname 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux[/B]

---

### Post by steeldriver on 2013-02-26
If the .deb file is still in your apt-cache, you should be able to reinstall it using dpkg from there

```
ls /var/cache/apt/archives | grep apt
```If it's already been cleaned, you should be able to download the appropriate .deb individually

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by kjohnsting on 2013-02-26
There are no results from running the ls command. 

Can you assist in figuring out which deb is correct? I believe tried this before and it kept failing.

for example:

root@web1:/# dpkg -i apt_0.8.16~exp12ubuntu10.7_amd64.deb                  dpkg: error processing apt_0.8.16~exp12ubuntu10.7_amd64.deb (--install):
 apt: 0.8.16~exp12ubuntu10.7 (Multi-Arch: no) is not co-installable with apt:i386 0.8.16~exp12ubuntu10.7 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 apt_0.8.16~exp12ubuntu10.7_amd64.deb

---

### Post by steeldriver on 2013-02-26
Hmm... try this maybe?

```
 dpkg-query --print-avail apt
```

How exactly did you remove it?

---

### Post by kjohnsting on 2013-02-26
Not sure how I removed it.

root@web1:/# dpkg-query --print-avail apt
Package: apt
Priority: important
Section: admin
Installed-Size: 3167
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 0.8.16~exp12ubuntu10.7
Replaces: manpages-pl (<< 20060617-3~)
Depends: ubuntu-keyring, libapt-pkg4.12 (>= 0.8.16~exp12ubuntu10.7), libc6 (>= 2.15), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.6), gnupg
Pre-Depends: dpkg (>= 1.15.7.2)
Suggests: aptitude | synaptic | wajig, dpkg-dev, apt-doc, bzip2, lzma, python-apt
Conflicts: python-apt (<< 0.7.93.2~)
Filename: pool/main/a/apt/apt_0.8.16~exp5ubuntu13_amd64.deb
Size: 1092096
MD5sum: 3af35190986fd7ea443aca80c34286b9
Description: commandline package manager
 This package provides commandline tools for searching and
 managing as well as querying information about packages
 as a low-level access to all features of the libapt-pkg library.
 .
 These include:
  * apt-get for retrieval of packages and information about them
    from authenticated sources and for installation, upgrade and
    removal of packages together with their dependencies
  * apt-cache for querying available information about installed
    as well as installable packages
  * apt-cdrom to use removable media as a source for packages
  * apt-config as an interface to the configuration settings
  * apt-key as an interface to manage authentication keys
Original-Maintainer: APT Development Team <deity@lists.debian.org>

---

### Post by tgalati4 on 2013-02-26
There may be something else going on, like a failing hard disk that is trashing programs in /usr/bin.  See if aptitude works.  It's separate from apt:

In a terminal:

```
aptitude
```See if your repositories are read correctly and if any errors come up.
```

tgalati4@Mint14-Extensa ~ $ apt-cache depends synaptic
synaptic
  Depends: libapt-inst1.5
  Depends: libapt-pkg4.12
  Depends: libc6
  Depends: libept1.4.12
  Depends: libgcc1
  Depends: libgdk-pixbuf2.0-0
  Depends: libglib2.0-0
  Depends: libgtk2.0-0
  Depends: libpango1.0-0
  Depends: libstdc++6
  Depends: libvte9
  Depends: libx11-6
  Depends: libxapian22
  Depends: hicolor-icon-theme
  Suggests: dwww
  Suggests: menu
  Suggests: deborphan
  Suggests: apt-xapian-index
 |Recommends: gksu
 |Recommends: kdebase-bin
  Recommends: policykit-1
    policykit-1:i386
  Recommends: libgtk2-perl
  Recommends: rarian-compat
  Recommends: software-properties-gtk
  Conflicts: menu
  Conflicts: menu:i386
  Conflicts: synaptic:i386
tgalati4@Mint14-Extensa ~ $ apt-cache depends aptitude
aptitude
  Depends: aptitude-common
  Depends: libapt-pkg4.12
  Depends: libboost-iostreams1.49.0
  Depends: libc6
  Depends: libcwidget3
  Depends: libept1.4.12
  Depends: libgcc1
  Depends: libncursesw5
  Depends: libsigc++-2.0-0c2a
  Depends: libsqlite3-0
  Depends: libstdc++6
  Depends: libtinfo5
  Depends: libxapian22
 |Suggests: aptitude-doc-en
  Suggests: <aptitude-doc>
    aptitude-doc-cs
    aptitude-doc-en
    aptitude-doc-es
    aptitude-doc-fi
    aptitude-doc-fr
    aptitude-doc-it
    aptitude-doc-ja
  Suggests: tasksel
  Suggests: debtags
  Recommends: sensible-utils
  Recommends: apt-xapian-index
  Recommends: libparse-debianchangelog-perl
  Conflicts: <ia32-apt-get>
  Conflicts: <ia32-apt-get:i386>
  Conflicts: aptitude:i386
tgalati4@Mint14-Extensa ~ $ apt-cache depends apt
apt
  Depends: ubuntu-keyring
  Depends: libapt-pkg4.12
  Depends: libc6
  Depends: libgcc1
  Depends: libstdc++6
  Depends: gnupg
    gnupg:i386
 |Suggests: aptitude
 |Suggests: synaptic
  Suggests: wajig
  Suggests: dpkg-dev
  Suggests: apt-doc
  Suggests: xz-utils
    xz-utils:i386
  Suggests: python-apt
  Conflicts: python-apt
  Conflicts: python-apt:i386
  Replaces: manpages-pl
  Replaces: <manpages-pl:i386>
  Conflicts: apt:i386
```

For that matter, synaptic should still work, since the shared libraries should remain if your package manager is working correctly.

I can't wrap my head around how you would delete apt?

---

### Post by kjohnsting on 2013-02-26
Don't get me wrong, I DID uninstall or delete it. I remember the moment. I just don't remember the commands I used.

root@web1:~# aptitude
aptitude: error while loading shared libraries: libapt-pkg.so.4.12: cannot open shared object file: No such file or directory

---

### Post by steeldriver on 2013-02-26
From your post #3 it looks like you may have a 32-bit version installed? what does

```
dpkg --list apt
```say?

---

### Post by kjohnsting on 2013-02-26
root@web1:~# dpkg --list apt
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                        Version                                     Description
+++-===========================================-===========================================-======================================================================================================
in  apt                                         <none>                                      (no description available)

---

### Post by steeldriver on 2013-02-26
sorry maybe that should have been

```
 dpkg-query --list apt[COLOR=Red]:i386[/COLOR]
```

---

### Post by kjohnsting on 2013-02-26
root@web1:~#  dpkg-query --list apt:i386
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                        Version                                     Description
+++-===========================================-===========================================-======================================================================================================
iU  apt:i386                                    0.8.16~exp12ubuntu10.7                      commandline package manager

---

### Post by steeldriver on 2013-02-26
well I don't know enough about multiarch configs to advise you - sorry

it looks like maybe some other i386 package you installed pulled in apt:i386 as a dependency, and uninstalled the 'conflicting' amd64 package, and then left the :i386 version unpacked but uninstalled (iU)

---

### Post by matt_symes on 2013-02-26
Hi

> ubuntu-keyring, libapt-pkg4.12 (>= 0.8.16~exp12ubuntu10.7), libc6  (>= 2.15), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.6), gnupgThese are the packages apt directly depends on.

This one is missing libapt-pkg4.12. I suspect the others are not. 

libc6 is not missing and neither is libstdc++. You would know if they were by now :)

I suspect the other 2 are not missing  but lets just check. Please post the output of.

```
dpkg -l gnupg
```and 

```
dpkg -l ubuntu-keyring
```also post the output  of

```
uname -a
``````
cat /etc/lsb-release
```The predepends file dpkg is, of course, installed.

We should be able to get the packages for you with this information.

Kind regards

---

### Post by kjohnsting on 2013-02-27
root@web1:~# **dpkg -l gnupg**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  gnupg          1.4.11-3ubuntu GNU privacy guard - a free PGP replacement


root@web1:~# **dpkg -l ubuntu-keyring**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  ubuntu-keyring 2011.11.21.1   GnuPG keys of the Ubuntu archive


root@web1:~# **uname -a**
Linux web1.domain.com 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux



root@web1:~# **cat /etc/lsb-release**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"

---

### Post by matt_symes on 2013-02-27
Hi
```

root@web1:~#  dpkg-query --list apt:i386
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                        Version                                     Description
+++-===========================================-===========================================-==================================================   ==================================================  ==
iU  apt:i386                                    0.8.16~exp12ubuntu10.7                      commandline package manager
```

You need to remove this version of apt. It's not fully installed.

```
sudo dpkg -r  apt:i386
```

I'll look for the libraries you need.

Kind regards

---

### Post by kjohnsting on 2013-02-27
Completed, rebooting

---

### Post by matt_symes on 2013-02-27
Hi

After that.

```
cd && wget http://security.ubuntu.com/ubuntu/pool/main/a/apt/libapt-pkg4.12_0.8.16~exp12ubuntu10.7_amd64.deb
```

```
sudo dpkg -i libapt-pkg4.12_0.8.16~exp12ubuntu10.7_amd64.deb
```

Post back on how that step went but do it soon please as i am off for beer soon :)

Kind regards

---

### Post by kjohnsting on 2013-02-27
root@web1:~# cd && wget [http://security.ubuntu.com/ubuntu/pool/main/a/apt/l](http://security.ubuntu.com/ubuntu/pool/main/a/apt/l)                                                                                                                                ibapt-pkg4.12_0.8.16~exp12ubuntu10.7_amd64.deb
--2013-02-27 14:11:08--  [http://security.ubuntu.com/ubuntu/pool/main/a/apt/libap](http://security.ubuntu.com/ubuntu/pool/main/a/apt/libap)                                                                                                                                t-pkg4.12_0.8.16~exp12ubuntu10.7_amd64.deb
Resolving security.ubuntu.com (security.ubuntu.com)... 91.189.92.200, 91.189.91.                                                                                                                                13
Connecting to security.ubuntu.com (security.ubuntu.com)|91.189.92.200|:80... con                                                                                                                                nected.
HTTP request sent, awaiting response... 200 OK
Length: 933732 (912K) [application/x-debian-package]
Saving to: `libapt-pkg4.12_0.8.16~exp12ubuntu10.7_amd64.deb'

100%[======================================>] 933,732     1.14M/s   in 0.8s

2013-02-27 14:11:09 (1.14 MB/s) - `libapt-pkg4.12_0.8.16~exp12ubuntu10.7_amd64.d                                                                                                                                eb' saved [933732/933732]

root@web1:~# dpkg -i libapt-pkg4.12_0.8.16~exp12ubuntu10.7_amd64.deb
Selecting previously unselected package libapt-pkg4.12.
(Reading database ... 182419 files and directories currently installed.)
Unpacking libapt-pkg4.12 (from libapt-pkg4.12_0.8.16~exp12ubuntu10.7_amd64.deb)                                                                                                                                 ...
Setting up libapt-pkg4.12 (0.8.16~exp12ubuntu10.7) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by matt_symes on 2013-02-27
Hi

```
cd && wget http://security.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.8.16~exp12ubuntu10.7_amd64.deb
``````
sudo dpkg -i apt_0.8.16~exp12ubuntu10.7_amd64.deb
```Post back on this next step.

Kind regards

---

### Post by kjohnsting on 2013-02-27
root@web1:~# cd && wget [http://security.ubuntu.com/ubuntu/pool/main/a/apt/a](http://security.ubuntu.com/ubuntu/pool/main/a/apt/a)                                                                                                                                pt_0.8.16~exp12ubuntu10.7_amd64.deb
--2013-02-27 14:32:05--  [http://security.ubuntu.com/ubuntu/pool/main/a/apt/apt_0](http://security.ubuntu.com/ubuntu/pool/main/a/apt/apt_0)                                                                                                                                .8.16~exp12ubuntu10.7_amd64.deb
Resolving security.ubuntu.com (security.ubuntu.com)... 91.189.92.200, 91.189.91.                                                                                                                                13
Connecting to security.ubuntu.com (security.ubuntu.com)|91.189.92.200|:80... con                                                                                                                                nected.
HTTP request sent, awaiting response... 200 OK
Length: 1092096 (1.0M) [application/x-debian-package]
Saving to: `apt_0.8.16~exp12ubuntu10.7_amd64.deb'

100%[======================================>] 1,092,096   1.28M/s   in 0.8s

2013-02-27 14:32:06 (1.28 MB/s) - `apt_0.8.16~exp12ubuntu10.7_amd64.deb' saved [                                                                                                                                1092096/1092096]

root@web1:~# dpkg -i apt_0.8.16~exp12ubuntu10.7_amd64.deb
(Reading database ... 182421 files and directories currently installed.)
Unpacking apt (from apt_0.8.16~exp12ubuntu10.7_amd64.deb) ...
(Noting disappearance of apt:i386, which has been completely replaced.)
Setting up apt (0.8.16~exp12ubuntu10.7) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"                                                                                                                                 not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"                                                                                                                                 not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubunt                                                                                                                                u.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu                                                                                                                                .com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
Processing triggers for man-db ...

---

### Post by kjohnsting on 2013-02-27
After successfully running "apt-get update" I ran "apt-get upgrade" and received this output...

root@web1:~# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libapt-pkg4.12:i386 : Depends: libc6:i386 (>= 2.15) but it is not installed
                       Depends: libgcc1:i386 (>= 1:4.1.1) but it is not installed
                       Depends: libstdc++6:i386 (>= 4.6) but it is not installed
                       Depends: zlib1g:i386 (>= 1:1.2.3.3.dfsg) but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by kjohnsting on 2013-02-27
Sorry, running 'apt-get -f install'

---

### Post by matt_symes on 2013-02-27
.

---

### Post by kjohnsting on 2013-02-27
Looks like I am running out of free space, maybe on the boot partition?

root@web1:~# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gcc-4.6-base:i386 libc6:i386 libgcc1:i386 libstdc++6:i386 zlib1g:i386
Suggested packages:
  glibc-doc:i386 locales:i386
The following NEW packages will be installed:
  gcc-4.6-base:i386 libc6:i386 libgcc1:i386 libstdc++6:i386 zlib1g:i386
0 upgraded, 5 newly installed, 0 to remove and 74 not upgraded.
6 not fully installed or removed.
Need to get 4,394 kB of archives.
After this operation, 11.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main gcc-4.6-base i386 4.6.3-1ubuntu5 [15.3 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libgcc1 i386 1:4.6.3-1ubuntu5 [54.3 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libc6 i386 2.15-0ubuntu10.3 [3,940 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libstdc++6 i386 4.6.3-1ubuntu5 [333 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main zlib1g i386 1:1.2.3.4.dfsg-3ubuntu4 [51.1 kB]
Fetched 4,394 kB in 1s (2,896 kB/s)
Preconfiguring packages ...
Selecting previously unselected package gcc-4.6-base:i386.
(Reading database ... 182581 files and directories currently installed.)
Unpacking gcc-4.6-base:i386 (from .../gcc-4.6-base_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package libgcc1:i386.
Unpacking libgcc1:i386 (from .../libgcc1_1%3a4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package libc6:i386.
Unpacking libc6:i386 (from .../libc6_2.15-0ubuntu10.3_i386.deb) ...
Selecting previously unselected package libstdc++6:i386.
Unpacking libstdc++6:i386 (from .../libstdc++6_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package zlib1g:i386.
Unpacking zlib1g:i386 (from .../zlib1g_1%3a1.2.3.4.dfsg-3ubuntu4_i386.deb) ...
Setting up gcc-4.6-base:i386 (4.6.3-1ubuntu5) ...
Setting up initramfs-tools (0.99ubuntu13) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.2.0-32-generic (3.2.0-32.51) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.2.0-33-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-32-generic /boot/vmlinuz-3.2.0-32-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-32-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-32-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-32-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-33-generic (3.2.0-33.52) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.2.0-32-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-33-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-33-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-33-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-33-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-3.2.0-32-generic; however:
  Package linux-image-3.2.0-32-generic is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.32.35); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
Setting up libc6:i386 (2.15-0ubuntu10.3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                                                                                                                                                        Setting up zlib1g:i386 (1:1.2.3.4.dfsg-3ubuntu4) ...
Setting up libgcc1:i386 (1:4.6.3-1ubuntu5) ...
Setting up libstdc++6:i386 (4.6.3-1ubuntu5) ...
Setting up libapt-pkg4.12:i386 (0.8.16~exp12ubuntu10.7) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-31-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-31-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-3.2.0-32-generic
 linux-image-3.2.0-33-generic
 linux-image-server
 linux-server
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kjohnsting on 2013-02-27
root@web1:~# df
Filesystem                 1K-blocks    Used Available Use% Mounted on
/dev/mapper/fbpa1web1-root  19344076 3560288  14801160  20% /
udev                          241124       4    241120   1% /dev
tmpfs                         100688     244    100444   1% /run
none                            5120       0      5120   0% /run/lock
none                          251712       4    251708   1% /run/shm
/dev/sda1                     233191  227036         0 100% /boot
/home/user/.Private    19344076 3560288  14801160  20% /home/user

---

### Post by matt_symes on 2013-02-27
Hi

From the terminal post the output of 

```
df -h
```If your boot partition is almost full the delete the oldest kernels but keep the two newest.

after that run

```
sudo apt-get install -f
```Kind regards

---

### Post by kjohnsting on 2013-02-27
root@web1:~# df -h
Filesystem                  Size  Used Avail Use% Mounted on
/dev/mapper/fbpa1web1-root   19G  3.4G   15G  20% /
udev                        236M  4.0K  236M   1% /dev
tmpfs                        99M  244K   99M   1% /run
none                        5.0M     0  5.0M   0% /run/lock
none                        246M  4.0K  246M   1% /run/shm
/dev/sda1                   228M  222M     0 100% /boot
/home/user/.Private     19G  3.4G   15G  20% /home/user

---

### Post by kjohnsting on 2013-02-27
How do I delete the oldest kernels except for the two latest?

---

### Post by matt_symes on 2013-02-27
Hi
```

/dev/sda1                     233191  227036         0 100% /boot
```

Full boot partition.

Use the output of 

```
dpkg -l | grep linux-image
```

to delete your oldest kernels but keep at least 2.

If you need help post back.

Kind regards

---

### Post by matt_symes on 2013-02-27
Hi

Post the output of this

```
dpkg -l | grep linux-image
```

Kind regards

---

### Post by kjohnsting on 2013-02-27
root@web1:~# dpkg -l | grep linux-image
ii  linux-image-3.0.0-12-server      3.0.0-12.20                      Linux kernel image for version 3.0.0 on x86_64
ii  linux-image-3.0.0-16-server      3.0.0-16.29                      Linux kernel image for version 3.0.0 on x86_64
ii  linux-image-3.0.0-21-server      3.0.0-21.35                      Linux kernel image for version 3.0.0 on x86_64
ii  linux-image-3.2.0-26-generic     3.2.0-26.41                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-27-generic     3.2.0-27.43                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-29-generic     3.2.0-29.46                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-30-generic     3.2.0-30.48                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-31-generic     3.2.0-31.50                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-32-generic     3.2.0-32.51                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-33-generic     3.2.0-33.52                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iU  linux-image-server               3.2.0.32.35                      Linux kernel image on Server Equipment.

---

### Post by matt_symes on 2013-02-27
Hi> 

ii  linux-image-3.0.0-12-server      3.0.0-12.20                      Linux kernel image for version 3.0.0 on x86_64
ii  linux-image-3.0.0-16-server      3.0.0-16.29                      Linux kernel image for version 3.0.0 on x86_64
ii  linux-image-3.0.0-21-server      3.0.0-21.35                      Linux kernel image for version 3.0.0 on x86_64

We'll get rid of these three to get you fixed but *you will need to delete some more soon*. *Read up on this*.

```
sudo dpkg -P linux-image-3.0.0-{12,16,21}-server
```

```
sudo apt-get install -f
```

after that post back the output

```
ls -l /boot
```

to do the final cleanup.

Kind regards

---

### Post by matt_symes on 2013-02-27
Hi

I'll be back in half hour. Maybe :)

Kind regards

---

### Post by kjohnsting on 2013-02-27
Cheers! Have a pint for me! I'm stuck in the office until quiting time

---

### Post by kjohnsting on 2013-02-27
root@web1:~# ls -l /boot
total 157099
-rw-r--r-- 1 root root   791281 Jul  6  2012 abi-3.2.0-27-generic
-rw-r--r-- 1 root root   791281 Jul 27  2012 abi-3.2.0-29-generic
-rw-r--r-- 1 root root   791446 Aug 24  2012 abi-3.2.0-30-generic
-rw-r--r-- 1 root root   791446 Sep  7 12:57 abi-3.2.0-31-generic
-rw-r--r-- 1 root root   792532 Sep 26 18:14 abi-3.2.0-32-generic
-rw-r--r-- 1 root root   792532 Oct 18 13:10 abi-3.2.0-33-generic
-rw-r--r-- 1 root root   140454 Jul  6  2012 config-3.2.0-27-generic
-rw-r--r-- 1 root root   140432 Jul 27  2012 config-3.2.0-29-generic
-rw-r--r-- 1 root root   140432 Aug 24  2012 config-3.2.0-30-generic
-rw-r--r-- 1 root root   140459 Sep  7 12:57 config-3.2.0-31-generic
-rw-r--r-- 1 root root   140488 Sep 26 18:14 config-3.2.0-32-generic
-rw-r--r-- 1 root root   140488 Oct 18 13:10 config-3.2.0-33-generic
drwxr-xr-x 3 root root     5120 Feb 27 14:58 grub
-rw-r--r-- 1 root root 17854047 Aug 13  2012 initrd.img-3.2.0-27-generic
-rw-r--r-- 1 root root 17849742 Aug 13  2012 initrd.img-3.2.0-29-generic
-rw-r--r-- 1 root root 17855940 Sep  6 09:13 initrd.img-3.2.0-30-generic
-rw-r--r-- 1 root root 17860262 Oct  5 13:41 initrd.img-3.2.0-31-generic
-rw-r--r-- 1 root root 17862472 Feb 27 14:51 initrd.img-3.2.0-32-generic
-rw-r--r-- 1 root root 17865308 Feb 27 14:59 initrd.img-3.2.0-33-generic
drwxr-xr-x 2 root root    12288 Feb  2  2012 lost+found
-rw-r--r-- 1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r-- 1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw------- 1 root root  2882027 Jul  6  2012 System.map-3.2.0-27-generic
-rw------- 1 root root  2882108 Jul 27  2012 System.map-3.2.0-29-generic
-rw------- 1 root root  2883362 Aug 24  2012 System.map-3.2.0-30-generic
-rw------- 1 root root  2883401 Sep  7 12:57 System.map-3.2.0-31-generic
-rw------- 1 root root  2884076 Sep 26 18:14 System.map-3.2.0-32-generic
-rw------- 1 root root  2884306 Oct 18 13:10 System.map-3.2.0-33-generic
-rw------- 1 root root  4960848 Jul  6  2012 vmlinuz-3.2.0-27-generic
-rw------- 1 root root  4960752 Jul 27  2012 vmlinuz-3.2.0-29-generic
-rw------- 1 root root  4963280 Aug 24  2012 vmlinuz-3.2.0-30-generic
-rw------- 1 root root  4963792 Sep  7 12:57 vmlinuz-3.2.0-31-generic
-rw------- 1 root root  4966768 Sep 26 18:14 vmlinuz-3.2.0-32-generic
-rw------- 1 root root  4966896 Oct 18 13:10 vmlinuz-3.2.0-33-generic

---

### Post by kjohnsting on 2013-02-27
What the best way to manage the boot partition? I manually update every week. Are there certain commands I should be running afterwards to keep the max images to three?

---

### Post by kjohnsting on 2013-02-27
Looks good. Ran all of the upgrade and dist-upgrade commands, rebooted, no more available updates. I will grab an image of this soon for backup. 

I can't thank you enough! I was trying to build a replacement server and migrate my wordpress to it. That was a pain. But no longer needed, thanks to you!

---

### Post by matt_symes on 2013-02-27
Hi

I'm glad it's fixed.  :D

Tidy up your boot partition. You can free up a lot of space.

As this is a server i would suggest leaving at least three kernels and associated initramfs.

The newest and 2 known good ones. Always update your kernel when given the option for security reasons.

I got my beer and i'm off to drink it.

Kind regards

---

### Post by schragge on 2013-02-27
> **kjohnsting said:**
> What the best way to manage the boot partition? I manually update every week. Are there certain commands I should be running afterwards to keep the max images to three?
You can try this script
```

#!/bin/sh
prev=`readlink /vmlinuz.old` && prev=linux-image-${prev#*-}+
exec sudo apt-get purge '^linux-image-[0-9]' linux-image-`uname -r`+ $prev

```Save it in a file and make executable (chown +x). You can first test if it works right by placing the **-s** option (--simulate) in there:
```

#!/bin/sh
prev=`readlink /vmlinuz.old` && prev=linux-image-${prev#*-}+
exec sudo apt-get [COLOR=red]-s[/COLOR] purge '^linux-image-[0-9]' linux-image-`uname -r`+ $prev

```If the output matches your expectations, remove [COLOR=red]-s[/COLOR] and run the script again. There should be only two latest kernels left after it.

To keep three kernel images, you could try
```
sudo apt-get purge $(ls -I`uname -r` -rv /lib/modules | sed -n '3,$s/^/^linux-image-/p')
```

---

