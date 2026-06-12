---
title: "&quot;unable to migrate to dependency-based boot system&quot;"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by andypi on 2010-01-13
I have just had an auto-update, and the process has stopped with the warning above. The full error message is given below. Anyone know what's happened here? Thanks.

I had already had problems (not sure if they're somehow resolved or related to this) with updating (see [http://ubuntuforums.org/showthread.php?p=8648836](http://ubuntuforums.org/showthread.php?p=8648836)).

[INDENT]Tests have determined that problems in the boot system exist which prevent migration to dependency-based boot sequencing:

package virtualbox-ose removed but not purged, insserv: warning: script 'K20acpi-support' missing LSB tags and overrides, insserv: warning: script 'usplash' missing LSB tags and overrides, insserv: warning: script 'hwclock-save' missing LSB tags and overrides, insserv: warning: script 'acpid' missing LSB tags and overrides, insserv: warning: script 'gdm' missing LSB tags and overrides, insserv: warning: script 'failsafe-x' missing LSB tags and overrides, insserv: warning: script 'acpi-support' missing LSB tags and overrides, insserv: warning: script 'udevmonitor' missing LSB tags and overrides, insserv: warning: script 'hwclock' missing LSB tags and overrides, insserv: warning: script 'rsyslog-kmsg' missing LSB tags and overrides, insserv: script virtualbox-ose: service vboxdrv already provided!, insserv: script virtualbox-ose: service virtualbox-ose already provided!, insserv: warning: script 'dmesg' missing LSB tags and overrides, insserv: warning: script 'procps' missing LSB tags and overrides, insserv: warning: script 'atd' missing LSB tags and overrides, insserv: warning: script 'avahi-daemon' missing LSB tags and overrides, insserv: warning: script 'udevtrigger' missing LSB tags and overrides, insserv: warning: script 'apport' missing LSB tags and overrides, insserv: warning: script 'udev' missing LSB tags and overrides, insserv: warning: script 'ufw' missing LSB tags and overrides, insserv: warning: script 'rsyslog' missing LSB tags and overrides, insserv: warning: script 'anacron' missing LSB tags and overrides, insserv: warning: script 'network-manager' missing LSB tags and overrides, insserv: warning: script 'dbus' missing LSB tags and overrides, insserv: warning: script 'udev-finish' missing LSB tags and overrides, insserv: warning: script 'module-init-tools' missing LSB tags and overrides, insserv: warning: script 'hal' missing LSB tags and overrides, insserv: warning: script 'cron' missing LSB tags and overrides,

If the reported problem is a local modification, it needs to be fixed manually. If it's a bug in the package, it should be reported to the BTS and fixed in the package. See [http://wiki.debian.org/LSBInitScripts/DependencyBasedBoot](http://wiki.debian.org/LSBInitScripts/DependencyBasedBoot) for more information about how to fix the problems preventing migration.

To reattempt the migration process after the problems have been fixed, run "dpkg-reconfigure sysv-rc".[/INDENT]

---

### Post by andypi on 2010-01-13
Synaptic tells me that the udev package is broken. When I tell synaptic to fix it, I get this error:
[INDENT]
An error occurred

The following details are provided:

E: /var/cache/apt/archives/udev_150-2_i386.deb: trying to overwrite '/etc/modprobe.d/blacklist.conf', which is also in package module-init-tools 0[/INDENT]

---

### Post by pete_m on 2010-05-31
hi Andy Pi,

find myself in the self-same position vis a vis dependency-based boot.  .
found this on Debian . .[http://wiki.debian.org/LSBInitScripts/DependencyBasedBoot](http://wiki.debian.org/LSBInitScripts/DependencyBasedBoot)

i  am attempting to upgrade from Karmic to Lucid/Sid..
after using a customised KarmicNBR, and  experimenting with eb4( Sid-based), 

after grappling with dependencies on libc6 - crucial C libraries - which seem to prevent ubuntu users from locking into Debian Sid.  .( using a'hacked' mountall from launchpad PPA )
upgrade seemed to go well and then got these same error messages . . and ( debconf) frontend locks up and has to be pkllled.

apparently these init scripts do not conform to the new way of doing init.d things . .

i'm now trying a fresh upgrade . ..

aptitude safe-upgrade .  .it's taking forever and has found some confilicts i've not seen what they are yet . ..

---

### Post by andypi on 2010-05-31
I'm afraid I think I ended up doing the same thing. I've yet to take the plunge on Lucid, so we'll see if this thing comes up again!

Andy

---

### Post by pete_m on 2010-05-31
[http://ubuntuforums.org/showthread.php?t=1454106](http://ubuntuforums.org/showthread.php?t=1454106) . . don't know why it's marked solved, unless the  i person decided to just go the tried n tested clean install route . .

but at least it shows the code to put in offending init.d scripts . .if the upgrade doesn't fix things . .


Add a block  like this in the init.d script: 
```

### BEGIN INIT INFO
# Provides:          scriptname
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon.
### END INIT INFO                      
```

btw . .have you come across the libc6 stuff . .felt like the plymouth was holding the rest of the udates to ransom.  .the 'hacked' mountall seems to have dealt with it and i'm now back on up-to-date( Sid/Lucid )  libc6 etc.

the original ( libc6 ) problems were with. . 
consolekit, mountall, upstart, ureadahead, udev, initramfs . .

but touch wood the mountall ppa has shut those ones up ..

incidentally - in that other thread . .

ERROR:root:Installing/upgrading 'ubuntu-minimal' failed
ERROR:root:Installing/upgrading 'ubuntu-standard' failed

i did a aptitude why ( and why-not ) upstart ( one of the previously offending packages)and only ubuntu-minimal seemed to be interested.  ..

---

