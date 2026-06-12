---
title: "Help needed with PXE network install of 7.10 Alternate CD"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by Slim Backwater on 2008-04-22
I've successfully used PXE to install other Distros (CentOS, RedHat, System Rescue CD), but Ubuntu 7.10 is giving me some trouble.

What I think is happening is that the installer is looking out to the internet for updates and then complaining when my 7.10 Alternate CD doesn't have them.

I'd like to do an installation with just what's on the CD, as if I were installing from the CD, only here the CD is on the network.  Or somehow tell it to not look out to the Internet for Updates.

My pxelinux.cfg/default looks (mostly - numerous entries removed) like this:

```

PROMPT 0
TIMEOUT 300

LABEL gutsy-desktop
    kernel ubuntu-installer/i386/linux
    append initrd=ubuntu-installer/i386/initrd.gz locale=en_CA console-setup/layoutcode=us url=http://waiter/Ubuntu-7.10-i386-desktop-preseed.cfg --


```

My Ubuntu-7.10-i386-desktop-preseed.cfg looks like this:
```

# Gutsy Desktop
# Set apt-mirror
d-i     mirror/suite    string gutsy
d-i     mirror/country  string enter information manually
d-i     mirror/http/hostname    string waiter
d-i     mirror/http/directory   string /ubuntu-7.10-alternate-i386/ubuntu
d-i     apt-setup/universe      boolean false

# Setup clock and timezone
clock-setup     clock-setup/utc boolean true
d-i     time/zone       string Canada/Eastern
d-i     time/zone       select Canada/Eastern
#d-i    pkgsel/include string openssh-server

#d-i    base-installer/kernel/override-image string linux-server

popularity-contest popularity-contest/participate       boolean true

d-i     finish-install/reboot_in_progress       note

tasksel tasksel/first   string ubuntu-desktop

```

On my machine "waiter" I have mounted the 7.10 Alternate CD into the ubuntu-7.10-alternate-i386 directory.

The installer loads and runs fine, right up until it tries to download:
 
e2fsprogs-udeb_1.40.2-1ubuntu1.1_i386.udeb

Which, of course, doesn't exist on the 7.10 Alternate CD as this is a package that was updated since 7.10 was released.

One post says to disconnect Internet access during the installation, which isn't really practical, (and I understand why it may work) but it doesn't work, the installer fails with a "Bad archive mirror".

Is it possible to do a Network Install of a CD Image?

Thanks.

---

### Post by dstew on 2008-04-23
You can do this. Look at the [_Installation/LocalNet_]("https://help.ubuntu.com/community/Installation/LocalNet") community document. Down the page are instructions for booting a locally-stored Live CD image, with an example pxelinux.cfg/default file.

---

