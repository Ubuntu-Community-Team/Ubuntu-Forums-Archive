---
title: "Blank screen after installation from preseed."
date: 2017-01-12
forum: Installation &amp; Upgrades
---

### Post by horizn on 2017-01-12
Hi,
I am trying to install 16.04-LTS (desktop) from preseed, unfortunately after installation all I've got is a blank screen. I am able to login using SSH. I've tried to add nomodeset, but it won't help. The same preseed for 14.04-LTS works fine.
Maybe someone can see something wrong in my preseed for 16.04?

```

# Preseeding only locale sets language, country and locale.
d-i debian-installer/locale string en_GB.UTF-8

# The values can also be preseeded individually for greater flexibility.
d-i debian-installer/language string en
d-i debian-installer/country string GB

# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode        string uk
d-i console-setup/variantcode       string 
d-i debian-installer/keymap select uk
d-i keyboard-configuration/xkb-keymap select uk
d-i keymap select uk
d-i console-data/keymap/policy      select  Don't touch keymap

# netcfg will choose an interface that has link if possible. This makes it
# skip displaying a list if there is more than one interface.
d-i netcfg/choose_interface select auto

# If you have a slow dhcp server and the installer times out waiting for
# it, this might be useful.
d-i netcfg/dhcp_timeout string 20

# If you prefer to configure the network manually, change this to true
# and add static network configuration below.
d-i netcfg/disable_autoconfig boolean false

### Added multiarch support for local purposes only.
d-i apt-setup/multiarch string i386

# Install Kernel headers
d-i base-installer/kernel/headers boolean true

# If non-free firmware is needed for the network or other hardware, you can
# configure the installer to always try to load it, without prompting. Or
# change to false to disable asking.
d-i hw-detect/load_firmware boolean true

# If you select ftp, the mirror/country string does not need to be set.
#d-i mirror/protocol string ftp
d-i mirror/country string manual
d-i mirror/http/hostname string ubuntu.domain.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string

# Alternatively: by default, the installer uses CC.archive.ubuntu.com where
# CC is the ISO-3166-2 code for the selected country. You can preseed this
# so that it does so without asking.
d-i mirror/http/mirror select uk.archive.ubuntu.com

# Suite to install.
d-i mirror/suite string xenial

# Controls whether or not the hardware clock is set to UTC.
d-i clock-setup/utc boolean true

# You may set this to any valid setting for $TZ; see the contents of
# /usr/share/zoneinfo/ for valid values.
d-i time/zone string Europe/London

########################################################
# Automatic partitioning with single root partition

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

# Allow root login
d-i passwd/root-login boolean true

# Root password, encrypted
d-i passwd/root-password-crypted password 123123
d-i passwd/root-password-crypted password 123123

# Skip creation of a normal user account.
d-i passwd/make-user boolean false

# Set to true if you want to encrypt the first user's home directory.
d-i user-setup/encrypt-home boolean false

# Policy for applying updates. May be "none" (no automatic updates),
# "unattended-upgrades" (install security updates automatically), or
# "landscape" (manage system with Landscape).
d-i pkgsel/update-policy select unattended-upgrades

# Some versions of the installer can report back on what software you have
# installed, and what software you use. The default is not to report back,
# but sending reports helps the project determine what software is most
# popular and include it on CDs.
popularity-contest popularity-contest/participate boolean false

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

# Alternatively, if you want to install to a location other than the mbr,
# uncomment and edit these lines:
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

# Add custom repository
d-i apt-setup/local0/repository string \
        http://debian2.domain.com/repos/apt/debian xenial main
d-i apt-setup/local0/key string http://debian2.domain.com/repos/apt/mirror.gpg.key

# By default the installer requires that repositories be authenticated
# using a known gpg key. This setting can be used to disable that
# authentication. Warning: Insecure, not recommended.
d-i debian-installer/allow_unauthenticated boolean true

# Accept Microsoft Fonts EULA
ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula boolean true

# Setuid bit for davfs2, allow davfs mounts by users.
davfs2 davfs2/suid_file boolean true

tasksel tasksel/first multiselect standard, ubuntu-desktop

# Individual additional packages to install

d-i pkgsel/include string openssh-server \
   wbritish firefox-locale-en thunderbird-locale-en libreoffice \
   myspell-en-gb apt-file autofs build-essential byobu \
   cifs-utils console-common davfs2 eclipse eclipse-egit enigmail \
   filezilla gedit-plugins git gitg  gnupg  gnupg-agent  gpm \
   htop inkscape libcrack2 \
   meld nmap regexxer rdesktop retext ruby \
   shutter skype synaptic terminator traceroute vim \
   ubuntu-restricted-extras vim virt-manager vlc wine \
   wireshark mtr hddtemp sysstat iptraf mc scite xrdp \
   apache2 isc-dhcp-server tcpdump cvs libc6 subversion \
   fetchmail tree antiword smbnetfs smbclient \
   dialog alien rwho rwhod openbsd-inetd tftpd-hpa minicom \
   lrzsz vlc xpdf wireshark inkscape kscope gitk \
   dvbsnoop ethtool make nfs-kernel-server cups \
   nfs-common ntp ntpdate resolvconf openvpn \
   smartmontools ca-certificates hdparm gcc-multilib \
   iotop exim4 exim4-base exim4-config exim4-daemon-light \
   chromium-browser ca-certificates debconf-utils adduser \
   gawk rsync rpm sudo-ldap ldap-utils nscd  \
   libnss-ldap libpam-ldap krb5-user krb5-config \
   libpam-ccreds libnss-db nss-updatedb libcap2-bin \
   libpam-script openssh-blacklist 

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

# Avoid that last message about the install being complete.
d-i finish-install/reboot_in_progress note

# This will prevent the installer from ejecting the CD during the reboot,
# which is useful in some situations.
d-i cdrom-detect/eject boolean true

# Monitor autodetection is recommended.
xserver-xorg xserver-xorg/autodetect_monitor boolean true
# Uncomment if you have an LCD display.
#xserver-xorg xserver-xorg/config/monitor/lcd boolean true
# X has three configuration paths for the monitor. Here's how to preseed
# the "medium" path, which is always available. The "simple" path may not
# be available, and the "advanced" path asks too many questions.
##xserver-xorg xserver-xorg/config/monitor/selection-method \
##       select medium
##xserver-xorg xserver-xorg/config/monitor/mode-list \
##       select 1024x768 @ 60 Hz

# No boot splash screen.
#d-i debian-installer/splash boolean false

##################
# Wireshark Non-root users can capture packets
##################
wireshark-common        wireshark-common/install-setuid boolean true

##################
# LDAP setup for Xenial 16.04 LTS (Xenial)
##################

ldap-auth-config    ldap-auth-config/binddn    string    cn=LDAPsearch,cn=Users,dc=domain,dc=com
ldap-auth-config    ldap-auth-config/bindpw    password    Password
ldap-auth-config    ldap-auth-config/dblogin    boolean    false
ldap-auth-config    ldap-auth-config/dbrootlogin    boolean    true
ldap-auth-config    ldap-auth-config/ldapns/base-dn    string    cn=Users,dc=domainm,dc=com
ldap-auth-config    ldap-auth-config/ldapns/ldap-server    string    ldap://1.2.3.4/
ldap-auth-config    ldap-auth-config/ldapns/ldap_version    select    3
ldap-auth-config    ldap-auth-config/move-to-debconf    boolean    true
ldap-auth-config    ldap-auth-config/override    boolean    true
ldap-auth-config    ldap-auth-config/pam_password    select    crypt
ldap-auth-config    ldap-auth-config/rootbinddn    string    cn=LDAPsearch,cn=Users,dc=domain,dc=com
ldap-auth-config    ldap-auth-config/rootbindpw    password     Password
libnss-ldap    libnss-ldap/binddn    string    cn=LDAPsearch,cn=Users,dc=domain,dc=com
libnss-ldap    libnss-ldap/bindpw    password    Password
libnss-ldap    libnss-ldap/confperm    boolean    false
libnss-ldap    libnss-ldap/dblogin    boolean    false
libnss-ldap    libnss-ldap/dbrootlogin    boolean    true
libnss-ldap    libnss-ldap/nsswitch    note
libnss-ldap    libnss-ldap/override    boolean    true
libnss-ldap    libnss-ldap/rootbinddn    string    cn=LDAPsearch,cn=Users,dc=domain,dc=com
libnss-ldap    libnss-ldap/rootbindpw    password    Password
libnss-ldap    shared/ldapns/base-dn    string    cn=Users,dc=domain,dc=com
libnss-ldap    shared/ldapns/ldap-server    string    ldap://1.2.3.4/
libnss-ldap    shared/ldapns/ldap_version    select    3
libpam-ldap    libpam-ldap/binddn    string    cn=LDAPsearch,cn=Users,dc=domain,dc=com
libpam-ldap    libpam-ldap/bindpw    password    Password
libpam-ldap    libpam-ldap/dblogin    boolean    false
libpam-ldap    libpam-ldap/dbrootlogin    boolean    false
libpam-ldap    libpam-ldap/override    boolean    true
libpam-ldap    libpam-ldap/pam_password    select    crypt
libpam-ldap    libpam-ldap/rootbinddn    string    cn=LDAPsearch,cn=Users,dc=domain,dc=com
libpam-ldap    libpam-ldap/rootbindpw    password    Password
libpam-ldap    shared/ldapns/base-dn    string    cn=Users,dc=domain,dc=com
libpam-ldap    shared/ldapns/ldap-server    string    ldap://1.2.3.4/
libpam-ldap    shared/ldapns/ldap_version    select    3
libpam-runtime    libpam-runtime/profiles    multiselect    unix, ldap
krb5-config     krb5-config/default_realm       string  DOMAIN.COM

##################
# Make exim work for outgoing mail on the local network
##################
exim4-config    exim4/dc_noalias_regenerate     boolean false
exim4-config    exim4/dc_smarthost      string  mail.domain.com
exim4-config    exim4/dc_relay_domains  string
exim4-config    exim4/dc_relay_nets     string
exim4-config    exim4/dc_localdelivery  select  mbox format in /var/mail/
exim4-config    exim4/dc_local_interfaces       string  127.0.0.1
exim4-config    exim4/dc_minimaldns     boolean false
exim4-config    exim4/dc_eximconfig_configtype  select  mail sent by smarthost; received via SMTP or fetchmail
exim4-config    exim4/no_config         boolean true
exim4-config    exim4/hide_mailname     boolean false
exim4-config    exim4/dc_readhost       string  domain.com
exim4-config    exim4/use_split_config  boolean false
exim4-config    exim4/dc_postmaster     string  linux-admins@domain.com

##################
# Set up samba tools to use the DOMAIN domain/workgroup
##################
samba-common    samba-common/dhcp       boolean false
samba-common    samba-common/workgroup  string  DOMAIN

```

---

### Post by horizn on 2017-01-16
OK, I found the issue. The problem was with duplicated packages defined in the preseed file.

---

