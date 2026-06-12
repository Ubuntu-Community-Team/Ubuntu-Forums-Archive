---
title: "Updater wants to do partial upgrade in 16.04 - but frightened by what it will REMOVE!"
date: 2018-02-17
forum: Installation &amp; Upgrades
---

### Post by crazybear on 2018-02-17
I got a "Not all updates can be installed; Run a partial ugrade" message. When I asked in terminal what would be removed and upgraded, the upgrades didn't raise any worries, BUT SOME OF THOSE TO BE REMOVED REALLY FRIGHTENED ME - INCLUDING UBUNTU DESKTOP!!!!!! Am I missing something? What should I do? Thanks. 

*N.B. I don't use unity - I have a Gnome version of 16.04, but is my understanding that there are shared files between unity and gnome, and I certainly need my desktop! I would  also thnk it wise to leave in unity in the case that gnome failed and I had to get in using unity.*

                        ```
The following packages will be REMOVED:

   [SIZE=3]libunity-2d-private0 **[SIZE=4][COLOR=#ce181e]_ubuntu-desktop_[/COLOR][/SIZE]** unity unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread unity-tweak-tool[/SIZE]

 
 
 The following packages will be upgraded:
   apt apt-transport-https apt-utils bsdutils compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default compiz-plugins-extra compiz-plugins-main
   compiz-plugins-main-default compizconfig-settings-manager gnome-disk-utility indicator-multiload libapt-inst2.0 libapt-pkg5.0 libblkid1 libcompizconfig0
   libdecoration0 libfdisk1 libmount1 libsmartcols1 libunity-control-center-dev libunity-control-center1 libuuid1 libuuid1:i386 libvala-0.36-0 libvirt-bin
   libvirt0 mount oem-audio-hda-daily-lts-xenial-dkms php-cli php-common php-gd php-xml postfix python-compizconfig qemu qemu-block-extra qemu-kvm qemu-system qemu-system-arm qemu-system-common qemu-system-mips qemu-system-misc qemu-system-ppc qemu-system-sparc qemu-system-x86 qemu-user qemu-user-static qemu-utils unity-control-center unity-control-center-faces util-linux uuid-runtime valac valac-0.36-vapi vivaldi-stable


```

---

### Post by cruzer001 on 2018-02-17
This was suppose to be fix already.

