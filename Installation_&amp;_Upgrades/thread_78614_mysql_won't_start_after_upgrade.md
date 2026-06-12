---
title: "mysql won't start after upgrade"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by pesachzon on 2005-10-18
Hello,
I've just upgraded with apt-get dist-upgrade
and mysql stopped working, now when I try to start it I get:


[HTML]
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket 
'/var/run/mysqld/mysqld.sock' (2                                                                                      )'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists![/HTML]

Does anyone know how to fix this?

thanks

---

### Post by mwnovak on 2005-10-21
I've got the exact same problem: mySQL was up and running fine under Hoary; post-upgrade to Breezy, I get the following error (same as noted above):

```

Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```

The upgrade was completed as follows:

1) edited /etc/apt/sources.list as per [https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

2) apt-get update

3) apt-get dist-upgrade

The only indicated hiccup during the upgrade was that many packages indicated problems (missing or not configured, I believe) with "EN" localisation.  I checked several of those packages after the upgrade, and they seem to work fine.

Looking specifically to mySQL...

I've checked permissions on /var/run/mysqld, and they look to be in order:

```
drwxr-xr-x  2 mysql root 4096 2005-10-20 23:14 mysqld
```

I've tried running with a copy of my pre-upgrade /etc/mysql/my.cnf (I let the "apt-get dist-upgrade" procedure replace my.cnf) to no avail.

Out of total frustration, I even reverted to my Windows roots and completely removed and re-installed (via apt-get) the mysql-server, mysql-client, mysql-common, libmysql*, etc. packages.  No joy.  So, I again removed the packages (via apt-get), deleted every instance of mysql* I could locate on my system, and _then_ reinstalled the packages.  Again, no joy (though I'm pretty sure that last move introduced some ghosts that I'll be chasing down for the next several weeks).

Most of the Google hits I got for this problem indicate username/password issues, but I don't think that applies here: mysqladmin can't find a database to play with.  For example, "mysqladmin -u root version" returns the now-familiar:

```

mysqladmin -u root version
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```

-----

After working through this post, Googling about and trying different things, I just realized that I can't ping localhost and I can't ping 127.0.0.1.  That makes sense: mysql can't connect to localhost because something is awry with the loopback interface... or some such along those lines.

It's late: I'm calling it a night, but I'll post back to this thread tomorrow with either 1) a solution or 2) detailed information about my network setup and a plea for help. :^|

Any and all preemptory (read: headache-saving) input is appreciated.

--MW

---

### Post by mwnovak on 2005-10-21
Okay, so the problem remains: I can't ping localhost (by name or ip):

```

mwnovak@myserver:~$ ping -c 5 localhost
PING myserver.net (127.0.0.1) 56(84) bytes of data.

--- myserver.net ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3998ms

```

Same result if I ping 127.0.0.1

How do I fix this?  I'm not sure where to begin posting troubleshooting information, but the following bits might let someone more savvy lend a hand...

Output from "ifconfig":

```

mwnovak@myserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:65:C1:8D:72  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:65ff:fec1:8d72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:3848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:406784 (397.2 KiB)  TX bytes:416702 (406.9 KiB)
          Interrupt:41 Base address:0xf800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2772 (2.7 KiB)  TX bytes:2772 (2.7 KiB)

```

I believe that's in order, no?  Output from "netstat -rv && netstat -iv":

```

mwnovak@myserver:~$ netstat -rv && netstat -iv
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     *               255.255.255.0   U         0 0          0 eth0
default         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0   1492 0      4114      0      0      0     2943      0      0      0 BMRU
lo    16436 0        33      0      0      0       33      0      0      0 LRU

```

Loopback doesn't show up in the routing table--is that normal?  If I try adding it manually, I get:

```

mwnovak@myserver:~$ sudo route add -net 127.0.0.1
sudo: unable to lookup myserver via gethostbyname()
SIOCADDRT: Invalid argument

```

