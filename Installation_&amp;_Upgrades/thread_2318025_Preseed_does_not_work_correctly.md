---
title: "Preseed does not work correctly"
date: 2016-03-22
forum: Installation &amp; Upgrades
---

### Post by horizn on 2016-03-22
Here is my preseed file for Ubuntu 14.04 LTS. Despite I've defined answers or canceled questions, for some reasons installer still asks for:
language, keyboard layout, hostname, user creation.

```

# Preseeding only locale sets language, country and locale.
d-i debian-installer/locale string en_GB.UTF-8

# The values can also be preseeded individually for greater flexibility.
d-i debian-installer/language string en
d-i debian-installer/country string GB

# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i debian-installer/keymap select uk
d-i keyboard-configuration/xkb-keymap select uk
d-i keymap select uk

# netcfg will choose an interface that has link if possible. This makes it
# skip displaying a list if there is more than one interface.
d-i netcfg/choose_interface select eth0

# If you have a slow dhcp server and the installer times out waiting for
# it, this might be useful.
d-i netcfg/dhcp_timeout string 20

# If you prefer to configure the network manually, change this to true
# and add static network configuration below.
d-i netcfg/disable_autoconfig boolean false

# Any hostname and domain names assigned from dhcp take precedence over
# values set here. However, setting the values still prevents the questions
# from being shown, even if values come from dhcp.
d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain

# Added multiarch support
d-i apt-setup/multiarch string i386

# Install kernel headers
d-i base-installer/kernel/headers boolean true

# If non-free firmware is needed for the network or other hardware, you can
# configure the installer to always try to load it, without prompting. Or
# change to false to disable asking.
d-i hw-detect/load_firmware boolean true

# If you select ftp, the mirror/country string does not need to be set.
#d-i mirror/protocol string ftp
d-i mirror/country string manual
d-i mirror/http/hostname string ubuntu.local.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string

# Alternatively: by default, the installer uses CC.archive.ubuntu.com where
# CC is the ISO-3166-2 code for the selected country. You can preseed this
# so that it does so without asking.
d-i mirror/http/mirror select uk.archive.ubuntu.com

# Controls whether or not the hardware clock is set to UTC.
d-i clock-setup/utc boolean true

# You may set this to any valid setting for $TZ; see the contents of
# /usr/share/zoneinfo/ for valid values.
d-i time/zone string Europe/London

# Controls whether to use NTP to set the clock during the install
d-i clock-setup/ntp boolean true
# NTP server to use. The default is almost always fine here.
d-i clock-setup/ntp-server string time.local.com

########################################################
# Automatic partitioning with single root partition
########################################################

d-i partman-auto/disk                   string /dev/sda
d-i partman-auto/method                 string regular

d-i partman-auto/purge_lvm_from_device  boolean true
d-i partman-md/device_remove_md         boolean true
d-i partman-lvm/device_remove_lvm       boolean true
d-i partman-auto/alignment              string optimal
#d-i mdadm/boot_degraded                 boolean true
d-i partman-auto/choose_recipe          select atomic

d-i partman-auto/text/atomic_scheme ::  \
        500000 1000 -1 ext4          \
        $primary{ }                     \
        $bootable{ }                    \
        method{ format }                \
        format{ }                       \
        use_filesystem{ }               \
        filesystem{ ext4 }              \
        mountpoint{ / }                 \
        .
        1024 1000 6144 linux-swap       \
        $logical{ }                     \
        method{ swap }                  \
        format{ }                       \
        .
d-i partman-partitioning/confirm_write_new_label     boolean true
d-i partman/choose_partition            select  finish
d-i partman/confirm                     boolean true
d-i partman/confirm_nooverwrite         boolean true

# Root password, either in MD5
d-i passwd/root-password-crypted password 123
d-i passwd/root-password-crypted password 123

# Skip creation of a normal user account.
d-i passwd/make-user boolean false

# Set to true if you want to encrypt the first user's home directory.
d-i user-setup/encrypt-home boolean false

# Policy for applying updates. May be "none" (no automatic updates),
# "unattended-upgrades" (install security updates automatically), or
# "landscape" (manage system with Landscape).
d-i pkgsel/update-policy select unattended-upgrades


# By default, the system's locate database will be updated after the
# installer has finished installing most packages. This may take a while, so
# if you don't want it, you can set this to "false" to turn it off.
d-i pkgsel/updatedb boolean true

# This is fairly safe to set, it makes grub install automatically to the MBR
# if no other operating system is detected on the machine.
d-i grub-installer/only_debian boolean true

# This one makes grub-installer install to the MBR if it also finds some other
# OS, which is less safe as it might not be able to boot that other OS.
d-i grub-installer/with_other_os boolean true
d-i grub-installer/bootdev string
d-i grub-installer/choose_bootdev   select /dev/sda

# snippet 'ubuntu_package'
# You can choose to install restricted and universe software, or to install
# software from the backports repository.
d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/multiverse boolean true
d-i apt-setup/partner boolean true
d-i apt-setup/extras boolean true
d-i apt-setup/non-free boolean true
d-i apt-setup/backports boolean false

# By default the installer requires that repositories be authenticated
# using a known gpg key. This setting can be used to disable that
# authentication. Warning: Insecure, not recommended.
d-i debian-installer/allow_unauthenticated boolean true

# Accept Microsoft Fonts EULA
ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula boolean true

# don't set adobe reader as default
acroread-common acroread-common/default-viewer boolean false

# Setuid bit for davfs2, allow davfs mounts by users.
davfs2 davfs2/suid_file boolean true

tasksel tasksel/first multiselect standard, ubuntu-desktop
#tasksel tasksel/first multiselect lamp-server, print-server
#tasksel tasksel/first multiselect kubuntu-desktop

# Individual additional packages to install
d-i pkgsel/include string openssh-server \
  wbritish firefox-locale-en thunderbird-locale-en libreoffice \
  libreoffice-l10n-en libreoffice-help-en myspell-en-gb \
  acroread apt-file autofs build-essential byobu chromium-browser \
  cifs-utils console-common davfs2 eclipse eclipse-egit enigmail \
  filezilla gedit-plugins git gitg  gnupg  gnupg-agent  gpm \
  htop inkscape libcrack2 libreoffice-presenter-console \
  lightning-extension meld nmap regexxer rdesktop retext ruby \
  shutter skype synaptic terminator traceroute vim \
  ubuntu-restricted-extras vim virt-manager vlc wine \
  wireshark mtr hddtemp sysstat iptraf mc scite xrdp \
  apache2 isc-dhcp-server tcpdump cvs libc6 nscd subversion \
  ldap-utils fetchmail tree antiword smbnetfs smbclient \
  dialog alien rwho rwhod openbsd-inetd tftpd-hpa minicom \
  lrzsz vlc xpdf wireshark inkscape kscope libpam-ldap gitk \
  dvbsnoop libnss-ldap ethtool make nfs-kernel-server cups \
  nfs-common nslcd nss-updatedb ntp ntpdate resolvconf openvpn \
  libnss-db smartmontools ca-certificates hdparm gcc-multilib \
  iotop exim4 exim4-base exim4-config exim4-daemon-light

# Whether to upgrade packages after debootstrap.
# Allowed values: none, safe-upgrade, full-upgrade
d-i pkgsel/upgrade select full-upgrade

# Change shell to /bin/bash
d-i preseed/late_command string apt-install bash; in-target chsh -s /bin/bash

# Some versions of the installer can report back on what software you have
# installed, and what software you use. The default is not to report back,
# but sending reports helps the project determine what software is most
# popular and include it on CDs.
popularity-contest popularity-contest/participate boolean false

# By default, the system's locate database will be updated after the
# installer has finished installing most packages. This may take a while, so
# if you don't want it, you can set this to "false" to turn it off.
d-i pkgsel/updatedb boolean true

# During installations from serial console, the regular virtual consoles
# (VT1-VT6) are normally disabled in /etc/inittab. Uncomment the next
# line to prevent this.
#d-i finish-install/keep-consoles boolean true

# Avoid that last message about the install being complete.
d-i finish-install/reboot_in_progress note

# This will prevent the installer from ejecting the CD during the reboot,
# which is useful in some situations.
d-i cdrom-detect/eject boolean true

# This is how to make the installer shutdown when finished, but not
# reboot into the installed system.
#d-i debian-installer/exit/halt boolean true
# This will power off the machine instead of just halting it.
#d-i debian-installer/exit/poweroff boolean true

# Monitor autodetection is recommended.
xserver-xorg xserver-xorg/autodetect_monitor boolean true
# Uncomment if you have an LCD display.
#xserver-xorg xserver-xorg/config/monitor/lcd boolean true
# X has three configuration paths for the monitor. Here's how to preseed
# the "medium" path, which is always available. The "simple" path may not
# be available, and the "advanced" path asks too many questions.
xserver-xorg xserver-xorg/config/monitor/selection-method \
       select medium
xserver-xorg xserver-xorg/config/monitor/mode-list \
       select 1024x768 @ 60 Hz

# No boot splash screen.
#d-i debian-installer/splash boolean false

# Install the debconf oem-config frontend (if in OEM mode).
#d-i oem-config-udeb/frontend string debconf
# Add the network and tasks oem-config steps by default.
#oem-config oem-config/steps multiselect language, keyboard, user, network, tasks


```

