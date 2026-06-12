---
title: "Jaunty update broke SSH tunnel .."
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dwarness on 2009-03-27
I've been running Jaunty for a few weeks now without many issues until today.  Our company has multiple remote sites, and I use ssh tunneling to access those sites seamlessly using the following command:

 ssh -fM -w 0:0 -o TCPKeepAlive=yes -o ServerAliveInterval=10 -S /tmp/control-$IFACE  root@<hostname> 'ifdown tun0; ifup tun0'

After today's update, this has stopped working and prints out the following error:

channel 0: open failed: administratively prohibited: open failed

While trying to investigate this, I found that dmesg | tail was giving the following error:

[ 4766.504539] tun0: Disabled Privacy Extensions

Any thoughts as to what changed, or how to fix this?

---

### Post by bapoumba on 2009-03-27
Moved to Jaunty.

---

### Post by syko21 on 2009-03-27
Others have reported a similar problem doing an upgrade from gutsy to hardy. Perhaps try the command on livecd and see if its an upgrade issue.
[http://ubuntuforums.org/showthread.php?t=597288](http://ubuntuforums.org/showthread.php?t=597288)

---

### Post by dwarness on 2009-03-27
Well, it worked completely fine this morning, and after I did an update of the packages that came out last night, it stopped.

Strangely, it started working after lunch and I have no clue why.  I'll have to investigate it further.

---