Not sure what that means, exactly.  What is SIOCADDRT?  What is gethostbyname() and why can't it lookup my hostname?

Other associated information...

My /etc/hostname:
```

myserver.net

```

My /etc/hosts:

```

127.0.0.1 myserver.net localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

My /etc/host.conf:

```

order hosts,bind
multi on

```

My /etc/network/interfaces:

```

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
        hostname www.myserver.net

```

Does anyone have any ideas?  Suggestions?  I can post more information ... I just have no idea what's going on here and I'm not sure where to start.  Searching through the Ubuntu forums, hitting the Debian lists, googling around ... I'm not getting much traction on this problem.  Any input is appreciated.

--MW

---

### Post by dcostelloe on 2005-10-24
can't help you but I'm in the same boat getting same error:

error: 'Can't connect to local MySQL server through socket (2)

Look like mysql thinks there are 2 running...

Will post once I figure this out

:confused: 

I down graded from 4.1 to in hoary 4.0.23

due to client issues

---

### Post by lsald on 2005-10-24
Should this be reported as a bug? I too had the same issues with the Breezy upgrade. I even did a fresh install with the Breezy ISO. When apt-get installing all of the required packages MySQL still couln't *get it up*. 

It reall seems to think that there are two instances running. Googling for this issue brings up little relevant information. 

I will be interested in knowing what the solution is. I am no n00b when it comes to LAMP. 

I was also wondering if any of you are PPC users.

---

### Post by mwnovak on 2005-10-25
Yeah, I'm running a server install on a G4 cube.  In that context, I've yet to have a single ppc-specific problem.

--MW

---

### Post by mwnovak on 2005-10-25
Turns out the loopback interface isn't the problem: part of my firewall script was/is disabling ping responses (see [http://www.ubuntuforums.org/showthread.php?t=80510](http://www.ubuntuforums.org/showthread.php?t=80510)).  

I was using the same firewall script under Hoary, and mySQL worked just fine... guess I never noticed that I couldn't ping localhost.

Back to the drawing board with this mySQL glitch.  Anyone out there making any progress?

--MW

---

### Post by mwnovak on 2005-10-26
I have an old machine in my office, and--to troubleshoot this mysql problem--I decided to install a fresh copy of Breezy onto it.  Following the Ubuntu install, I installed mysql-server (apt-get install mysql-server).  Guess what?  mysqld works like a charm, so I guess there's nothing wrong with the packages themselves.

Still no clue what's wrong with my post-Breezy-upgrade box at home.

After a start/stop of mysql ("sudo /etc/init.d/mysql start"; still results in the same error noted in the original posts of this thread), I got the following in /var/log/syslog:

```

Oct 27 00:05:18 localhost mysqld_safe[11628]: started
Oct 27 00:05:19 localhost mysqld[11632]: InnoDB: No valid checkpoint found.
Oct 27 00:05:19 localhost mysqld[11632]: InnoDB: If this error appears when you are creating an InnoDB database,
Oct 27 00:05:19 localhost mysqld[11632]: InnoDB: the problem may be that during an earlier attempt you managed
Oct 27 00:05:19 localhost mysqld[11632]: InnoDB: to create the InnoDB data files, but log file creation failed.
Oct 27 00:05:19 localhost mysqld[11632]: InnoDB: If that is the case, please refer to
Oct 27 00:05:19 localhost mysqld[11632]: InnoDB: http://dev.mysql.com/doc/mysql/en/Error_creating_InnoDB.html
Oct 27 00:05:19 localhost mysqld[11632]: 051027  0:05:19 Can't init databases
Oct 27 00:05:19 localhost mysqld[11632]: 051027  0:05:19 Aborting
Oct 27 00:05:19 localhost mysqld[11632]:
Oct 27 00:05:19 localhost mysqld[11632]: 051027  0:05:19  InnoDB: Warning: shutting down a not properly started
Oct 27 00:05:19 localhost mysqld[11632]:                  InnoDB: or created database!
Oct 27 00:05:19 localhost mysqld[11632]: 051027  0:05:19 /usr/sbin/mysqld: Shutdown Complete
Oct 27 00:05:19 localhost mysqld[11632]:
Oct 27 00:05:19 localhost mysqld_safe[11638]: ended
Oct 27 00:05:24 localhost /etc/init.d/mysql[11701]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Oct 27 00:05:24 localhost /etc/init.d/mysql[11701]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Oct 27 00:05:24 localhost /etc/init.d/mysql[11701]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Oct 27 00:05:24 localhost /etc/init.d/mysql[11701]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Oct 27 00:05:24 localhost /etc/init.d/mysql[11701]:

