---
title: "Automatic Installation becomes interactive"
date: 2011-12-06
forum: Installation &amp; Upgrades
---

### Post by hmyousry on 2011-12-06
Hi,
    This is the first time for me here in the forum, acctually i am trying to create an automatically installed CD i edited the preceed file /cdrom/preseed/ubuntu.seed and started installation but it becomes interactive !!!!!

according to the boot messages the file is read, i even tried to make a syntax error in the file to make sure that this is the file being read, the error showed during booting.

but still the installation is interactive

as i noticed the boot options are loaded from /cdrom/isolinux/txt.cfg

here is its content:

default live-install
label live
  menu label ^Try Ubuntu without installing
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
label live-install
  menu label ^Install Ubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz --
label check
  menu label ^Check disc for defects
  kernel /casper/vmlinuz
  append  boot=casper integrity-check initrd=/casper/initrd.lz quiet splash --
label memtest
  menu label Test ^memory
  kernel /install/mt86plus
label hd
  menu label ^Boot from first hard disk
  localboot 0x80

and here is the ubuntu.seed file

# Enable extras.ubuntu.com.
#d-i    apt-setup/extras    boolean true------------
# Install the Ubuntu desktop.
#tasksel    tasksel/first    multiselect ubuntu-desktop-------------
# On live DVDs, don't spend huge amounts of time removing substantial
# application packages pulled in by language packs. Given that we clearly
# have the space to include them on the DVD, they're useful and we might as
# well keep them installed.
#ubiquity    ubiquity/keep-installed    string icedtea6-plugin openoffice.org------------

# Preseeding only locale sets language, country and locale.
d-i debian-installer/locale string en_US


# The values can also be preseeded individually for greater flexibility.
d-i debian-installer/language string en
d-i debian-installer/country string NL
d-i debian-installer/locale string en_GB.UTF-8
# Optionally specify additional locales to be generated.
d-i localechooser/supported-locales en_US.UTF-8, nl_NL.UTF-8


# Keyboard selection.
# Disable automatic (interactive) keymap detection.
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us

# netcfg will choose an interface that has link if possible. This makes it
# skip displaying a list if there is more than one interface.
d-i netcfg/choose_interface select auto

# If you have a slow dhcp server and the installer times out waiting for
# it, this might be useful.
#d-i netcfg/dhcp_timeout string 60

# If you want the preconfiguration file to work on systems both with and
# without a dhcp server, uncomment these lines and the static network
# configuration below.
d-i netcfg/dhcp_failed note
d-i netcfg/dhcp_options select Configure network manually

# Static network configuration.
d-i netcfg/get_nameservers string 192.168.1.1
d-i netcfg/get_ipaddress string 192.168.1.42
d-i netcfg/get_netmask string 255.255.255.0
d-i netcfg/get_gateway string 192.168.1.1
d-i netcfg/confirm_static boolean true

# Any hostname and domain names assigned from dhcp take precedence over
# values set here. However, setting the values still prevents the questions
# from being shown, even if values come from dhcp.
d-i netcfg/get_hostname string myhost
d-i netcfg/get_domain string mydomain

# Disable that annoying WEP key dialog.
d-i netcfg/wireless_wep string
# The wacky dhcp hostname that some ISPs use as a password of sorts.
#d-i netcfg/dhcp_hostname string radish

# If non-free firmware is needed for the network or other hardware, you can
# configure the installer to always try to load it, without prompting. Or
# change to false to disable asking.
#d-i hw-detect/load_firmware boolean true


# Setting the proxy
#d-i mirror/http/proxy string [http://192.168.1.1:3142](http://192.168.1.1:3142)

### Clock and time zone setup
# Controls whether or not the hardware clock is set to UTC.
d-i clock-setup/utc boolean true

# You may set this to any valid setting for $TZ; see the contents of
# /usr/share/zoneinfo/ for valid values.
d-i time/zone string Africa/Cairo

