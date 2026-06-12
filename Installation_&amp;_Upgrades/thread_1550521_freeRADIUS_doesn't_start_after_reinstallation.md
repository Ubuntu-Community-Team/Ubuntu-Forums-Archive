---
title: "freeRADIUS doesn't start after reinstallation"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by Joshua Huh on 2010-08-11
I purged out and reinstalled freeRADIUS.

# sudo aptutude purge freeradius; sudo aptitude install freeradius

At first installation, it worked at least with its default configuration. Next installation, it won't start it service while i installed it.

What shoud I do to make it work?

I ran "sudo bash -x /etc/init.d/freeradius start", and I can't understand the output.

+ case "$1" in
+ log_daemon_msg 'Starting FreeRADIUS daemon' freeradius
+ '[' -z 'Starting FreeRADIUS daemon' ']'
+ log_use_usplash
+ '[' n = y ']'
+ type usplash_write
+ log_use_fancy_output
+ TPUT=/usr/bin/tput
+ EXPR=/usr/bin/expr
+ '[' -t 1 ']'
+ '[' xxterm '!=' x ']'
+ '[' xxterm '!=' xdumb ']'
+ '[' -x /usr/bin/tput ']'
+ '[' -x /usr/bin/expr ']'
+ /usr/bin/tput hpa 60
+ /usr/bin/tput setaf 1
+ '[' -z ']'
+ FANCYTTY=1
+ case "$FANCYTTY" in
+ true
+ /usr/bin/tput xenl
++ /usr/bin/tput cols
+ COLS=143
+ '[' 143 ']'
+ '[' 143 -gt 6 ']'
++ /usr/bin/expr 143 - 7
+ COL=136
+ printf ' * Starting FreeRADIUS daemon freeradius       '
 * Starting FreeRADIUS daemon freeradius       ++ /usr/bin/expr 143 - 1
+ /usr/bin/tput hpa 142
                                                                                                                                              + printf ' '
 + start-stop-daemon --start --quiet --pidfile /var/run/freeradius/freeradius.pid --exec /usr/sbin/freeradius
+ ret=1
+ log_end_msg 1
+ '[' -z 1 ']'
+ log_use_usplash
+ '[' n = y ']'
+ type usplash_write
+ '[' 136 ']'
+ '[' -x /usr/bin/tput ']'
+ printf '\r'
+ /usr/bin/tput hpa 136
                                                                                                                                        + '[' 1 -eq 0 ']'
+ printf '['
[+ /usr/bin/tput setaf 1
+ printf fail
fail+ /usr/bin/tput op
+ echo ']'
]
+ return 1

What's wrong with it?

---

