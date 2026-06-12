---
title: "Sub-process /usr/bin/dpkg returned an error code"
date: 2015-12-24
forum: Installation &amp; Upgrades
---

### Post by andrewmc2 on 2015-12-24
I have installing anything. Its does not matter what I'm trying to install. Even doe for example usual mc and it ends with same error always. Please help to solve this issue.
I am running Ubuntu with Cinnamon(partially installed).

```
andrew@lab00t:~$ sudo apt-get install mc

The following packages were automatically installed and are no longer required:
  libtorrent-rasterbar7 linux-headers-3.19.0-15
  linux-headers-3.19.0-15-generic linux-headers-generic
  linux-image-3.19.0-15-generic linux-image-extra-3.19.0-15-generic thermald
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libssh2-1 mc-data
Suggested packages:
  arj catdvi texlive-binaries dbview djvulibre-bin gv imagemagick links w3m
  lynx odt2txt python-boto python-tz
The following packages will be REMOVED:
  linux-image-extra-3.19.0-41-generic
The following NEW packages will be installed:
  libssh2-1 mc mc-data
0 upgraded, 3 newly installed, 1 to remove and 38 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1 698 kB of archives.
After this operation, 154 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 307435 files and directories currently installed.)
Removing linux-image-extra-3.19.0-41-generic (3.19.0-41.46) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-41-generic /boot/vmlinuz-3.19.0-41-generic
run-parts: failed to stat component /etc/kernel/postinst.d/dkms: No such file or directory
dpkg: error processing package linux-image-extra-3.19.0-41-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.19.0-41-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@lab00t:~$
```

---

### Post by matt_symes on 2015-12-24
Hi

Can we check your sources. Please post the output of this command. Copy and paste it into the terminal.

```
grep "^[^#]" /etc/apt/sources.list{,.d/*}
```

Kind regards

---

### Post by andrewmc2 on 2015-12-25
```

andrew@lab00t:~$ grep "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) vivid main restricted
/etc/apt/sources.list:deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) vivid multiverse main universe restricted #Added by software-properties
/etc/apt/sources.list:deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) vivid-updates main restricted
/etc/apt/sources.list:deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) vivid-updates multiverse main universe restricted #Added by software-properties
/etc/apt/sources.list:deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) vivid universe
/etc/apt/sources.list:deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) vivid-updates universe
/etc/apt/sources.list:deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) vivid multiverse
/etc/apt/sources.list:deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) vivid-updates multiverse
/etc/apt/sources.list:deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) vivid-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) vivid-backports main restricted universe multiverse #Added by software-properties
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security main restricted
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security multiverse main universe restricted #Added by software-properties
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security multiverse
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
/etc/apt/sources.list:deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
/etc/apt/sources.list:deb [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) vivid-proposed multiverse main universe restricted
/etc/apt/sources.list.d/canonical-qt5-edgers-ubuntu-qt5-proper-vivid.list:deb [http://ppa.launchpad.net/canonical-qt5-edgers/qt5-proper/ubuntu](http://ppa.launchpad.net/canonical-qt5-edgers/qt5-proper/ubuntu) vivid main
/etc/apt/sources.list.d/canonical-qt5-edgers-ubuntu-qt5-proper-vivid.list.saveeb [http://ppa.launchpad.net/canonical-qt5-edgers/qt5-proper/ubuntu](http://ppa.launchpad.net/canonical-qt5-edgers/qt5-proper/ubuntu) vivid main
/etc/apt/sources.list.d/getdeb.list.save:deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) vivid-getdeb apps
/etc/apt/sources.list.d/gnome3-team-ubuntu-gnome3-vivid.list:deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) vivid main
/etc/apt/sources.list.d/gnome3-team-ubuntu-gnome3-vivid.list.save:deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) vivid main
/etc/apt/sources.list.d/gwendal-lebihan-dev-ubuntu-cinnamon-nightly-vivid.listeb [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu) vivid main
/etc/apt/sources.list.d/gwendal-lebihan-dev-ubuntu-cinnamon-nightly-vivid.listeb-src [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu) vivid main
/etc/apt/sources.list.d/gwendal-lebihan-dev-ubuntu-cinnamon-nightly-vivid.list.save:deb [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu) vivid main
/etc/apt/sources.list.d/gwendal-lebihan-dev-ubuntu-cinnamon-nightly-vivid.list.save:deb-src [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-nightly/ubuntu) vivid main
/etc/apt/sources.list.d/metasploit-framework.list:deb [http://downloads.metasploit.com/data/releases/metasploit-framework/apt](http://downloads.metasploit.com/data/releases/metasploit-framework/apt) lucid main
/etc/apt/sources.list.d/metasploit-framework.list.save:deb [http://downloads.metasploit.com/data/releases/metasploit-framework/apt](http://downloads.metasploit.com/data/releases/metasploit-framework/apt) lucid main
/etc/apt/sources.list.d/moorkai-ubuntu-cinnamon-vivid.list:deb [http://ppa.launchpad.net/moorkai/cinnamon/ubuntu](http://ppa.launchpad.net/moorkai/cinnamon/ubuntu) vivid main
/etc/apt/sources.list.d/moorkai-ubuntu-cinnamon-vivid.list:deb-src [http://ppa.launchpad.net/moorkai/cinnamon/ubuntu](http://ppa.launchpad.net/moorkai/cinnamon/ubuntu) vivid main
/etc/apt/sources.list.d/moorkai-ubuntu-cinnamon-vivid.list.save:deb [http://ppa.launchpad.net/moorkai/cinnamon/ubuntu](http://ppa.launchpad.net/moorkai/cinnamon/ubuntu) vivid main
/etc/apt/sources.list.d/moorkai-ubuntu-cinnamon-vivid.list.save:deb-src [http://ppa.launchpad.net/moorkai/cinnamon/ubuntu](http://ppa.launchpad.net/moorkai/cinnamon/ubuntu) vivid main
/etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-vivid.list:deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) vivid main
/etc/apt/sources.list.d/otto-kesselgulasch-ubuntu-gimp-vivid.list.save:deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) vivid main
/etc/apt/sources.list.d/playdeb.list:deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) vivid-getdeb games
/etc/apt/sources.list.d/playdeb.list.save:deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) vivid-getdeb games
/etc/apt/sources.list.d/qbittorrent-team-ubuntu-qbittorrent-stable-vivid.list:eb [http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu](http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu) vivid main
/etc/apt/sources.list.d/qbittorrent-team-ubuntu-qbittorrent-stable-vivid.list.save:deb [http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu](http://ppa.launchpad.net/qbittorrent-team/qbittorrent-stable/ubuntu) vivid main
/etc/apt/sources.list.d/ria-repository.list:deb [https://installer.id.ee/media/ubuntu/](https://installer.id.ee/media/ubuntu/) vivid main
/etc/apt/sources.list.d/ria-repository.list.save:deb [https://installer.id.ee/media/ubuntu/](https://installer.id.ee/media/ubuntu/) vivid main
/etc/apt/sources.list.d/ubuntu-sdk-team-ubuntu-ppa-vivid.list:deb [http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu) vivid main
/etc/apt/sources.list.d/ubuntu-sdk-team-ubuntu-ppa-vivid.list.save:deb [http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu) vivid main
/etc/apt/sources.list.d/videolan-ubuntu-stable-daily-vivid.list:deb [http://ppa.launchpad.net/videolan/stable-daily/ubuntu](http://ppa.launchpad.net/videolan/stable-daily/ubuntu) vivid main
/etc/apt/sources.list.d/videolan-ubuntu-stable-daily-vivid.list.save:deb [http://ppa.launchpad.net/videolan/stable-daily/ubuntu](http://ppa.launchpad.net/videolan/stable-daily/ubuntu) vivid main
/etc/apt/sources.list.d/webupd8team-ubuntu-java-vivid.list:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) vivid main
/etc/apt/sources.list.d/webupd8team-ubuntu-java-vivid.list.save:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) vivid main
/etc/apt/sources.list.d/webupd8team-ubuntu-y-ppa-manager-vivid.list:deb [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) vivid main
/etc/apt/sources.list.d/webupd8team-ubuntu-y-ppa-manager-vivid.list.save:deb [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) vivid main
andrew@lab00t:~$

```

