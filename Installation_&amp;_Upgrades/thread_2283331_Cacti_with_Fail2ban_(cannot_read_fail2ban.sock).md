---
title: "Cacti with Fail2ban (cannot read fail2ban.sock)"
date: 2015-06-21
forum: Installation &amp; Upgrades
---

### Post by matthys on 2015-06-21
Hi there,

First of all Fail2ban has some files for Cacti but mentions:
[I]The user running poller.php must have read and write
   access to the socket used by Fail2ban.[/I]

However I think this is a very bad idea, so I modified my /etc/init.d/fail2ban script years ago.
Adding the following lines for the do_start;
```
        start-stop-daemon --start --quiet --chuid "$FAIL2BAN_USER" --exec $DAEMON -- \
                $DAEMON_ARGS start > /dev/null\
                || return 2
        # ADDED so Cacti (www-data) has access to fail2ban socket
        chmod ugo+rwx $SOCKFILE
        return 0
```

This works fine with Ubuntu 14.04 LTS, but now installed a fresh Ubuntu 15.04 server and this seems to use systemctl.

I just wonder how people deal with this, do you change the poller to root?
I really do not understand why there is not much control over the fail2ban.sock, other than root.

Out of the box it will never work, as Cacti poller runs by default as www-data.

Thanks,
Matthijs

---

### Post by dino99 on 2015-06-21
Seems highly related to the systemd login process: your script needs to be compatible (but i'm unable to point you in the good direction, sorry)
the alternative is to use 'upstart' boot option (advanced grub line) until you find how to modify the script; or reverse permanently systemd by installing upstart-sysv (purge systemd-sysv).

---

### Post by matthys on 2015-06-21
Yes ... but if I look at the Ubuntu roadmap they want to move to systemd....

---