```

I checked the [indicated link]("http://dev.mysql.com/doc/mysql/en/Error_creating_InnoDB.html"), read through its suggestions, and deleted the following files:

/var/lib/mysql/ibdata*
/var/lib/ib_logfile*

Following another start of mysqld, I got the following in /var/log/syslog:

```

Oct 27 00:10:32 localhost mysqld_safe[11890]: started
Oct 27 00:10:32 localhost mysqld[11894]: InnoDB: The first specified data file ./ibdata1 did not exist:
Oct 27 00:10:32 localhost mysqld[11894]: InnoDB: a new database to be created!
Oct 27 00:10:32 localhost mysqld[11894]: 051027  0:10:32  InnoDB: Setting file ./ibdata1 size to 10 MB
Oct 27 00:10:32 localhost mysqld[11894]: InnoDB: Database physically writes the file full: wait...
Oct 27 00:10:33 localhost mysqld[11894]: 051027  0:10:33  InnoDB: Log file ./ib_logfile0 did not exist: new to be created
Oct 27 00:10:33 localhost mysqld[11894]: InnoDB: Setting log file ./ib_logfile0 size to 5 MB
Oct 27 00:10:33 localhost mysqld[11894]: InnoDB: Database physically writes the file full: wait...
Oct 27 00:10:33 localhost mysqld[11894]: 051027  0:10:33  InnoDB: Log file ./ib_logfile1 did not exist: new to be created
Oct 27 00:10:33 localhost mysqld[11894]: InnoDB: Setting log file ./ib_logfile1 size to 5 MB
Oct 27 00:10:33 localhost mysqld[11894]: InnoDB: Database physically writes the file full: wait...
Oct 27 00:10:34 localhost mysqld[11894]: InnoDB: Doublewrite buffer not found: creating new
Oct 27 00:10:34 localhost mysqld[11894]: InnoDB: Doublewrite buffer created
Oct 27 00:10:34 localhost mysqld[11894]: InnoDB: Creating foreign key constraint system tables
Oct 27 00:10:34 localhost mysqld[11894]: InnoDB: Foreign key constraint system tables created
Oct 27 00:10:34 localhost mysqld[11894]: 051027  0:10:34  InnoDB: Started
Oct 27 00:10:34 localhost mysqld[11894]: 051027  0:10:34 Fatal error: Can't open privilege tables: Table 'mysql.host' doesn't exist
Oct 27 00:10:34 localhost mysqld[11894]: 051027  0:10:34 Aborting
Oct 27 00:10:34 localhost mysqld[11894]:
Oct 27 00:10:34 localhost mysqld[11894]: 051027  0:10:34  InnoDB: Starting shutdown...
Oct 27 00:10:36 localhost mysqld[11894]: 051027  0:10:36  InnoDB: Shutdown completed
Oct 27 00:10:36 localhost mysqld[11894]: 051027  0:10:36 /usr/sbin/mysqld: Shutdown Complete
Oct 27 00:10:36 localhost mysqld[11894]:
Oct 27 00:10:36 localhost mysqld_safe[11907]: ended
Oct 27 00:10:42 localhost /etc/init.d/mysql[11967]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Oct 27 00:10:42 localhost /etc/init.d/mysql[11967]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Oct 27 00:10:42 localhost /etc/init.d/mysql[11967]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Oct 27 00:10:42 localhost /etc/init.d/mysql[11967]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Oct 27 00:10:42 localhost /etc/init.d/mysql[11967]:

```
 
I spent some time googling terms from the above messages (mysql.host, mysqld.sock, etc) and found some scattered posts mentioning file permissions problems.  Walking through permissions on the mysql directories... everything seems to be in order.

I checked the directories indicated in /etc/mysql/my.cnf:

```

#
# * Basic Settings
#
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
language        = /usr/share/mysql/english

```

Here's what I get (ls output edited for brevity):

```

mwnovak@myserver:~$ sudo ls -l /var/run /var/run/mysqld /usr /var/lib /var/lib/mysql /tmp /usr/share/mysql /usr/share/mysql/english

/tmp:
total 0

/usr:
total 76
drwxr-xr-x    2 root root 20480 2005-10-26 23:01 bin
drwxr-xr-x    2 root root  4096 2005-10-17 00:53 doc
drwxr-xr-x    2 root root  4096 2005-10-17 00:47 games
drwxr-xr-x   62 root root  8192 2005-10-17 00:47 include
drwxr-xr-x   65 root root 20480 2005-10-20 23:05 lib
drwxr-xr-x   10 root root  4096 2005-04-29 18:56 local
drwxr-xr-x    2 root root  4096 2005-10-26 23:01 sbin
drwxr-xr-x  103 root root  4096 2005-10-26 23:01 share
drwxrwsr-x    2 root src   4096 2005-06-24 14:24 src
drwxr-xr-x    5 root root  4096 2005-10-17 00:47 X11R6

/usr/share/mysql:
total 100
-rwxr-xr-x  1 root root   27 2005-09-09 13:16 echo_stderr
drwxr-xr-x  2 root root 4096 2005-10-26 23:01 english

/usr/share/mysql/english:
total 32
-rw-r--r--  1 root root 12626 2005-09-09 13:16 errmsg.sys
-rw-r--r--  1 root root 13667 2005-09-09 13:16 errmsg.txt

/var/lib:
total 80
drwxr-xr-x  4 mysql mysql 4096 2005-10-26 23:01 mysql

/var/lib/mysql:
total 20556
-rw-rw----  1 mysql mysql    25088 2005-10-26 23:01 ib_arch_log_0000000000
-rw-rw----  1 mysql mysql 10485760 2005-10-26 23:01 ibdata1
-rw-rw----  1 mysql mysql  5242880 2005-10-26 23:01 ib_logfile0
-rw-rw----  1 mysql mysql  5242880 2005-10-26 23:01 ib_logfile1
drwxr-xr-x  2 mysql root      4096 2005-10-26 23:01 mysql
drwxr-xr-x  2 mysql root      4096 2005-10-26 23:01 test

/var/run:
total 80
drwxr-xr-x  2 mysql root 4096 2005-10-26 23:01 mysqld

/var/run/mysqld:
total 0

```

I'm no expert with *nix, but the permissions seem to be in order... how does this look to someone else?  

I'm almost ready to backup /etc and /home, axe my current Hoary->Breezy system, and do a clean install of Breezy.  Very frustrating.  At least I'd only been using mysql for testing up until this point ... nothing major at stake with my little server ... but, still, this shouldn't be so painful.

--MW

---

### Post by mwnovak on 2005-10-27
Found this in the bug reports for the mysql-server package: [http://bugzilla.ubuntu.com/show_bug.cgi?id=15549](http://bugzilla.ubuntu.com/show_bug.cgi?id=15549)

The report seems to apply, given the symptoms.  

The "workaround" was/is to uninstall mysql-server and install mysql-server-4.1 instead.  Not what I'd consider an ideal solution, but ... whatever.  I've got a working mysqld again, so I suppose that's what matters. :)

--MW

---

### Post by MatthewMetzger on 2005-11-11
Thanks for posting the solution. I wonder why 4.0 won't work. The application that I am seeking to run on Ubuntu is Koha (a library automation system) and I have read somewhere that it doesn't like MySQL versions above 4.0. I hope this is not the case, as then I would have to figure out how to get MySQL 4.0 to work on breezy.

---

### Post by fortysixandtwo on 2007-02-09
> **mwnovak said:**
> Okay, so the problem remains: I can't ping localhost (by name or ip):

```

