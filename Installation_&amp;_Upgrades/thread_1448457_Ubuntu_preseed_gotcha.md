---
title: "Ubuntu preseed gotcha"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by mpadams on 2010-04-06
A snippet from my finally-working preseed command to run a "postinstall". btw, this works on Lucid 10.04

The "working command" from Debian+Ubuntu (semicolon missing on end)

```
#d-i preseed/late_command string apt-install zsh; in-target chsh -s /bin/zsh
```

What works on my setup (separated commands + semicolons)

```
d-i preseed/late_command string \
 . /hd-media/dumpinstall.sh ; \
 in-target sh /postinstall/postinstall.sh ;
```

[B]*[Working preseed I found that helped]("http://www.unix.com/unix-advanced-expert-users/81346-running-script-after-preseed-install.html")
*[Cross-posted blog post]("http://unquietwiki.blogspot.com/2010/04/solved-ubuntu-debian-preseed-problem.html")[/B]


**ADDED: MODIFIED WORKING EXAMPLE (REMOVED ACCOUNT CREATION)**
```

# Install the Ubuntu desktop.
tasksel tasksel/first   multiselect ubuntu-desktop
d-i base-installer/kernel/image string  linux-686
d-i hw-detect/load_floppy       boolean false

# If you want the preconfiguration file to work on systems both with and
# without a dhcp server, uncomment these lines and the static network
# configuration below.
d-i netcfg/disable_dhcp boolean false
d-i netcfg/dhcp_failed note
d-i netcfg/dhcp_options select Configure network manually
d-i netcfg/confirm_static boolean true

# Is the system clock set to UTC?
d-i clock-setup/utc     boolean false
d-i clock-setup/ntp     boolean true
d-i clock-setup/ntp-server      us.pool.ntp.org

# Partitioning
d-i partman-auto/expert_recipe string boot-root :: 500 10000 1000000000 ext4 method{ regular } format{ } use_filesystem{ } filesystem{ ext4 } mountpoint{ / } . 64 512 2048 linux-swap method{ swap } format{ } .
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition        select Finish partitioning and write changes to disk
d-i partman/confirm                 boolean true

# Software
d-i netcfg/get_nameservers      string  208.67.222.222 208.67.220.220
d-i apt-setup/universe  boolean true
d-i apt-setup/non-free  boolean true
d-i apt-setup/partner   boolean true
d-i apt-setup/restricted        boolean true
base-config     mirror/http/proxy       string
d-i mirror/http/proxy   string
d-i mirror/http/hostname        string  mirror.anl.gov
d-i mirror/http/directory       string  /pub/ubuntu

# No encrypted user directory
user-setup-udeb user-setup/encrypted-private boolean false

# Autodetect monitor
xserver-xorg xserver-xorg/autodetect_monitor boolean true

# Finish install
d-i preseed/late_command string \
 . /hd-media/dumpinstall.sh ; \
 in-target sh /postinstall/postinstall.sh ;
d-i prebaseconfig/reboot_in_progress    note
d-i cdrom-detect/eject  boolean true
d-i grub-installer/only_debian  boolean true

```

---

