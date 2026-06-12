---
title: "HOWTO: Startup oss soundon"
date: 2005-07-05
forum: Installation &amp; Upgrades
---

### Post by gert cuykens on 2005-07-05
Whats the right way to start up oss soundon at startup ?

I tried this with initrd but doesnt work.

#! /bin/sh

NAME=oss
DESC="oss sound"

case "$1" in
start)
log_begin_msg "Starting $DESC: $NAME"
exec /usr/lib/oss/bin/soundon
log_end_msg $?
;;
stop)
log_begin_msg "Stopping $DESC: $NAME"
exec /usr/lib/oss/bin/soundoff
log_end_msg $?
;;
*)
exit 1
;;
esac

exit 0

---

### Post by sundancer on 2005-07-05
What about using
```

#! /bin/sh

NAME=oss
DESC="oss sound"

case "$1" in
  start)
    log_begin_msg "Starting $DESC: $NAME"
    /sbin/start-stop-daemon --start --quiet --exec /usr/lib/oss/bin/soundon
    log_end_msg $?
    ;;
  stop)
    log_begin_msg "Stopping $DESC: $NAME"
    /sbin/start-stop-daemon --start --quiet --exec /usr/lib/oss/bin/soundoff
    log_end_msg $?
    ;;
  *)
    exit 1
    ;;
esac

exit 0

```

Does this work?

---

### Post by gert cuykens on 2005-07-07
almost  :) 

i need to export KERNELINCLUDE=/usr/src/linux/include before starting soundon i tryed this but doesnt work

#! /bin/sh
#update-rc.d /etc/init.d/oss defaults

NAME=oss
DESC="oss sound"

case "$1" in
  start)
    log_begin_msg "Starting $DESC: $NAME"
    export KERNELINCLUDE=/usr/src/linux/include
    /sbin/start-stop-daemon --start --quiet --exec /usr/lib/oss/bin/soundon
    log_end_msg $?
    ;;
  stop)
    log_begin_msg "Stopping $DESC: $NAME"
    /sbin/start-stop-daemon --start --quiet --exec /usr/lib/oss/bin/soundoff
    log_end_msg $?
    ;;
  *)
    exit 1
    ;;
esac

exit 0

---

### Post by sundancer on 2005-07-07
OK. What about:
```

#! /bin/sh
#update-rc.d /etc/init.d/oss defaults

NAME=oss
DESC="oss sound"
KERNELINCLUDE=/lib/modules/`/bin/uname -r`/build/include

case "$1" in
  start)
    log_begin_msg "Starting $DESC: $NAME"
    /sbin/start-stop-daemon --start --quiet --exec /usr/lib/oss/bin/soundon
    log_end_msg $?
    ;;
  stop)
    log_begin_msg "Stopping $DESC: $NAME"
    /sbin/start-stop-daemon --start --quiet --exec /usr/lib/oss/bin/soundoff
    log_end_msg $?
    ;;
  *)
    exit 1
    ;;
esac

exit 0

```
Using the above directory makes this work with different kernel versions.

BTW: Here's a nice init script doing auto-detection for ALSA/OSS:
[http://www-ccrma.stanford.edu/~nando/linux/sounddriver](http://www-ccrma.stanford.edu/~nando/linux/sounddriver)

---

### Post by gert cuykens on 2005-07-07
what does this mean ?

mk_sp_file: mknod failed

---

### Post by gert cuykens on 2005-07-07
KERNELINCLUDE=/lib/modules/`/bin/uname -r`/build/include

doesnt work, i still have to export it manualy

---

### Post by sundancer on 2005-07-07
When does this error message  appear? Did you try the script?

---

### Post by gert cuykens on 2005-07-08
Yes it try's to start soundon but doesnt find the include files until i export kernelinclude manualy before doing ossscript start

The error message had nothing to do with the script but with some dev permissions you can fix that by removing the sound devices.

---

### Post by gert cuykens on 2005-07-09
If i just put export on top it works :)

#! /bin/sh
#update-rc.d /etc/init.d/oss defaults

NAME=oss
DESC="oss sound"
export KERNELINCLUDE=/lib/modules/`/bin/uname -r`/build/include

case "$1" in
  start)
    log_begin_msg "Starting $DESC: $NAME"
    /sbin/start-stop-daemon --start --quiet --exec /usr/lib/oss/bin/soundon
    log_end_msg $?
    ;;
  stop)
    log_begin_msg "Stopping $DESC: $NAME"
    /sbin/start-stop-daemon --start --quiet --exec /usr/lib/oss/bin/soundoff
    log_end_msg $?
    ;;
  *)
    exit 1
    ;;
esac

exit 0

PS log_begin_msg or end_msg isnt reconized as a valid command?

---

