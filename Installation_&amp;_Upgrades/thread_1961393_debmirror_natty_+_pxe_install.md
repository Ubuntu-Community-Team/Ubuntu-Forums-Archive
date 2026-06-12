---
title: "debmirror natty + pxe install"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by grozours on 2012-04-19
Hello everyone,

I'm trying to setup en environment with a local natty mirror for preseed automated installation of natty i386  desktop clients.

First, debmirror synchronize correctly, but does not get all the packages necessary to install correctly from a minimal pxe environment. It seems it synchronizes only the packages for a cdrom installation.

Secondly, looking for a solution, to have only the packages associated to a specific ubuntu release,
the mirror is release discriminant for only the "dists" tree. the "pool" tree is not "natty" specific.

Is there a way to get only the natty packages in the "pool" application tree ?
Since, we will start to deploy a "natty" desktop, i dont wan't to get all the old packages.

I synchronized to pool tree to see how much disk space is uses and found 140Go of data,
removing the source files and more.




My /etc/debmirror.conf :

```

# Default config for debmirror

# The config file is a perl script so take care to follow perl syntax.
# Any setting in /etc/debmirror.conf overrides these defaults and
# ~/.debmirror.conf overrides those again. Take only what you need.
#
# The syntax is the same as on the command line and variable names
# loosely match option names. If you don't recognize something here
# then just stick to the command line.


# Output options
$verbose=0;
$progress=0;
$debug=0;

# Download options
$host="fr.archive.ubuntu.com";
$user="anonymous";
$passwd="anonymous@";
$remoteroot="/ubuntu";
$download_method="http";
@dists="natty,natty-backports,natty-proposed,natty-security,natty-updates";
@sections="main,multiverse,restricted,universe";
@arches="i386";
# @extra_dirs="";
# @ignores="";
# @includes="";
#  Some Games exclusions to some diskspace  on the mirror machine
@excludes="n/nexuiz-data/|o/openarena-data/|w/warsow-data/|a/alien-arena-data/|s/sauerbraten-data|.*dbg.*";
@excludes_deb_section="debug";

# @limit_priority="";
$skippackages=0;
$getcontents=0;
$do_source=0;
$max_batch=0;

# Security/Sanity options
$ignore_release_gpg=1;
$ignore_release=0;
$check_md5sums=0;
$ignore_small_errors=0;

# Cleanup
$cleanup=1;
$post_cleanup=1;

# Locking options
$timeout=300;

# Rsync options
$rsync_batch=200;
$rsync_options="-aIL --partial";

# FTP/HTTP options
$passive=0;
#$proxy="";

# Dry run
$dry_run=0;

# Don't keep pdiff files but use them
$pdiff_mode="use";

# The config file must return true or perl complains.
# Always copy this.
1;

```Here my rsync script, to complete the missing packages needed for pxe install :

