---
title: "DHCP/PXE install [Quantal]"
date: 2013-03-28
forum: Installation &amp; Upgrades
---

### Post by eckertd on 2013-03-28
Having a little issue here getting Quantal installed from a DHCP/PXE setup that we currently use to deploy RHEL & CentOS.

I pulled the kernel and initrd files from here

```
http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-amd64/current/images/cdrom/initrd.gz
http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-amd64/current/images/cdrom/vmlinuz
```

Stored locally on the DHCP/PXE server

```
/tftpboot/kernels/Ubuntu/amd64/Quantal/initrd.gz
/tftpboot/kernels/Ubuntu/amd64/Quantal/vmlinuz
```

Using this pxelinux.0 file

```
# strings pxelinux.0 | grep PXELINUX
PXELINUX 4.05 20120702
```

Entry in isolinux.cfg:

```
LABEL ubuntu-quantal
  KERNEL kernels/Ubuntu/amd64/Quantal/vmlinuz
  APPEND initrd=kernels/Ubuntu/amd64/Quantal/initrd.gz
  APPEND preseed/url=http://aaa.bbb.ccc.ddd/ubuntu/preseed/preseed-quantal.cfg
  APPEND preseed/url/cehcksum=03bb7756b55fea992b1219dc2e6e99e5
```

The server is PXE-booted, and our splash screen & boot prompt are displayed, at which point I enter

```
boot: ubuntu-quantal
```

It starts off ok, but then I get a VFS error and kernel panic about not being able to open root device (se attached image).  At this point, it hasn't even attempted to pull the preseed file from the specified URL (verified w/tcpdump).  What am I missing?  It's almost as if it's trying to do a diskless boot rather than an install.

---

### Post by eckertd on 2013-03-28
Of course the boot messages scroll too quick to capture on an iLO virtual console.  I'm pretty sure it has something to do with the CCISS driver (or lack thereof).  The only "valid" partition it reports is the CD/DVD device (sr0).

I've even tried the kernel/initrd files from here, which according to the manifest, are those to be used for PXE installs

> [http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/ubuntu-installer/amd64/](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/ubuntu-installer/amd64/)

Same result.

---

### Post by eckertd on 2013-03-29
I'm making some progress.  Consolidating the multiple "APPEND" lines into 1 seems to be helping.  At least I'm getting further in the install process.  It looks like it's grabbing the preseed file, but it having some issue retrieving a file(s) from my local distro mirror.

---

### Post by eckertd on 2013-03-29
Slowly working my way through this... my isolinux.cfg entry now looks like

> LABEL ubuntu-quantal
  KERNEL kernels/Ubuntu/amd64/Quantal/linux
  APPEND initrd=kernels/Ubuntu/amd64/Quantal/initrd.gz locale=en_US -- interface=eth2 url=http://172.26.23.131/preseed/preseed-quantal.cfg keyboard-configuration/layoutcode=en_US

It's pulling in the preseed file ok.  According to the apache2 access log, it's trying to retrieve files in the path

> /ubuntu/dists/quantal/main/debian-installer/binary-amd64/

However, the local mirror  I have set up doesn't have the "debian-installer" subdir under "main".  Here is my /etc/apt-mirror.list:

> ############# config ##################
#
set base_path    /apt-mirror
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     20
set _tilde 0
#
############# end config ##############

#
# Mirror lists for Ubuntu 12.10 - Quantal Quetzal
#

deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted universe multiverse
deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security main restricted universe multiverse
deb-amd64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted universe multiverse
deb-i386 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted universe multiverse
deb-i386 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security main restricted universe multiverse
deb-i386 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted universe multiverse
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-proposed main restricted universe multiverse
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-backports main restricted universe multiverse

#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-proposed main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-backports main restricted universe multiverse

clean [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

Wondering if there's something to override this in the preseed config file...

---

