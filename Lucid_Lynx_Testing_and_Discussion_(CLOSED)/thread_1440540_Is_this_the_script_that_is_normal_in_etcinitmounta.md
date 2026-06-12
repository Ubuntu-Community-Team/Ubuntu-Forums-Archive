---
title: "Is this the script that is normal in /etc/init/mountall.conf"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2010-03-27
It just does not like the Lucid script I had before I lost it and had to:
sudo apt-get install --reinstall mountall because I had screwed it up.
If someone would look in their /etc/init/mountall.conf and let me know.

# temporary, until we have progress indication
# and output capture 
console output

script
    . /etc/default/rcS
    [ -f /forcefsck ] && force_fsck="--force-fsck"
    [ "$FSCKFIX" = "yes" ] && fsck_fix="--fsck-fix"
    [ -n "$TMPTIME" ] && tmptime=10"--tmptime=$TMPTIME"
    exec mountall --daemon $force_fsck $fsck_fix $tmptime
end script

post-stop script
    rm -f /forcefsck 2>dev/null || true
end script

---

### Post by coffeecat on 2010-03-27
My (untouched) Lucid /etc/init/mountall.conf:

```
# mountall - Mount filesystems on boot
#
# This helper mounts filesystems in the correct order as the devices
# and mountpoints become available.

description    "Mount filesystems on boot"

start on startup
stop on starting rcS

expect daemon
task

emits virtual-filesystems
emits local-filesystems
emits remote-filesystems
emits all-swaps
emits filesystem
emits mounting
emits mounted

# temporary, until we have progress indication
# and output capture (next week :p)
console output

script
    . /etc/default/rcS
    [ -f /forcefsck ] && force_fsck="--force-fsck"
    [ "$FSCKFIX" = "yes" ] && fsck_fix="--fsck-fix"

    exec mountall --daemon $force_fsck $fsck_fix
end script

post-stop script
    rm -f /forcefsck 2>dev/null || true
end script
```

---

### Post by garvinrick4 on 2010-03-27
Thank You Coffeecat I had 2 extra lines, new something looked off.
I appreciate it. Did not have Live CD in Lucid to look at, seems all my Live medium is in 9.10. Will make sure I make one in my testing from now on.

---

