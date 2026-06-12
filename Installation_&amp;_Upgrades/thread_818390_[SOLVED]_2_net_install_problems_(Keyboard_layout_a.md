---
title: "[SOLVED] 2 net install problems (Keyboard layout and sources.list)"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by kai4785 on 2008-06-04
I have a little experience with Redhat Systems, and my first stab at Ubuntu is to try and get the automated installer working. I had no problems getting through the PXE and preseed.cfg process, and can do an unattended installation using this tutorial:
[http://www.debuntu.org/how-to-unattended-ubuntu-network-install-preseed-p5](http://www.debuntu.org/how-to-unattended-ubuntu-network-install-preseed-p5)

When my system comes up I have 2 problems.

1) My keyboard layout seems to be off. When I sit at the keyboard, I get little diamonds for anything I type except the numpad, which prints numbers. However, I can use SSH to connect, so I am able to use the system the way I intend to anyway. I appear to be in run level 2:
```
root@ubunut-installer:~# runlevel
N 2

```
The preseed config file is set to en_US for the keyboard, so I'm a little confused.

2) My /etc/apt/sources.list file uses the my own mirror of the CD image I put on my local network instead of a public mirror. I need to change the soruces.list to use a public mirror because these systems will not be on the same network as the local mirror when these servers actually get put to use. I also can't install things like 'elinks' from atp-get, but not sure if that's just because I missed a step somewhere:
```
root@ubunut-installer:~# apt-get install elinks
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package elinks

```

I suppose you'll want the preseed file and my sources.list, not sure what else though. Here they are:

preseed.cfg
```
d-i debian-installer/locale string en_US
d-i console-setup/layoutcode string en_US
d-i netcfg/choose_interface select eth0

# Any hostname and domain names assigned from dhcp take precedence over
# values set here. However, setting the values still prevents the questions
# from being shown, even if values come from dhcp.
d-i netcfg/get_hostname string ubunutu-test
d-i netcfg/get_domain string fiber.net
#d-i netcfg/wireless_wep string

### Mirror settings
# If you select ftp, the mirror/country string does not need to be set.
d-i mirror/country string enter information manually
d-i mirror/protocol string http
d-i mirror/http/hostname string PXE
d-i mirror/http/directory string /linux/ubuntu/releases/8.04/os/
d-i mirror/http/proxy string

# Suite to install.
#d-i mirror/suite string testing

# Suite to use for loading installer components (optional).
#d-i mirror/udeb/suite string testing
d-i mirror/suite string hardy

### Partitioning
# If the system has free space you can choose to only partition that space.
# Note: this must be preseeded with a localized (translated) value.
#d-i partman-auto/init_automatically_partition \
# select Guided - use the largest continuous free space

# Alternatively, you can specify a disk to partition. The device name
# can be given in either devfs or traditional non-devfs format.
# For example, to use the first disk:
#d-i partman-auto/disk string /dev/discs/disc0/disc
d-i partman-auto/disk string /dev/sda

# In addition, you'll need to specify the method to use.
# The presently available methods are: "regular", "lvm" and "crypto"
d-i partman-auto/method string lvm

# If one of the disks that are going to be automatically partitioned
# contains an old LVM configuration, the user will normally receive a
# warning. This can be preseeded away...
d-i partman-auto/purge_lvm_from_device boolean true

# And the same goes for the confirmation to write the lvm partitions.
d-i partman-lvm/confirm boolean true

# You can choose from any of the predefined partitioning recipes.
# Note: this must be preseeded with a localized (translated) value.
d-i partman-auto/choose_recipe \
select Separate /home, /usr, /var, and /tmp partitions

# This makes partman automatically partition without confirmation.
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition \
select Finish partitioning and write changes to disk
d-i partman/confirm boolean true

### Clock and time zone setup
# Controls whether or not the hardware clock is set to UTC.
d-i clock-setup/utc boolean true

# You may set this to any valid setting for $TZ; see the contents of
# /usr/share/zoneinfo/ for valid values.
d-i time/zone string America/Denver

### Apt setup
# You can choose to install non-free and contrib software.
d-i apt-setup/multiverse boolean true
d-i apt-setup/universe boolean true

# To create a normal user account.
d-i passwd/user-fullname string Kai Meyer
d-i passwd/username string kai

# Normal user's password, either in clear text
#d-i passwd/user-password password insecure
#d-i passwd/user-password-again password insecure
# or encrypted using an MD5 hash.
d-i passwd/user-password-crypted password $1$kqoeOB9Z$LROkVUK36wsN22pYiYvkv.

# This is fairly safe to set, it makes grub install automatically to the MBR
# if no other operating system is detected on the machine.
d-i grub-installer/only_debian boolean true

# This one makes grub-installer install to the MBR if it also finds some other
# OS, which is less safe as it might not be able to boot that other OS.
d-i grub-installer/with_other_os boolean true

### Package selection
tasksel tasksel/first multiselect standard, lamp-server

# Individual additional packages to install
d-i pkgsel/include string openssh-server

### Finishing up the first stage install

# Avoid that last message about the install being complete.
d-i finish-install/reboot_in_progress note
#xserver-xorg xserver-xorg/autodetect_monitor boolean true
#xserver-xorg xserver-xorg/config/monitor/selection-method \
#select medium
#xserver-xorg xserver-xorg/config/monitor/mode-list \
#select 1024x768 @ 60 Hz 

```