# Controls whether to use NTP to set the clock during the install
d-i clock-setup/ntp boolean false
# NTP server to use. The default is almost always fine here.
#d-i clock-setup/ntp-server string ntp.example.com


# use the first hard drive 
d-i partman-auto/disk string /dev/sda

# The presently available methods are:
# - regular: use the usual partition types for your architecture
# - lvm:     use LVM to partition the disk
# - crypto:  use LVM within an encrypted partition
d-i partman-auto/method string regular

# You can choose one of the three predefined partitioning recipes:
# - atomic: all files in one partition
# - home:   separate /home partition
# - multi:  separate /home, /usr, /var, and /tmp partitions
d-i partman-auto/choose_recipe select home

# This makes partman automatically partition without confirmation, provided
# that you told it what to do using one of the methods above.
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true

# To create a normal user account.
d-i passwd/user-fullname string Ubuntu User
d-i passwd/username string ubuntu
# Normal user's password, either in clear text
# password set to ubuntu
d-i passwd/user-password password koki
d-i passwd/user-password-again password koki
# or encrypted using an MD5 hash.
#d-i passwd/user-password-crypted password [MD5 hash]
# The installer will warn about weak passwords. If you are sure you know
# what you're doing and want to override it, uncomment this.
d-i user-setup/allow-password-weak boolean true
# Set to true if you want to encrypt the first user's home directory.
d-i user-setup/encrypt-home boolean false

# taskselect
tasksel tasksel/first multiselect ubuntu-desktop
# no upgrade for testing purpose
# d-i pkgsel/upgrade select none
d-i pkgsel/update-policy select safe-upgrade

# taskselect
tasksel tasksel/first multiselect ubuntu-desktop
# no upgrade for testing purpose
# d-i pkgsel/upgrade select none
d-i pkgsel/update-policy select safe-upgrade

# Individual additional packages to install
#d-i pkgsel/include string openssh-server cfengine2 mplayer \
#nautilus-dropbox gimp klavaro ia32-libs lib32asound2 lib32gcc1 lib32stdc++6 libc6-i386 skype auth-client-config winbind \
#libpam-mount smbfs nss-updatedb libnss-db libpam-ccreds
d-i pkgsel/include string openssh-server cfengine2 smbfs auth-client-config \
winbind libpam-mount skype mplayer \
fbreader gimp klavaro p7zip-full gstreamer0.10-ffmpeg \
linphone extcalc postr gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-ugly \
vlc openvpn nss-updatedb libnss-db libpam-ccreds \
network-manager-openvpn network-manager-openvpn-gnome abiword\
bcmwl-kernel-source realtek-rts-pstor-pcie-media-card-reader-dkms cheese

#ntp extcalc
# Language pack selection
d-i pkgsel/language-packs multiselect en



# cfengine2 mplayer klavaro gimp fbreader p7zip-full ntp
popularity-contest popularity-contest/participate boolean false

# This is fairly safe to set, it makes grub install automatically to the MBR
# if no other operating system is detected on the machine.
d-i grub-installer/only_debian boolean true

# This will power off the machine instead of just halting it.
# d-i debian-installer/exit/poweroff boolean true

---

### Post by pablosanmarcos on 2011-12-06
I'm having the same problem, tried every possible preseed configurations and they are of no use. I guess that the problem is that timezone, keyboard and user creation dialogs come after the installation has started, a very good desition to speed up ubuntu setup but not good for people trying to generate an unattended setup.
Have you find the solution?

---

### Post by pablosanmarcos on 2011-12-06
It's incredible. The only way I found after hours and days of research to avoid the user setup form in the installation process on oneiric is to add these lines at the end of the preseed file:
> d-i passwd/root-login boolean true
d-i passwd/root-password-crypted password [MD5 generated by mkpasswd]
d-i passwd/make-user boolean false

Looks like the second line commits an error and that prevents the installer from showing up the user setup form.

---

