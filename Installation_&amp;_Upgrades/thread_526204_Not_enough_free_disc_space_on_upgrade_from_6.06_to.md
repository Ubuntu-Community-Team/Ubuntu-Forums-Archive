---
title: "Not enough free disc space on upgrade from 6.06 to 6.10 when /var and /usr are 512mb."
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by quixotic-cynic on 2007-08-15
/usr is 2G not 512mb (mistake)

When I try to upgrade from 6.06 to 6.10 using > gksu "update-manager -c" I get the error:

> Not enough free disc space

The upgrade aborts now. Please free at least 433M of disc space on /var/cache/apt/archives/. Empty your wastebasket and remove temporary packages of former installations using 'sudo apt-get clean'.

I used > Here's the quick fix. Create or edit /etc/apt/apt.conf and add this line: Dir::Cache::archives "/path/to/your/archive/dir"; from [_another thread_]("http://ubuntuforums.org/showthread.php?t=415590"). That fixed the /var problem but now I have the same thing with /usr.

My partitions are:
```
[FONT="Courier New"]   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          10       80293+  83  Linux    /boot
/dev/sda2              11         924     7341705   83  Linux    /
/dev/sda3             925        1185     2096482+  83  Linux    /usr/local
/dev/sda4            1186        4864    29551567+   5  Extended
/dev/sda5            1186        1446     2096451   83  Linux    /usr
/dev/sda6            1447        1536      722893+  82  Linux swap
/dev/sda7            1537        1601      522081   83  Linux    /var
/dev/sda8            1602        1666      522081   83  Linux    /tmp
/dev/sda9            1667        4853    25599546   83  Linux    /home
/dev/sda10           4854        4864       88326   83  Linux    /usr/X11R6[/FONT]
```

I also did sudo apt-get clean, to no avail.

I tried to research partiton sizes quite extensively before install, however, it appears that I may have screwed up with my choices. If so how much: am I going to have to do some serious re-engineering?

Is the only way to resolve this problem to use the GParted live CD (I really do not want to do this since previous experience suggests screwing with defined partitions is a really bad idea)? Can I use a CD instead?

Thank you.

Edit: I have realised that with my current setup the / partition size and /usr partition sizes are wrong - my root partition is unused since all the programs etc are in /usr/    >.<

Edit 2: I think I will use the 7.04 live cd and alter my partitions during the install. End.

---

