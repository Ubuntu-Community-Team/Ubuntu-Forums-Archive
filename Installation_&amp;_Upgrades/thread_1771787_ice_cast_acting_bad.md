---
title: "ice cast acting bad"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-05-30
icecast-server is an antique unsupported package, and its closest to anything i can get to run.  i synapticed libxslt1-dev onto my system and im going to work on compiling icecast from source.  if anyone knows why i cant connect to 127.0.0.1:8000 via the synaptic package i would like to know.

also if anyones got a working server, i would like the configs - passwords, and location of configs.


-----------------------------------------------start of **** storm----------------------------------------

mkultra [ ~/Downloads/icecast-2.3.2 ]$ sudo /etc/init.d/icecast2 start
icecast2 daemon disabled - read /etc/default/icecast2.


/etc/default/icecast2 says 

# Name or ID of the user and group the daemon should run under
USERID=icecast2
GROUPID=icecast

# ENABLE=false
ENABLE=true

edited in

now browser shows 127.0.0.1:8000....  again im working with icecast from synaptic repository, and not source.  purging everything seems to have fixed my problems....  before i was getting a gid 130 error...  i was mucking around in the user/group settings the other night.  i should really quit working on building systems @ 5 am!


file:///usr/share/doc/icecast2/index.html

in the browser should be helpful to my cause.

as of right now my password is 'hackme' and its going to be changed!

sudo gedit /etc/icecast2/icecast.xml

restart ice cast to ensure password has changed

sudo /etc/init.d/icecast2 restart

---

### Post by boblizar on 2011-05-30
i just checked 2 shoutcast radio stations i listened to and both of them are using shoutcast 1.9.8 / linux.

[http://www.shoutcast.com/broadcast-tools](http://www.shoutcast.com/broadcast-tools) is where i found shoutcast, really simple package binary executable and config file.


ill further investigate this.  curiosity killed the process, but thats ok im god.

---