And my eventual /etc/sources.list:
```
# deb http://PXE/linux/ubuntu/releases/8.04/os/ hardy main restricted
# deb http://PXE/linux/ubuntu/releases/8.04/os/ hardy-updates main restricted
# deb http://PXE/ubuntu hardy-security main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://PXE/linux/ubuntu/releases/8.04/os/ hardy main restricted
deb-src http://PXE/linux/ubuntu/releases/8.04/os/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://PXE/linux/ubuntu/releases/8.04/os/ hardy-updates main restricted
deb-src http://PXE/linux/ubuntu/releases/8.04/os/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://PXE/linux/ubuntu/releases/8.04/os/ hardy universe
deb-src http://PXE/linux/ubuntu/releases/8.04/os/ hardy universe
deb http://PXE/linux/ubuntu/releases/8.04/os/ hardy-updates universe
deb-src http://PXE/linux/ubuntu/releases/8.04/os/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://PXE/linux/ubuntu/releases/8.04/os/ hardy multiverse
deb-src http://PXE/linux/ubuntu/releases/8.04/os/ hardy multiverse
deb http://PXE/linux/ubuntu/releases/8.04/os/ hardy-updates multiverse
deb-src http://PXE/linux/ubuntu/releases/8.04/os/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://PXE/linux/ubuntu/releases/8.04/os/ hardy-backports main restricted universe multiverse
# deb-src http://PXE/linux/ubuntu/releases/8.04/os/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

I'd also like to know if the preseed file has a post-install script section. Fixing the sources.list should be a matter of a one liner for perl but not sure how to do it.

Thanks!
-Kai Meyer

---

### Post by kai4785 on 2008-06-05
So I found the fix for both of my problems:
[http://www.linuxquestions.org/questions/linux-hardware-18/changing-the-keyboard-layout-from-uk-to-us-debian-285750/](http://www.linuxquestions.org/questions/linux-hardware-18/changing-the-keyboard-layout-from-uk-to-us-debian-285750/)
This fixes my keyboard problem:
```
apt-get install console-common
install-keymap us
```

And here's a post with a working copy of a hardy sources.list:
[http://ubuntuforums.org/showpost.php?p=4724207&postcount=4](http://ubuntuforums.org/showpost.php?p=4724207&postcount=4)

Now, the trick is to automate the fix for both of these problems in a preseed file. Any ideas?

---

### Post by kai4785 on 2008-06-09
I've been able to solve both problems using the kickseed project. 
[https://help.ubuntu.com/8.04/installation-guide/i386/automatic-install.html](https://help.ubuntu.com/8.04/installation-guide/i386/automatic-install.html)

This is great, since I'm a redhat guy, and have a little experience with kick start scripts. I hope this helps the next guy that comes along :)

---

### Post by blafrisch on 2008-06-17
I actually ran across the same exact problem, but I eventually resolved it with just the preseed file.  I just bulked up the locale information and that seemed to solve the problem.  These are just snippets from my preseed file for the locale and keyboard setup.

Here is what worked with Gutsy:
```
#locale
d-i debian-installer/locale string en_US

# keyboard setup
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us
```

Here is what worked with Hardy:
```
# locale
d-i debconf/language string en
d-i debian-installer/language string en
d-i debian-installer/country string US
d-i debian-installer/locale string en_US.UTF-8
d-i debian-installer/fallbacklocale string en_US.UTF-8
d-i debian-installer/consoledisplay string kbd=lat0-sun16(utf8)

# keyboard setup
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us
```

I know you already solved your problem, but I think this would help even more to those of us who aren't very knowledgeable of Red Hat Linux.

---

