---
title: "couchdb weirdness"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Longinus00 on 2009-10-06
I've noticed in my most recent bootcharts that couchdb was spawning lots of processes (see attached image). This started happening sometime according to my collection of bootcharts.

After I've logged in, running ps yields
```
$ ps awux | grep couchdb
couchdb   1343  0.0  0.0   1836   580 ?        S    10:55   0:00 /bin/sh -e /usr/bin/couchdb -a \"/etc/couchdb/default.ini\" -a \"/etc/couchdb/local.ini\" -b -r 5 -p /var/run/couchdb/couchdb.pid -o /dev/null -e /dev/null -R
dl        2539  0.0  0.0   1836   552 ?        S    10:56   0:00 /bin/sh -e /usr/bin/couchdb -n -a \"/etc/couchdb/default.ini\" -a \"/home/dl/.config/desktop-couch/desktop-couchdb.ini\" -b -r 0 -p /home/dl/.cache/desktop-couch/desktop-couchdb.pid -o /home/dl/.cache/desktop-couch/desktop-couchdb.stdout -e /home/dl/.cache/desktop-couch/desktop-couchdb.stderr -R
dl        2577  0.0  0.0   1836   324 ?        S    10:56   0:00 /bin/sh -e /usr/bin/couchdb -n -a \"/etc/couchdb/default.ini\" -a \"/home/dl/.config/desktop-couch/desktop-couchdb.ini\" -b -r 0 -p /home/dl/.cache/desktop-couch/desktop-couchdb.pid -o /home/dl/.cache/desktop-couch/desktop-couchdb.stdout -e /home/dl/.cache/desktop-couch/desktop-couchdb.stderr -R
dl        2578  0.0  0.7  63044  7980 ?        Sl   10:56   0:00 /usr/lib/erlang/erts-5.7.2/bin/beam.smp -Bd -K true -- -root /usr/lib/erlang -progname erl -- -home /home/dl -noshell -noinput -smp auto -sasl errlog_type error -pa /usr/lib/couchdb/erlang/lib/couch-0.10.0a/ebin /usr/lib/couchdb/erlang/lib/mochiweb-r97/ebin /usr/lib/couchdb/erlang/lib/ibrowse-1.5.2/ebin /usr/lib/couchdb/erlang/lib/erlang-oauth/ebin -eval application:load(ibrowse) -eval application:load(oauth) -eval application:load(crypto) -eval application:load(couch) -eval crypto:start() -eval ssl:start() -eval ibrowse:start() -eval couch_server:start([ "/etc/couchdb/default.ini", "/home/dl/.config/desktop-couch/desktop-couchdb.ini"]), receive done -> done end. -pidfile /home/dl/.cache/desktop-couch/desktop-couchdb.pid -heart
couchdb   7160  0.0  0.0   3040   628 ?        S    11:04   0:00 sleep 5
dl        7189  0.0  0.0   3124   800 pts/0    R+   11:05   0:00 grep --color=auto couchdb
```

There appears to be a repeated task there and the .pid file gets rewritten twice. 

This bug report seems related but I'm not really sure.
[https://bugs.launchpad.net/ubuntu/+source/couchdb/+bug/419091](https://bugs.launchpad.net/ubuntu/+source/couchdb/+bug/419091)

Anybody have any further insights into this?

---