```

#!/bin/bash

dir=`dirname $0`
cd $dir

# ubuntu version
version="natty"
sections="main multiverse restricted universe"

# rsync source
source="archive.ubuntu.com/ubuntu"

# destination directory
destination="ubuntu/mirror/archive.ubuntu.com/ubuntu/"

# rsync options
options="-a --progress --ignore-existing"

# includes and excludes files rules
includes="--include-from=includes/include_list"
excludes="--exclude-from=excludes/exclude_list --exclude-from=excludes/exclude_lang"

# lang parameters not excluded
languages="fr\|en"

# remove the lang rsync exclusion file
rm -f excludes/exclude_lang &>/dev/null
rm -f excludes/exclude_tmp &>/dev/null
rm -f excludes/exclude_list &>/dev/null

patternexclusion="excludes/exclude_pattern"
cat $patternexclusion >> excludes/exclude_list


# create lang exclusions from gnome kde etc
lynx -dump http://$source/pool/main/l/ | grep "language-" | grep -v "$languages" | awk -F"http://$source/" '{print $2}' >> excludes/exclude_lang

lynx -dump http://$source/pool/main/ | awk -F"http://$source/" '{print $2}' | grep -v "/?" | sort -u | grep -v "pool/$" >> excludes/exclude_tmp
for ligne in `cat excludes/exclude_tmp`; do echo "$ligne" | awk -F"/" '{print $1"/"$2"/"$3"/*"}'; done >> excludes/exclude_list

# exclude translations from installer
for section in $sections
do
   lynx -dump http://$source/dists/"$version"/$section/i18n/ | grep "Translation-" | grep -v "$languages" | awk -F"http://$source/" '{print $2}'| sort -u >> excludes/exclude_lang
done

# we remove empty lines
sed -i '/^$/d' excludes/exclude_lang

debmirrror $destination
rsync $options  $includes $excludes rsync://$source $destination

```my excludes/exclude_pattern file :
```

indices/***
project/***
ubuntu/***
dists/hardy**
dists/lucid**
dists/maverick**
dists/oneiric**
dists/precise**
dists/**/*amd64*
dists/**/dist-upgrader-all
dists/**/source
dists/**/installer-i386/*2010*
dists/**/installer-i386/*beta*
dists/*proposed**
pool/multiverse/***
pool/restricted/***
pool/universe/***
pool/**/*amd64*
pool/**/*bz2
pool/**/*dbg*
pool/**/*debug*
pool/**/*source*
pool/**/*gz
pool/**/*dsc
pool/**/*xz
pool/**/*lucid*
pool/**/*maverick*
pool/**/*hardy*
pool/**/*2.6.2*
pool/**/*2.6.32*
pool/**/*2.6.35*
pool/**/*3.0.0*
pool/**/*3.2.0*


```my includes/include_list : ( Needed for Ubuntu  pxe boot )
```

pool/main/a/apt-setup/
pool/main/b/base-files/
pool/main/b/base-installer/
pool/main/b/binutils/
pool/main/b/btrfs-tools/
pool/main/c/clock-setup/
pool/main/c/cryptsetup/
pool/main/d/debian-installer-utils/
pool/main/d/debootstrap/
pool/main/d/dmraid/
pool/main/e/e2fsprogs/
pool/main/e/eglibc/
pool/main/e/elilo-installer/
pool/main/f/finish-install/
pool/main/f/fuse/
pool/main/g/grub2/
pool/main/g/grub-installer/
pool/main/h/hw-detect/
pool/main/j/jfsutils/
pool/main/libb/libbsd/
pool/main/libg/libgcrypt11/
pool/main/libg/libgpg-error/
pool/main/libu/libusb/
pool/main/l/lilo-installer/
pool/main/l/linux/
pool/main/l/linux-backports-modules-2.6.38/
pool/main/l/linux-firmware/
pool/main/l/linux-ntfs/
pool/main/l/lvm2/
pool/main/m/mdadm/
pool/main/n/nobootloader/
pool/main/n/ntfs-3g/
pool/main/o/open-iscsi/
pool/main/o/os-prober/
pool/main/p/partconf/
pool/main/p/parted/
pool/main/p/partman-auto/
pool/main/p/partman-auto-crypto/
pool/main/p/partman-auto-loop/
pool/main/p/partman-auto-lvm/
pool/main/p/partman-auto-raid/
pool/main/p/partman-base/
pool/main/p/partman-basicfilesystems/
pool/main/p/partman-basicmethods/
pool/main/p/partman-btrfs/
pool/main/p/partman-crypto/
pool/main/p/partman-efi/
pool/main/p/partman-ext3/
pool/main/p/partman-iscsi/
pool/main/p/partman-jfs/
pool/main/p/partman-lvm/
pool/main/p/partman-md/
pool/main/p/partman-partitioning/
pool/main/p/partman-reiserfs/
pool/main/p/partman-target/
pool/main/p/partman-xfs/
pool/main/p/pcre3/
pool/main/p/pkgsel/
pool/main/p/popt/
pool/main/r/rdate/
pool/main/r/reiserfsprogs/
pool/main/t/tzsetup/
pool/main/u/ubiquity/
pool/main/u/udev/
pool/main/u/usbutils/
pool/main/u/user-setup/
pool/main/u/util-linux/
pool/main/x/xfsprogs/

```Is there a way to keep only natty packages in the "pool" tree  ?


Thanks in advance.

---

### Post by grozours on 2012-04-21
updated the  script :)

---