---

### Post by matt_symes on 2015-12-25
Hi

```
/etc/apt/sources.list.d/metasploit-framework.list:deb http://downloads.metasploit.com/data...-framework/apt **lucid** main
```

Installing mc should never remove a kernel.

You have a Lucid (10.04) repository on a Vivid (15.10) installation. This may or may not be the cause of your problem but there is obviously a major problem with your package manager.

You only want use repositories for your current version of Ubuntu.

Start off by removing that source and then apt-get update.

Kind regards

---

### Post by andrewmc2 on 2015-12-25
> **matt_symes said:**
> Hi

```
/etc/apt/sources.list.d/metasploit-framework.list:deb http://downloads.metasploit.com/data...-framework/apt **lucid** main
```

Installing mc should never remove a kernel.

You have a Lucid (10.04) repository on a Vivid (15.10) installation. This may or may not be the cause of your problem but there is obviously a major problem with your package manager.

You only want use repositories for your current version of Ubuntu.

Start off by removing that source and then apt-get update.

Kind regards

I removed lucid repos but problem still there.. i even can remove all repos and to leave only basic one, just tell me what to do.

---

### Post by matt_symes on 2015-12-25
Hi

> **andrewmc2 said:**
> I removed lucid repos but problem still there.. i even can remove all repos and to leave only basic one, just tell me what to do.

That'll help in the future.

Here is the contents of the file you are missing.
```

#!/bin/bash

# We're passed the version of the kernel being installed
inst_kern=$1

uname_s=$(uname -s)

_get_kernel_dir() {
    KVER=$1
    case ${uname_s} in
       Linux)          DIR="/lib/modules/$KVER/build" ;;
       GNU/kFreeBSD)   DIR="/usr/src/kfreebsd-headers-$KVER/sys" ;;
    esac
    echo $DIR
}

_check_kernel_dir() {
    DIR=$(_get_kernel_dir $1)
    case ${uname_s} in
       Linux)          test -e $DIR/include ;;
       GNU/kFreeBSD)   test -e $DIR/kern && test -e $DIR/conf/kmod.mk ;;
       *)              return 1 ;;
    esac
    return $?
}

case "${uname_s}" in
    Linux)
        header_pkg="linux-headers-$inst_kern"
        kernel="Linux"
    ;;
    GNU/kFreeBSD)
        header_pkg="kfreebsd-headers-$inst_kern"
        kernel="kFreeBSD"
    ;;
esac

if [ -x /usr/lib/dkms/dkms_autoinstaller ]; then
    exec /usr/lib/dkms/dkms_autoinstaller start $inst_kern > /dev/null
fi

if ! _check_kernel_dir $inst_kern ; then
    echo "dkms: WARNING: $kernel headers are missing, which may explain the above failures." >&2
    echo "      please install the $header_pkg package to fix this." >&2
fi


```

That ^^^ needs to go into the file

```
/etc/kernel/postinst.d/dkms
```

You can use whichever editor you feel most comfortable with; just open it with elevated privileges.

Then type

```
sudo apt-get install -f
```

Post back any errors or on success.

Kind regards

---