[https://ubuntuforums.org/showthread.php?t=2385070&p=13740211#post13740211](https://ubuntuforums.org/showthread.php?t=2385070&p=13740211#post13740211)

---

### Post by wildmanne39 on 2018-02-17
You should almost never do a partial upgrade in all most every case it will break ubuntu.

[https://wiki.ubuntu.com/U%2B1/partial_upgrade](https://wiki.ubuntu.com/U%2B1/partial_upgrade)

---

### Post by cruzer001 on 2018-02-17
Possibility your download source has not been updated yet.  Could change to the main server.

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by crazybear on 2018-02-18
Well, Thanks all. I wasn't going crazy after all. I'm not expert, but that looked lethal to me. As of this morning 2.18.18 it still wants to do this 'partial' upgrade (or complete demolition)! - even set on main repository...help me set the correct repository for Czech Republic although I have super highspeed internet and anywhere in the World will work fine - as long as it is giving the correct information!

---

### Post by crazybear on 2018-02-21
Hello all. You seem to indicate this was fixed, but I see nothing changed:

```
The following packages will be REMOVED:
  libunity-2d-private0 ubuntu-desktop unity unity-2d unity-2d-common unity-2d-panel unity-2d-shell
  unity-2d-spread unity-tweak-tool
The following packages will be upgraded:
  apt apt-transport-https apt-utils bsdutils chromium-browser chromium-browser-l10n
  chromium-codecs-ffmpeg-extra compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default
  compiz-plugins-extra compiz-plugins-main compiz-plugins-main-default compizconfig-settings-manager cpp-5
  cups cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-ppdc cups-server-common g++-5
  gcc-5 gcc-5-base gcc-5-base:i386 gcc-5-cross-base gcj-5-jre gcj-5-jre-headless gcj-5-jre-lib
  gir1.2-unity-5.0 gnome-disk-utility indicator-multiload lib32stdc++6 libapt-inst2.0 libapt-pkg5.0
  libasan2 libatomic1 libaudit-common libaudit1 libblkid1 libcc1-0 libcilkrts5 libcompizconfig0 libcups2
  libcups2:i386 libcupscgi1 libcupsimage2 libcupsimage2:i386 libcupsmime1 libcupsppdc1 libdecoration0
  libfdisk1 libgcc-5-dev libgcc1-armel-cross libgcj16 libgcj16-awt libgfortran3 libgomp1 libgomp1:i386
  libitm1 liblsan0 libmount1 libmpx0 libnuma-dev libnuma1 libobjc4 libpython-all-dev libpython-dev
  libpython-stdlib libquadmath0 libsane libsane:i386 libsane-common libsmartcols1 libstdc++-5-dev
  libstdc++6 libstdc++6:i386 libtsan0 libubsan0 libunity-control-center-dev libunity-control-center1
  libunity-protocol-private0 libunity-scopes-json-def-desktop libunity9 libuuid1 libuuid1:i386
  libvala-0.36-0 libvirt-bin libvirt0 mount oem-audio-hda-daily-lts-xenial-dkms opera-developer php-cli
  php-common php-gd php-xml postfix python python-all python-all-dev python-compizconfig python-dev
  python-gdbm python-minimal python-tk qemu qemu-block-extra qemu-kvm qemu-system qemu-system-arm
  qemu-system-common qemu-system-mips qemu-system-misc qemu-system-ppc qemu-system-sparc qemu-system-x86
  qemu-user qemu-user-static qemu-utils sane-utils unity-control-center unity-control-center-faces
  unity-scopes-runner util-linux uuid-runtime valac valac-0.36-vapi vivaldi-stable
132 upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
Need to get 277 MB of archives.
After this operation, 9,629 kB disk space will be freed.
```



PLEASE ADVISE how this is FIXED? Thanks.

---

### Post by cruzer001 on 2018-02-21
I didn't look close enough. 14.04 was the last release to use unity-2d. Go ahead and remove them all.  Ubuntu-desktop is a meta-pack it can also be removed.  Your running gnome desktop.

---

### Post by crazybear on 2018-02-22
> **cruzer001 said:**
> I didn't look close enough. 14.04 was the last release to use unity-2d. Go ahead and remove them all.  Ubuntu-desktop is a meta-pack it can also be removed.  Your running gnome desktop.

But I just read the warning pointed to [above] about the dangers of doing partial upgrades, and if these were really meant for 14.04, why this many years later is the system suddenly asking for their removal?

 Also, can someone give me someplace to go and assure myself that ubuntu-desktop's removal will not destroy system. Sorry, but to me this seems just too important to take any one person's word on without really knowing what will happen!

---

### Post by cruzer001 on 2018-02-22
> but to me this seems just too important to take any one person's word on without really knowing what will happen!
Ok, but you might try googling ubuntu meta packages while your waiting.

And where do you see this partial upgrade?

---

### Post by crazybear on 2018-02-23
I see this page about ubuntu-desktop that doesn't make me want to remove it without knowing more. [https://packages.ubuntu.com/xenial/ubuntu-desktop](https://packages.ubuntu.com/xenial/ubuntu-desktop) 
ubuntu-desktop: The Ubuntu desktop system

I see it pop up every day in Software Updater or if I ask the OS to do a dist-upgrade. If I just do an upgrade it installs the new programs and holds back those listed above for removal including ubuntu-desktop. I'd be the first to say I don't fully understand the system/logic here, but I don't want to destroy my OS. ubuntu-desktop seems like a core program if not THE core program - or is there a substitute in Gnome variant of 16.04?

---

### Post by again? on 2018-02-23
[MetaPackages]("https://help.ubuntu.com/community/MetaPackages") are just a list of packages to install. Removing a metapackage doesn't remove the packages it installed.

Post your full output for (**-s** flag means simulation without installing anything)
```
sudo apt **-s** full-upgrade
```
.

---

### Post by Impavidus on 2018-02-23
ubuntu-desktop is not a package you need. It's a meta-package, which is a package that conveniently triggers the installation of a bunch of other packages. Removing ubuntu-desktop won't hurt your system directly. However, it may cause your package manager to offer you to autoremove some packages that you do need.

I don't know why the package manager wants to remove those unity-2d packages right now. Maybe they have become incompatible with some other package that is to be upgraded now. No less than 59 packages are to be upgraded now, which is a lot. I also don't know why those unity-2d packages weren't remove long ago. Maybe they were on hold?

This should tell us about any problems with your packages:```
dpkg --list | egrep -v '^ii|^rc'
```That should list all packages except those normally installed or those removed with remaining configuration, listing only the packages on hold and those with some problem.

It may also be interesting to see which versions of the packages it wants to remove are currently installed:```
apt-cache policy libunity-2d-private0 ubuntu-desktop unity unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread unity-tweak-tool
```

---

### Post by vasa1 on 2018-02-23
Support for *unity-2d* was stopped around 12.10: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1035261](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1035261)

What is your current system?

Please post```
uname -a
```and```
lsb_release -a
```using code tags.

---

### Post by crazybear on 2018-02-24
> **guber2 said:**
> [MetaPackages]("https://help.ubuntu.com/community/MetaPackages") are just a list of packages to install. Removing a metapackage doesn't remove the packages it installed.

Post your full output for (**-s** flag means simulation without installing anything)
```
sudo apt **-s** full-upgrade
```
.

```

The following packages will be REMOVED:
  libunity-2d-private0 ubuntu-desktop unity unity-2d unity-2d-common
  unity-2d-panel unity-2d-shell unity-2d-spread unity-tweak-tool
The following NEW packages will be installed:
  linux-headers-4.13.0-36 linux-headers-4.13.0-36-generic
  linux-image-4.13.0-36-generic linux-image-extra-4.13.0-36-generic
The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default
  libcompizconfig0 libdecoration0 linux-generic-hwe-16.04
  linux-headers-generic-hwe-16.04 linux-image-generic-hwe-16.04
  oem-audio-hda-daily-lts-xenial-dkms
11 upgraded, 4 newly installed, 9 to remove and 0 not upgraded.

```

---

### Post by crazybear on 2018-02-24
> **Impavidus said:**
> ubuntu-desktop is not a package you need. It's a meta-package, which is a package that conveniently triggers the installation of a bunch of other packages. Removing ubuntu-desktop won't hurt your system directly. However, it may cause your package manager to offer you to autoremove some packages that you do need.

I don't know why the package manager wants to remove those unity-2d packages right now. Maybe they have become incompatible with some other package that is to be upgraded now. No less than 59 packages are to be upgraded now, which is a lot. I also don't know why those unity-2d packages weren't remove long ago. Maybe they were on hold?

This should tell us about any problems with your packages:```
dpkg --list | egrep -v '^ii|^rc'
```That should list all packages except those normally installed or those removed with remaining configuration, listing only the packages on hold and those with some problem.

It may also be interesting to see which versions of the packages it wants to remove are currently installed:```
apt-cache policy libunity-2d-private0 ubuntu-desktop unity unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread unity-tweak-tool
```


```

$ dpkg --list | egrep -v '^ii|^rc'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                        Version                                                  Architecture Description
+++-===========================================================-========================================================-============-=====================================================================================================================================================================================================================
ri  caribou                                                     0.4.20-1                                                 amd64        Configurable on screen keyboard with scanning mode
ri  dolphin4                                                    4:15.12.3-0ubuntu1                                       amd64        file browser
ri  kpart-webkit                                                1.3.4-2                                                  amd64        WebKit KPart
ri  libaudcore2:amd64                                           3.5.2.really.3.5.2-1                                     amd64        audacious core engine library
ri  libccrtp0:amd64                                             2.0.6-3                                                  amd64        Common C++ class framework for RTP packets
ri  libccrtp2v5:amd64                                           2.0.9-2.2                                                amd64        Common C++ class framework for RTP packets
ri  libclang-common-3.7-dev                                     1:3.7.1-2ubuntu2                                         amd64        clang library - Common development package
ri  libllvm3.7:amd64                                            1:3.7.1-2ubuntu2                                         amd64        Modular compiler and toolchain technologies, runtime library
ri  libllvm3.8:amd64                                            1:3.8-2ubuntu4                                           amd64        Modular compiler and toolchain technologies, runtime library
ri  libllvm3.8:i386                                             1:3.8-2ubuntu4                                           i386         Modular compiler and toolchain technologies, runtime library
ri  libllvm4.0:i386                                             1:4.0.1-0ubuntu0.16.04.3                                 i386         Modular compiler and toolchain technologies, runtime library
ri  libtxc-dxtn-s2tc0:i386                                      0~git20131104-1.1                                        i386         Texture compression library for Mesa
ri  libucommon6                                                 6.0.7-1.1                                                amd64        lightweight C++ threading and sockets - shared libraries
ri  libucommon7v5:amd64                                         6.4.4-2ubuntu1                                           amd64        lightweight C++ threading and sockets - shared libraries
ri  libvala-0.34-0:amd64                                        0.34.9-0ubuntu1~16.04~valateam0                          amd64        C# like language for the GObject system - library
ri  libxfont2:amd64                                             1:2.0.1-3~ubuntu16.04.3                                  amd64        X11 font rasterisation library
ri  libzrtpcpp2                                                 2.3.4-1.1                                                amd64        ccrtp extension for zrtp/Zfone support
ri  valac-0.34-vapi                                             0.34.9-0ubuntu1~16.04~valateam0                          all          C# like language for the GObject system - vapi files

```

```

$ apt-cache policy libunity-2d-private0 ubuntu-desktop unity unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread unity-tweak-tool
libunity-2d-private0:
  Installed: 7.2.6+14.04.20151021-0ubuntu1
  Candidate: 7.2.6+14.04.20151021-0ubuntu1
  Version table:
 *** 7.2.6+14.04.20151021-0ubuntu1 100
        100 /var/lib/dpkg/status
ubuntu-desktop:
  Installed: 1.361.1
  Candidate: 1.361.1
  Version table:
 *** 1.361.1 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.361 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
unity:
  Installed: 201511150329-7.4.0+16.04.20151102~4036~ubuntu16.04.1
  Candidate: 201511150329-7.4.0+16.04.20151102~4036~ubuntu16.04.1
  Version table:
 *** 201511150329-7.4.0+16.04.20151102~4036~ubuntu16.04.1 500
        500 http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     7.4.5+16.04.20171201.3 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
     7.4.0+16.04.20160415-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
unity-2d:
  Installed: 7.2.6+14.04.20151021-0ubuntu1
  Candidate: 7.2.6+14.04.20151021-0ubuntu1
  Version table:
 *** 7.2.6+14.04.20151021-0ubuntu1 100
        100 /var/lib/dpkg/status
unity-2d-common:
  Installed: 7.2.6+14.04.20151021-0ubuntu1
  Candidate: 7.2.6+14.04.20151021-0ubuntu1
  Version table:
 *** 7.2.6+14.04.20151021-0ubuntu1 100
        100 /var/lib/dpkg/status
unity-2d-panel:
  Installed: 7.2.6+14.04.20151021-0ubuntu1
  Candidate: 7.2.6+14.04.20151021-0ubuntu1
  Version table:
 *** 7.2.6+14.04.20151021-0ubuntu1 100
        100 /var/lib/dpkg/status
unity-2d-shell:
  Installed: 7.2.6+14.04.20151021-0ubuntu1
  Candidate: 7.2.6+14.04.20151021-0ubuntu1
  Version table:
 *** 7.2.6+14.04.20151021-0ubuntu1 100
        100 /var/lib/dpkg/status
unity-2d-spread:
  Installed: 7.2.6+14.04.20151021-0ubuntu1
  Candidate: 7.2.6+14.04.20151021-0ubuntu1
  Version table:
 *** 7.2.6+14.04.20151021-0ubuntu1 100
        100 /var/lib/dpkg/status
unity-tweak-tool:
  Installed: 0.0.7ubuntu2
  Candidate: 0.0.7ubuntu2
  Version table:
 *** 0.0.7ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial/universe i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by crazybear on 2018-02-24
> **vasa1 said:**
> Support for *unity-2d* was stopped around 12.10: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1035261](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1035261)

What is your current system?

Please post```
uname -a
```and```
lsb_release -a
```using code tags.

```

$ uname -a
Linux 4.13.0-32-generic #35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

$ lsb_release -a
LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial

```

---

### Post by crazybear on 2018-03-03
I'm still getting what I consider some very dangerous suggestions of programs or packages to be removed. Can anyone help me through this. I've avoided allowing their removal for fear of a dead OS.

```

$ sudo apt-get dist-upgrade
The following packages will be REMOVED:
  libunity-2d-private0 ubuntu-desktop unity unity-2d unity-2d-common unity-2d-panel unity-2d-shell
  unity-2d-spread unity-tweak-tool
The following NEW packages will be installed:
  linux-headers-4.13.0-36 linux-headers-4.13.0-36-generic linux-image-4.13.0-36-generic
  linux-image-extra-4.13.0-36-generic
The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default libcompizconfig0
  libdecoration0 linux-generic-hwe-16.04 linux-headers-generic-hwe-16.04
  linux-image-generic-hwe-16.04 oem-audio-hda-daily-lts-xenial-dkms
11 upgraded, 4 newly installed, 9 to remove and 0 not upgraded.


```

---

### Post by crazybear on 2018-03-06
This seems no longer to be of mild annoyance - it just caused the shut down of my system! Earlier today I upgaded to a new kernel and don't know if that alone was what caused the crash. I just booted up using the older kernel in an effort to test this....though that will take a long time. I had long had a problem apparently between my AMD GPU and 16.04...and was looking forward to 18.04 [although nothing I can see on the internet states if this problem will be solved]. Now when I am prompted to do an update it says:

```

  	 	 	 	   The following packages have been kept back:
 compiz  
 compiz-core  
 compiz-gnome  
 compiz-plugins  
 compiz-plugins-default 
 libcompizconfig0
 libdecoration0  

```

which seems innocent enough, but if I go to synaptic and check upgrade compiz, it tells me all the others I listed above that frighten me to have deleted will be deleted. Can someone kindly help me. I've had one 'trust me' remark without any proof I could see that damage would not occur.  Now, I'm also getting system crashes. Thanks.

---

### Post by crazybear on 2018-03-06
Things are QUICKLY getting out of control! I just had a second complete crash in the last few hours! If someone doesn't help me soon, I'll not have an OS to even post help messages with. All kinds of strange things are happening now. There is unusually high disk activity. Firefox keeps opening new iterations - one, then two, then three.....etc. Very high cpu usage and swap space was being used - it has never before been used and nothing special was happening. HELP!

```

$ sudo apt -s full-upgrade
The following packages will be REMOVED:
  libunity-2d-private0 **ubuntu-desktop unity unity-2d unity-2d-common**
**  unity-2d-panel unity-2d-shell unity-2d-spread unity-tweak-tool**
The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default
  libcompizconfig0 libdecoration0 oem-audio-hda-daily-lts-xenial-dkms
8 upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
Remv libunity-2d-private0 [7.2.6+14.04.20151021-0ubuntu1]
Remv ubuntu-desktop [1.361.1]
Remv unity-tweak-tool [0.0.7ubuntu2]
Remv unity-2d-panel [7.2.6+14.04.20151021-0ubuntu1]
Remv unity [201511150329-7.4.0+16.04.20151102~4036~ubuntu16.04.1] [unity-2d-common:amd64 unity-2d:amd64 unity-2d-shell:amd64 unity-2d-spread:amd64 ]
Remv unity-2d [7.2.6+14.04.20151021-0ubuntu1] [unity-2d-common:amd64 unity-2d-shell:amd64 unity-2d-spread:amd64 ]
Remv unity-2d-common [7.2.6+14.04.20151021-0ubuntu1] [unity-2d-shell:amd64 unity-2d-spread:amd64 ]
Remv unity-2d-shell [7.2.6+14.04.20151021-0ubuntu1] [unity-2d-spread:amd64 ]
Remv unity-2d-spread [7.2.6+14.04.20151021-0ubuntu1]
Inst libcompizconfig0 [1:0.9.12.2+16.04.20160823-0ubuntu1] (1:0.9.12.3+16.04.20180221-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64]) []
Inst compiz-gnome [1:0.9.12.2+16.04.20160823-0ubuntu1] (1:0.9.12.3+16.04.20180221-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64]) []
Inst compiz-plugins [1:0.9.12.2+16.04.20160823-0ubuntu1] (1:0.9.12.3+16.04.20180221-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64]) []
Inst compiz-plugins-default [1:0.9.12.2+16.04.20160823-0ubuntu1] (1:0.9.12.3+16.04.20180221-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64]) []
Inst libdecoration0 [1:0.9.12.2+16.04.20160823-0ubuntu1] (1:0.9.12.3+16.04.20180221-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64]) []
Inst compiz-core [1:0.9.12.2+16.04.20160823-0ubuntu1] (1:0.9.12.3+16.04.20180221-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64])
Inst compiz [1:0.9.12.2+16.04.20160823-0ubuntu1] (1:0.9.12.3+16.04.20180221-0ubuntu1 Ubuntu:16.04/xenial-updates [all])
Inst oem-audio-hda-daily-lts-xenial-dkms [0.201803042116~ubuntu16.04.1] (0.201803052119~ubuntu16.04.1 ALSA daily build snapshots:16.04/xenial [all])
Conf compiz-core (1:0.9.12.3+16.04.20180221-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64])
Conf libcompizconfig0 (1:0.9.12.3+16.04.20180221-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64])
Conf libdecoration0 (1:0.9.12.3+16.04.20180221-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64])
Conf compiz-plugins-default (1:0.9.12.3+16.04.20180221-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64])
Conf compiz-gnome (1:0.9.12.3+16.04.20180221-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64])
Conf compiz-plugins (1:0.9.12.3+16.04.20180221-0ubuntu1 Ubuntu:16.04/xenial-updates [amd64])
Conf compiz (1:0.9.12.3+16.04.20180221-0ubuntu1 Ubuntu:16.04/xenial-updates [all])
Conf oem-audio-hda-daily-lts-xenial-dkms (0.201803052119~ubuntu16.04.1 ALSA daily build snapshots:16.04/xenial [all])

