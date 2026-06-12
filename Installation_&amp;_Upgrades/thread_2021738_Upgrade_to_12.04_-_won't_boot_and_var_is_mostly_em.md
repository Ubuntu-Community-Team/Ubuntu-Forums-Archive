---
title: "Upgrade to 12.04 - won't boot and /var is mostly empty"
date: 2012-07-09
forum: Installation &amp; Upgrades
---

### Post by dvjunk on 2012-07-09
A few days ago I started the 12.04 upgrade on my Mythbuntu System (amd64). I walked away and some time later the power went out. After several days of power cycling/brown outs etc I tried booting my system and it wouldn't boot. I got this message (not copy/paste, so I may not have it exactly correct)
mountall: /lib/x86-64-linix-gnu/libc.so.6: version 'GLIBC_2.14' not found (required by /lib/libply.so.2)
General error mounting filesystems
A maintenance shell will now be started
CONTROL-D will terminate this shell and reboot the system

I was able to boot to a 12.04 liveCD
I tried Install to see the options (I was hoping for a "repair existing", but no luck) and it gave the option to install 12.04 alongside 12.04, so It looks like it got at least partially installed.
I was able to read the files on my 25GB boot partition, but it couldn't mount my 215GB partition. I did a
sudo fsck -f /dev/sda6
and then was able to mount the 215GB.

When I try to boot to recovery and run several iterations of apt-get I keep getting
Could not open lock file /var/lib/dpkg/lock
When I look at the /var path the only thing in there is cache
so there is no /var/lib/dpkg/lock

I tried to use recovery, select network (based on another post)
but when I select network I get
modem-manager ...snip...
Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

It looks like most of my /var directory got deleted. Is that normal during an upgrade?
Can I somehow recover it or replace it?? What if I boot a Mythbuntu liveCD and copy the contents of /var to my hard drive?

I've searched and can't find anyone with this same problem.

Thanks in advance for the help!

---

### Post by rtega on 2012-08-30
Maybe a bit late but the answer probably is here: [http://ubuntuforums.org/showthread.php?t=1983533&page=3](http://ubuntuforums.org/showthread.php?t=1983533&page=3)

---

