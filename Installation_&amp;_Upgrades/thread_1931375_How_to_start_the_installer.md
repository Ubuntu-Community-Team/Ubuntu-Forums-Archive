---
title: "How to start the installer"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by jamapii on 2012-02-25
What is the command line?

The famous debian-installer (as seen on help.ubuntu.org) doesn't exist.

I can provide the rest of the command line (as I guess it autostarts when booting from installation CD if X works)

You need an existing X server (on an existing Unix host) to connect to:

DISPLAY=existing-x-server:0 unknown-command

If that isn't possible, because TCP is not compiled into it, use a vnc server:

# on the existing Unix box
/usr/bin/vncserver :1 -geometry 1280x1024 -depth 24

# Which port needs to be open? 6001
iptables -I INPUT -p tcp --dport 6001 -j ACCEPT

# now back in the ubuntu installation LiveCD
DISPLAY=existing-x-server:1 xterm &    # this test works for me now

# To be filled in
# Call the ubuntu installer

EDIT:
looks like it's ubiquity

Found by searching /etc/init.d and /etc/init

---

