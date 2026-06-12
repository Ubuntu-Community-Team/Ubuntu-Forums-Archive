---
title: "How to modify preseed information in a ubuntu iso image"
date: 2016-11-16
forum: Installation &amp; Upgrades
---

### Post by captainquirk2 on 2016-11-16
Hi there,

I'm trying to solve a specific problem summed up [here]("https://ubuntuforums.org/showthread.php?t=2342872"). I created a new thread because I felt the title of the first one was misleading.

I could, thanks to some kindly advices : 


[LIST]
[*]**unpack** the iso file programmatically
[*]**modify its content (**I have specifically overwritten the file **preseed/ubuntu.seed **by an adapting an example I found [here]("https://help.ubuntu.com/lts/installation-guide/example-preseed.txt"))
[*]**repack** it as a modified iso file.
[/LIST]

This is the content of the **final preseed file**

```
[COLOR=#000000][FONT=&amp]#### Contents of the preconfiguration file (for xenial)[/FONT][/COLOR]### Localization
# Preseeding only locale sets language, country and locale.
d-i debian-installer/locale string en_US

# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i keyboard-configuration/xkb-keymap select fr

# netcfg will choose an interface that has link if possible. This makes it
# skip displaying a list if there is more than one interface.
d-i netcfg/choose_interface select auto

# Any hostname and domain names assigned from dhcp take precedence over
# values set here. However, setting the values still prevents the questions
# from being shown, even if values come from dhcp.
d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain

# Disable that annoying WEP key dialog.
d-i netcfg/wireless_wep string

### Mirror settings
# If you select ftp, the mirror/country string does not need to be set.
#d-i mirror/protocol string ftp
d-i mirror/country string manual
d-i mirror/http/hostname string archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string

# To create a normal user account.
d-i passwd/user-fullname string CaptainQuirk
d-i passwd/username string captainquirk
# Normal user's password, either in clear text
d-i passwd/user-password password azerty
d-i passwd/user-password-again password azerty

# The installer will warn about weak passwords. If you are sure you know
# what you're doing and want to override it, uncomment this.
d-i user-setup/allow-password-weak boolean true

# Set to true if you want to encrypt the first user's home directory.
d-i user-setup/encrypt-home boolean false

### Clock and time zone setup
# Controls whether or not the hardware clock is set to UTC.
d-i clock-setup/utc boolean true

# You may set this to any valid setting for $TZ; see the contents of
# /usr/share/zoneinfo/ for valid values.
d-i time/zone string Europe/Paris

# Controls whether to use NTP to set the clock during the install
d-i clock-setup/ntp boolean true

### Partitioning
## Partitioning example
# If the system has free space you can choose to only partition that space.
# This is only honoured if partman-auto/method (below) is not set.
# Alternatives: custom, some_device, some_device_crypto, some_device_lvm.
d-i partman-auto/init_automatically_partition select biggest_free

# Alternatively, you may specify a disk to partition. If the system has only
# one disk the installer will default to using that, but otherwise the device
# name must be given in traditional, non-devfs format (so e.g. /dev/sda
# and not e.g. /dev/discs/disc0/disc).
# In addition, you'll need to specify the method to use.
# The presently available methods are:
# - regular: use the usual partition types for your architecture
# - lvm:     use LVM to partition the disk
# - crypto:  use LVM within an encrypted partition
d-i partman-auto/method string lvm

# If one of the disks that are going to be automatically partitioned
# contains an old LVM configuration, the user will normally receive a
# warning. This can be preseeded away...
d-i partman-lvm/device_remove_lvm boolean true
# The same applies to pre-existing software RAID array:
d-i partman-md/device_remove_md boolean true
# And the same goes for the confirmation to write the lvm partitions.
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true

# You can choose one of the three predefined partitioning recipes:
# - atomic: all files in one partition
# - home:   separate /home partition
# - multi:  separate /home, /var, and /tmp partitions
d-i partman-auto/choose_recipe select atomic


# This makes partman automatically partition without confirmation.
d-i partman-md/confirm boolean true
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

### Package selection
tasksel tasksel/first multiselect ubuntu-desktop

# Individual additional packages to install
d-i pkgsel/include curl git chef-solo rvm build-essential
# Whether to upgrade packages after debootstrap.
# Allowed values: none, safe-upgrade, full-upgrade
d-i pkgsel/upgrade select full-upgrade

# Language pack selection
d-i pkgsel/language-packs multiselect de, en, fr

# Policy for applying updates. May be "none" (no automatic updates),
# "unattended-upgrades" (install security updates automatically), or
# "landscape" (manage system with Landscape).
d-i pkgsel/update-policy select unattended-upgrades

# This is fairly safe to set, it makes grub install automatically to the MBR
# if no other operating system is detected on the machine.
d-i grub-installer/only_debian boolean true

# This one makes grub-installer install to the MBR if it also finds some other
# OS, which is less safe as it might not be able to boot that other OS.
d-i grub-installer/with_other_os boolean true

# Avoid that last message about the install being complete.
d-i finish-install/reboot_in_progress note

# This will prevent the installer from ejecting the CD during the reboot,
# which is useful in some situations.
d-i cdrom-detect/eject boolean false

#### Advanced options
### Running custom commands during the installation
# d-i preseeding is inherently not secure. Nothing in the installer checks
# for attempts at buffer overflows or other exploits of the values of a
# preconfiguration file like this one. Only use preconfiguration files from
# trusted locations! To drive that home, and because it's generally useful,
# here's a way to run any shell command you'd like inside the installer,
# automatically.

# This command is run just before the install finishes, but when there is
# still a usable /target directory. You can chroot to /target and use it
# directly, or use the apt-install and in-target commands to easily install
# packages and run commands in the target system. [COLOR=#000000][FONT=&amp]d-i preseed/late_command string curl -sSL https://get.rvm.io | bash -s stable --ruby[/FONT][/COLOR]
```

[INDENT]*There is obviously something wrong either with **the preseed file itself** or its **location** in the iso image because launching qemu with this modified iso results in the **good old install wizard** being displayed.*[/INDENT]

Thanks in advance !

---

### Post by TheFu on 2016-11-17
I can't help with a solution. Never used this method. But ... some document links for the people interested (like me) in learning more:
[https://help.ubuntu.com/lts/installation-guide/amd64/apb.html](https://help.ubuntu.com/lts/installation-guide/amd64/apb.html) and [http://hands.com/d-i/](http://hands.com/d-i/)

I'd always thought Cobbler was the way to do this stuff, but that tool serves a different purpose than this.  Once an OS is installed, I use ansible to configure everything. The issue with this is partitioning/encryption will already be less-than-ideal. It is too late in the process.

Anyways, interesting problem.

---

### Post by captainquirk2 on 2016-11-17
Hi ! Thanks for your answer. I was thinking about rewriting my chef cookbooks into ansible playbooks for a time.

But I would like to have a build process ready from the start !

---