---

### Post by histamineblkr on 2016-08-09
Hello horizon,

I experienced the same thing with 16.04 LTS when I was trying to preseed and make a completely unattended install for Ubuntu Desktop.

What I found was that I had to pass in some of the questions as boot parameters. This means reimaging the .iso. Here is the exact line I used in the[COLOR=#000000] isolinux/isolinux.cfg[/COLOR]:
```

default live-install
label live-install
  menu label ^Install Ubuntu
  kernel /casper/vmlinuz.efi
  append  file=/cdrom/ks.preseed auto=true priority=critical debian-installer/locale=en_US keyboard-configuration/layoutcode=us ubiquity/reboot=true languagechooser/language-name=English countrychooser/shortlist=US localechooser/supported-locales=en_US.UTF-8 boot=casper automatic-ubiquity initrd=/casper/initrd.lz quiet splash noprompt noshell ---

```

Note all the parameters after the "append file=/cdrom/ks.preseed", these parameters combined with my preseed file are what gave me the final unattended install.

I have documented my process in a how-to style google document which can be found [here]("https://docs.google.com/document/d/1_4fDkd9TXQ0nUIL5Q-5W61TKrVpyS32x34GksL1uR8Q/edit?usp=sharing"). This should help you through the entire process and should be very similar for 14.04 LTS.

Let me know if it works for you.

---

### Post by phiphi.g on 2016-08-24
**remove console-common** from the package selection section! This package conflicts with plymouth, so it will remove ubuntu-desktop and cryptsetup etc. 

[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1528861](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/1528861)

---