mwnovak@myserver:~$ ping -c 5 localhost
PING myserver.net (127.0.0.1) 56(84) bytes of data.

--- myserver.net ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3998ms

```

Same result if I ping 127.0.0.1

How do I fix this?  I'm not sure where to begin posting troubleshooting information, but the following bits might let someone more savvy lend a hand...

Output from "ifconfig":

```

mwnovak@myserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:65:C1:8D:72  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:65ff:fec1:8d72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:3848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:406784 (397.2 KiB)  TX bytes:416702 (406.9 KiB)
          Interrupt:41 Base address:0xf800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2772 (2.7 KiB)  TX bytes:2772 (2.7 KiB)

```

I believe that's in order, no?  Output from "netstat -rv && netstat -iv":

```

mwnovak@myserver:~$ netstat -rv && netstat -iv
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     *               255.255.255.0   U         0 0          0 eth0
default         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0   1492 0      4114      0      0      0     2943      0      0      0 BMRU
lo    16436 0        33      0      0      0       33      0      0      0 LRU

```

Loopback doesn't show up in the routing table--is that normal?  If I try adding it manually, I get:

```

mwnovak@myserver:~$ sudo route add -net 127.0.0.1
sudo: unable to lookup myserver via gethostbyname()
SIOCADDRT: Invalid argument

```

Not sure what that means, exactly.  What is SIOCADDRT?  What is gethostbyname() and why can't it lookup my hostname?

Other associated information...

My /etc/hostname:
```

myserver.net

```

My /etc/hosts:

```

127.0.0.1 myserver.net localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

My /etc/host.conf:

```

order hosts,bind
multi on

```

My /etc/network/interfaces:

```

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
        hostname www.myserver.net

```

Does anyone have any ideas?  Suggestions?  I can post more information ... I just have no idea what's going on here and I'm not sure where to start.  Searching through the Ubuntu forums, hitting the Debian lists, googling around ... I'm not getting much traction on this problem.  Any input is appreciated.

--MW

Hi,

I installed Ubuntu 64bit yesterday and during the installation it did not recognize my ethernet interface. I didn't bother and hit the continue button. I thought I could just as well add the drivers later on. It did concern me though because I'm on a HP DL 380 G5 with Broadcom NICs, it should have picked those up ..

When the install was completed I logged in and typed #ifconfig -a which showed me all of my interfaces, strange I thought (but good..). I later discovered /etc/resolv and /etc/resolv.conf was missing.. something definitely broke during the install *grr*

Anyway.. to the point. The problem you're having happened to me too.
It's caused by the localhost interface having been set to 'down' -mode. That's why it does not respond to ping and that's why other threads like this one [http://www.ubuntuforums.org/showthread.php?t=239053](http://www.ubuntuforums.org/showthread.php?t=239053) has solved it by changing the bind address parameter to an interface that actually says hello.


Cure this with:

[code]
# ifconfig lo down
# ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.

--- 127.0.0.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms

# ifconfig lo up
# ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.018 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.005 ms

--- 127.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.005/0.011/0.018/0.007 ms
# 
</code>


I have a related problem, during install of mysql-server-4.1, this happens.

dpkg: error processing /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-4.1_4.1.15-1ubuntu5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any clues?

---

