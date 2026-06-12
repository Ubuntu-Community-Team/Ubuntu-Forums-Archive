---
title: "Oracle XE not starting"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by nstuart on 2006-09-05
Ok, so I've installed Oracle XE on 3 other kubuntu systems with out any problems, but now with my 4th install I'm having issues. The server just doesn't seem to be starting up.

I've run the configuration as needed and everything goes fine, but no oracle when its done. If I try to connect through sqlplus all I get is: 
ERROR:
ORA-12157: TNS:internal network communication error

which the oracle information for is not incredibly helpful about.

I'm kind of stuck now. None the log files are helpful as to why its not starting up and I've tried re-installing/configuring it several times to no avail. Anyone have any ideas?

---

### Post by Drag0n on 2006-12-16
I'm having the same problem here. I've tried debugging the issue and I think it's relating to hostnames but I can't tell...  There's no information available from oracle. I'm going to try the windows version at home.

---

### Post by nstuart on 2006-12-16
Ya, I figured out the reason on the machine I was having trouble with. For some reason my loopback device wasn't being started correctly on reboots and when oracle went to ping localhost or 127.0.0.1 it couldn't find it, and it didn't start.

Fixed the lo problems and its behaving itself now! :)

---

### Post by linque on 2007-08-14
How did you fix it? I can't ping localhost or 127.0.0.1 either.

---

### Post by linque on 2007-08-15
After a little searching I figured it out. Apparently when setting up my wireless card on my Dell Latitude D600, I accidentally added a duplicate entry in /etc/network/interfaces. After commenting the entry out, I was able to ping myself with 127.0.0.1, or localhost. You can edit that file using the following command:

```
sudo gedit /etc/network/interfaces
```

Use the "#" symbol in front of any line you want to comment out.

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#iface eth0 inet
```

On a side note, I tried to uninstall Oracle XE in hopes that re-installing would fix some of the issues I was having. Bad idea. I uninstalled by issuing this command:

```
sudo apt-get remove oracle-xe
```

I then removed all directories and files referencing Oracle (mainly /usr/lib/oracle/*), then deleted the oracle user, and dba group. On reinstall (using apt-get) it looked ok at first, but at the end it complained about the oracle user not being created. So I uninstalled again added the dba role, and oracle user back, and tried to reinstall. It made it through the install without any problems, but it did not rebuild the gui menu that lets you start and stop the database, use SQLPLUS, or any of the other functions you might use. I tried to run SQLPLUS from the directory where it was installed, but none of the environment variables were reconfigured, so it failed.

I had it working on an older laptop just a few weeks ago, so I know it's possible to have it running on Ubuntu 7.04. If anyone has any ideas, or can tell me how to clean up after I uninstall Oracle XE, please share your thoughts.

---