```

---

### Post by Impavidus on 2018-03-06
I don't know what's going on on your computer. Someone else may have a clue, or maybe not. And I doubt the other problems could be caused by a package management problem. It is conceivable though that the package management problem and the other problems have a common cause, like hardware. That's a wild guess; when in doubt, you can always try to blame hardware.

**unity** is a package you probably want to keep. It actually contains some files. It may be possible to remove it and later reinstall, if necessary via console (in case removal means you can no longer log in). **unity-tweak-tool** is not vital, so it should be no problem if it gets removed. **ubuntu-desktop** is a metapackage. It can be removed, but you may want to reinstall it before running any autoremove. The other packages it wants to remove are old and should have been removed a long time ago.

You also have a  long list of unrelated packages installed, but marked for removal. I don't know why.

Will accepting the upgrade, with 8 upgrades and 9 packages removed, be safe? I don't know. I would make sure I had good backups and a live disk, so that in worst case I could just reinstall, and then accept the upgrade. If it works, nice. If it doesn't work, nothing lost.

---

### Post by crazybear on 2018-03-24
Please HELP! No one is responding and I'm almost 99.99% sure if I just let this go ahead I'll have a dead OS! What the OS wants to replace/upgrade/remove keeps changing in strange ways....it is now:

```

The following packages have been kept back:
  compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default
  libcompizconfig0 libdecoration0 linux-generic-hwe-16.04
  linux-headers-generic-hwe-16.04 linux-image-generic-hwe-16.04

