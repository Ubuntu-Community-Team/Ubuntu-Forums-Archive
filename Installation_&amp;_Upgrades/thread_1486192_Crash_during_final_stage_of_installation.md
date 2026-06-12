---
title: "Crash during final stage of installation"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by fig_wright on 2010-05-17
I was clean installing Ubuntu 10.04, and for some reason my machine crashed during the final stages (has been a bit unstable recently), when running the init scripts I think. As a result I think that some programs are not being run properly. For example, cups is never running - I have to start it to use printers. And CDs dont mount automatically. Here are the services states:
> 
~ > service --status-all
 [ ? ]  acpi-support
 [ ? ]  acpid
 [ ? ]  alsa-mixer-save
 [ ? ]  anacron
 [ - ]  apparmor
 [ ? ]  apport
 [ ? ]  atd
 [ ? ]  avahi-daemon
 [ ? ]  binfmt-support
 [ - ]  bluetooth
 [ - ]  bootlogd
 [ - ]  brltty
 [ ? ]  console-setup
 [ ? ]  cron
 [ ? ]  cryptdisks
 [ ? ]  cryptdisks-early
 [ ? ]  cryptdisks-enable
 [ ? ]  cryptdisks-udev
 [ - ]  cups
 [ ? ]  dbus
 [ ? ]  dmesg
 [ ? ]  dns-clean
 [ ? ]  ecryptfs-utils-restore
 [ ? ]  ecryptfs-utils-save
 [ ? ]  failsafe-x
 [ - ]  fancontrol
 [ ? ]  gdm
 [ ? ]  gkrellmd
 [ - ]  grub-common
 [ ? ]  hostname
 [ ? ]  hwclock
 [ ? ]  hwclock-save
 [ ? ]  irqbalance
 [ - ]  kerneloops
 [ ? ]  killprocs
 [ - ]  lm-sensors
 [ ? ]  module-init-tools
 [ ? ]  network-interface
 [ ? ]  network-interface-security
 [ ? ]  network-manager
 [ ? ]  networking
 [ ? ]  nmbd
 [ ? ]  ondemand
 [ ? ]  pcmciautils
 [ ? ]  plymouth
 [ ? ]  plymouth-log
 [ ? ]  plymouth-splash
 [ ? ]  plymouth-stop
 [ ? ]  pppd-dns
 [ ? ]  procps
 [ + ]  pulseaudio
 [ ? ]  rc.local
 [ - ]  rsync
 [ ? ]  rsyslog
 [ - ]  saned
 [ ? ]  screen-cleanup
 [ ? ]  sendsigs
 [ ? ]  smbd
 [ ? ]  speech-dispatcher
 [ ? ]  stop-bootlogd
 [ ? ]  stop-bootlogd-single
 [ ? ]  ubiquity
 [ ? ]  udev
 [ ? ]  udev-finish
 [ ? ]  udevmonitor
 [ ? ]  udevtrigger
 [ ? ]  ufw
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ ? ]  unattended-upgrades
 [ - ]  urandom
 [ ? ]  wpa-ifupdown
 [ - ]  x11-common


What can I run to clean this up and get things to how they should be? Dont suggest re-installing - I have no time for that and it might crash at the same point.

---

### Post by ronparent on 2010-05-17
If the install did not complete, the last step of installing grub probably didn't complete either. I see no easy alternative to retrying an install from the live cd. Append the boot parameter **nomodeset** to the boot line. 

The alternatives involve using the live cd to fix the install, which could be time consuing in itself.

---

### Post by fig_wright on 2010-05-18
Grub clearly installed otherwise I wouldnt be able to boot. I'm posting this from the machine right now. It's just a case of printers and CDs at the moment, cant find anything else not working.

---

### Post by fig_wright on 2010-05-18
Actually I appear to have this bug:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/524186](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/524186)

---

### Post by fig_wright on 2010-09-01
The bugfix for the above has just been released and it fixed all my issues :)

---

