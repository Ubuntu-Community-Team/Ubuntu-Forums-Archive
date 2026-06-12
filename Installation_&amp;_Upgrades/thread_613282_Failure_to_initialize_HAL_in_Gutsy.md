---
title: "Failure to initialize HAL in Gutsy"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by zach014 on 2007-11-14
I just upgraded to ubuntu gutsy, and when i start it up, it stalls at the HAL initialization part for about 5 minutes, until it cancels that and finishes booting.
then when i log in, and error pops up saying that HAL failed to initialize.
also, the internet could not connect, which seems to be related.
the network manager didnt start.
here's the output from this command: "sudo hald --daemon=no --verbose=yes"

```

18:12:10.136 [I] hald.c:529: hal 0.5.9.1
18:12:10.137 [I] hald.c:594: will not daemonize
18:12:10.138 [I] hald_dbus.c:4807: local server is listening at unix:abstract=/var/run/hald/dbus-oHLIXCT5R6,guid=3f9e07eb4a102416825a5b00473b80ca
18:12:10.139 [E] hald_dbus.c:5086: dbus_bus_get(): Failed to connect to socket /usr/local/var/run/dbus/system_bus_socket: No such file or directory

```

any help on this matter would be great
thanks,
zach

---

### Post by zach014 on 2007-11-16
bump

---

### Post by Xavier_To on 2007-11-21
I'd like some help too with that... I had the same problem 2 days ago and the only solution I found that could some this issue was booting with a live CD and making a backup of everything on my hard drive and re-installing.

The only thing I've seen is that the system_bus_socket file dissapeared. Why ? No clue. I'm sure we aren't the only people who have this problem. 

I'm using Xubuntu Gutsy on a toshiba satellite laptop...

In hopes that someone will come to our aid...

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-21
Hi, I think you *might* have the same issue with [this thread]("http://ubuntuforums.org/showthread.php?t=574992").

---

### Post by Xavier_To on 2007-11-21
Thanks a lot. I'll try that as soon as i get off from work !

---