```

How to I get the updates to the hwe-15.04 but not delete compiz*? Something is wrong and packages are broken, but I can't figure out how to fix all this and still have an operating system. Please suggestions. Thanks.

---

### Post by Impavidus on 2018-03-24
Have you got good backups and a tested live usb or dvd? Then nothing can go wrong. Worst case scenario is reinstalling the OS, which shouldn't take more than an hour.

I noticed that your unity comes from the lubuntu-desktop PPA. Sounds OK, but PPAs can cause package conflicts. I suggest you disable that PPA, then run the upgrade and let it remove the packages it wants to remove. If your systems breaks (not impossible, but I don't really expect it), use your live disk to get a working desktop system.

---

### Post by crazybear on 2018-03-25
> **Impavidus said:**
> Have you got good backups and a tested live usb or dvd? Then nothing can go wrong. Worst case scenario is reinstalling the OS, which shouldn't take more than an hour.

I noticed that your unity comes from the lubuntu-desktop PPA. Sounds OK, but PPAs can cause package conflicts. I suggest you disable that PPA, then run the upgrade and let it remove the packages it wants to remove. If your systems breaks (not impossible, but I don't really expect it), use your live disk to get a working desktop system.

You toss out 'use your live disk to get a working desktop system' lightly. I have a live CD disk [have tried to make live USB - but without success so far], but would _not_ know how to do this - and the back up is not that recent - a few weeks. In Synaptic it shows what will be changed and desktop will be removed [as will unity] - I'll have NO DESKTOP...which to me means I will have no system - It will remove a lot of other major programs that I consider essential to if not the core of the OS. I have used a live CD to fix grub and a few other things - but never to totally re-install the OS without destroying all the other data on the disk - I do not have the OS on a separate partition. And what will keep it from doing the same 'thing' when it upgrades everything? Will this upgrade to 18.04 when that comes out in three weeks in this condition? Where would I find a tutorial I could print out on how to rebuild the system as it is surely going to be not broken, but destroyed 100%? Surely there is another way!!! No? Thanks.

---

### Post by Impavidus on 2018-03-25
Get out of panic mode. Not daring anything won't fix your problem.

Whether you have a live usb or dvd doesn't matter, as long as you're sure you can boot it.

As stated before, the package ubuntu-desktop doesn't contain anything interesting. It only forces the installation of a large collection of interesting packages, but removing ubuntu-desktop doesn't force removal of the interesting packages. The packages that will be removed (according to your post of 2 weeks ago) are old or non-essential, except unity, but since you wrote you use gnome, not unity, even that shouldn't matter.

Depending on the configuration of your system, reinstalling may be as simple as clicking on install. If the configuration is a bit more complex, you may have to direct it the the right partition. It's basically the same as when you first installed Ubuntu. And this will definitely permanently solve your problem. It's caused by old and non-standard packages, that won't be present on a fresh install. In its present condition, you can't upgrade your system to 18.04. The upgrade might be offered, but I'm quite sure it will fail somehow.

Unless of course this problem is caused by something deeper, like hardware, but in that case there's no way to fix it anyway. So let's for the moment assume this is just a package conflict of unknown origin.

---

### Post by again? on 2018-03-25
How did you initially install linux to begin with?
Because of the myriad of ways you can customize your system and the intricacies of package management, it's sometimes hard 
to figure out what's happened or a definitive solution.
In some situations, backing up and reinstalling is the quickest and easiest solution. 

Most foolproof way to make a live usb is with dd from the command line.
This youtube playlist has all the info you need to create a live usb.
[**Making Bootable USB in Linux**]("https://www.youtube.com/playlist?list=PLSmXPSsgkZLvWbJ9XwZn-PohZxLhZcQOv")
The tutorials are quick and precise but you may need to turn on captions to grasp the accent.

Create a bootable usb and test that it indeed boots.
Then, after backing up your personal files, bite the bullet and attempt an upgrade.

---

### Post by crazybear on 2018-03-26
> **Impavidus said:**
> Get out of panic mode. Not daring anything won't fix your problem.

Whether you have a live usb or dvd doesn't matter, as long as you're sure you can boot it.

As stated before, the package ubuntu-desktop doesn't contain anything interesting. It only forces the installation of a large collection of interesting packages, but removing ubuntu-desktop doesn't force removal of the interesting packages. The packages that will be removed (according to your post of 2 weeks ago) are old or non-essential, except unity, but since you wrote you use gnome, not unity, even that shouldn't matter.

Depending on the configuration of your system, reinstalling may be as simple as clicking on install. If the configuration is a bit more complex, you may have to direct it the the right partition. It's basically the same as when you first installed Ubuntu. And this will definitely permanently solve your problem. It's caused by old and non-standard packages, that won't be present on a fresh install. In its present condition, you can't upgrade your system to 18.04. The upgrade might be offered, but I'm quite sure it will fail somehow.

Unless of course this problem is caused by something deeper, like hardware, but in that case there's no way to fix it anyway. So let's for the moment assume this is just a package conflict of unknown origin.

With all due respect, doing an 'install' will reformat the disk, reinstall the OS and delete all of the rest of the 2TB of data and programs....it would take months to get that back, while meanwhile I'll not be able to work. My set-up is complex and full of data, programs and things just the way I want/need them - not the way Ubuntu has them out of the 'box'. While I have a clone from about a month ago, I'm not even sure I'd be able to move in all those programs and information - and keep on working on an everyday basis. I earn my living on this computer - this is not for just surfing the internet for fun. I have never been successful with an 'install' alone, only upgrading from one OS to the next. I hear it is theoretically possible and many or most do that...but for me it has never worked out. The only clean install I did was 12.04 when I first was new to Ubuntu.

---

### Post by mörgæs on 2018-03-26
> **crazybear said:**
> The only clean install I did was 12.04 when I first was new to Ubuntu.

That could explain a lot of the problems you are seeing. Few people here would recommend using an initial install for so many years without reinstalls in between. 

If you use the computer for a living how are you set in case of a hard disk failure?

---

### Post by deadflowr on 2018-03-26
You can just run the update commands, and then simply reinstall the ubuntu-desktop package
```
sudo apt-get install ubuntu-desktop^
```

Somewhere along the line you removed a dependency of the ubuntu-desktop meta-package, which is why it would want to be removed.
Nothing to be alarmed about.
Reinstalling that one package after the upgrade will reset you back to normal, updater wise.

The absolute worst case scenario would be that you temporarily lose the desktop after the upgrades.
So preparing for that is simple, just make sure you have a terminal open and ready to run the install command posted.

**You can also try reinstalling the ubuntu-desktop^ package before running the upgrade, to make sure it pulls in all depends and then see what happens when you try a full upgrade/update.
(this is an after thought)

---

### Post by crazybear on 2018-03-27
> **mörgæs said:**
> That could explain a lot of the problems you are seeing. Few people here would recommend using an initial install for so many years without reinstalls in between. 

If you use the computer for a living how are you set in case of a hard disk failure?

I do monthly clones and some information files are stored in updated form on other disks.

---

### Post by crazybear on 2018-03-27
the HWE package was listed as broken, but when I checked it in Synaptic and asked it to be upgraded, it listed it would do that and to a few other packages, plus install some new kernels. It was only going to remove unity. I did this and now the system seems to be stable, OK and updated....
I guess I don't need unity [which were many packages - not just one], as I don't use it, but I thought that some programs were shared by unity and gnome - no?

---

### Post by Impavidus on 2018-03-27
If some software is shared by unity and gnome, it will be a dependency of both unity and gnome and it will be impossible to remove that software without removing both unity and gnome.

---

