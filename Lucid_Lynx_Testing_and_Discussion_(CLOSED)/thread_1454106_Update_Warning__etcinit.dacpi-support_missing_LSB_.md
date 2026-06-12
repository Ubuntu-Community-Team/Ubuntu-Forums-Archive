---
title: "Update Warning:  /etc/init.d/acpi-support missing LSB information"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Didius Falco on 2010-04-14
This is a warning received after an update I just did:

> Setting up acpi-support (0.134) ...
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>I dutifully went to [http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts) and found this:

> **Run-time dependencies**

 Adding run-time dependencies was a  release goal for Lenny, and dependency based boot sequencing is the  default in Squeeze. There is [a  separate wiki page]("http://wiki.debian.org/LSBInitScripts/DependencyBasedBoot") documenting that effort. 
By documenting the run-time dependencies for init.d  scripts, it becomes possible to verify the current boot order, order the  boot using these dependencies, and also to run boot scripts in parallel  to speed up the boot process. 
Add a block  like this in the init.d script: 
### BEGIN INIT INFO
# Provides:          scriptname
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon.
### END INIT INFOAfter digging around a bit on the LSBI part of the wiki, I'm still unable to determine where in acpi-support this block of code should go. Here is my acpi-support file:

```
#!/bin/bash
# INIT script to check whether we're on batteries, and so start with laptop 
# mode etc enabled.

# BUGS: unless we start *really* late, we have no way of throttling 
# xscreensaver, since it won't be there to command.
. /usr/share/acpi-support/power-funcs

test -f /lib/lsb/init-functions || exit 1
. /lib/lsb/init-functions

test -d /var/lib/acpi-support || exit 0

shopt -s nullglob

case "$1" in
  start)
    log_begin_msg "Checking battery state..."
    /etc/acpi/power.sh
    log_end_msg 0
    ;;
  stop)
    log_begin_msg "Disabling power management..."
    /etc/acpi/power.sh false
    log_end_msg 0
    ;;
  *)
  ;;
esac


```This seems like a pretty important thing, for laptop and non-laptop users alike. Since I'm *not* on a laptop, I don't want my pc thinking it is, but I'm sure laptop users don't want their laptops confused into thinking they are being run with dilithium crystals and have power for years to come, either. :P

My problem is I *think* I know where this block of code should go, but I'd rather be sure. 

Thanks for taking the time to read this - I know it's rather long.

**UPDATE:** Apparently, this is a bug dating back to Karmic. Since the devs are aware of it and my pc boots and runs just fine, I'm taking this off of [COLOR=Red]**Red Alert**[COLOR=Black] and taking a "wait until it's fixed in a patch" approach. 

For any interested, the bug report is here: [/COLOR][/COLOR][https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/305587](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/305587)

---

