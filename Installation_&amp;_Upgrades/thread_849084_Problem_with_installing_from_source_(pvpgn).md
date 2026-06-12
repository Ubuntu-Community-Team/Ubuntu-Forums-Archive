---
title: "Problem with installing from source (pvpgn)"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by Georgie.Mathews on 2008-07-04
I wanted to try out the pvpgn server on my Ubuntu Desktop 7.10.

I used the guide from [http://pvpgn.imigi.ro/index.php/Install_on_unix_from_sources](http://pvpgn.imigi.ro/index.php/Install_on_unix_from_sources) to set it up.

However i noticed a problem, i followed the exact steps, using the  pvpgn-1.8.2.tar.gz and pvpgn-support-1.1.tar.gz packages.

I wasnt going to use MYSQL (since i just wanted to get the feel of it) so these are the commands i used to install :

I extracted the files from the tar archives into its folders on my Desktop.

I got into terminal, and in the  pvpgn-1.8.2 directory i typed :

```

./configure
```

```
make 
```

```
sudo make install
```

Now the instructions were to copy the support files into /var/files/ but i noticed that it installed to /usr/local/var rather.
So i still copied it to the /usr/local/var/files directory. The bnetd.conf was in /usr/local/etc and not in /etc/ as stated in the guide.

After that, i uncommented the line in bnetd.conf which refers it to be a plain storage mode (i left the default settings) :

```
storage_path = file:mode=plain;dir=
```

Then i ran 
```
bnetd
```

To check if the installation was succesful i typed :
```
ps ax | grep bnetd
```

But all i got was 
```
12657 pts/0    S+     0:00 grep bnetd
```

Pls do help :)

---

### Post by pxc on 2008-07-30
It's most likely a permissions issue. When you install the (currently out-of-date) package, it runs bnetd through an boot script located in /etc/init.d/pvpgn. These scripts are run as root. I notice the same thing on my system if I manually start pvpgn as a user, but if I run it as root, it shows up in the process list.

Sorry also for the delayed response. I'm surprised no one else here uses PvPGN. I actually only stopped by to see if some more advanced user than I came in and released some updated package that I could use as a stopgap until the Ubuntu developers respond to my bug report.

In summary, use sudo to run bnetd. Also, you may have better luck with package-specific issues for (relatively) unpopular or uncommon packages on the [application's forums]("https://bugs.launchpad.net/ubuntu/+source/pvpgn/+bug/253336"). Also, if you go there, make sure to be polite about grammar and such things as most of the users there (as well as the lead developer) are not native English speakers.

---

### Post by pxc on 2008-07-30
Some new discoveries!
```
pxc@cista:~$ bnetd -h
usage: bnetd [<options>]
    -c FILE, --config=FILE   use FILE as configuration file (default is /etc/pvpgn/bnetd.conf)
    -d FILE, --hexdump=FILE  do hex dump of packets into FILE
     -f, --foreground         don't daemonize
    -D, --debug              run in debug mode (run in foreground and log to stdout)
    -h, --help, --usage      show this information and exit
    -v, --version            print version number and exit
```
Note the --foreground option.
```
pxc@cista:~$ bnetd -f
Jul 30 13:12:54 [error] eventlog_open: could not open file "/var/lib/pvpgn/bnetd.log" for appending (fopen: Permission denied)
Jul 30 13:12:54 [fatal] eventlog_startup: could not use file "/var/lib/pvpgn/bnetd.log" for the eventlog (exiting)
```

On my box I did the following to add a new system user for pvpgn with no rights and no shell, and give it complete access to pvpgn-related files.
```
sudo useradd -g nogroup -s /bin/false -d /home/pvpgn-srv -r pvpgn-srv
sudo chown pvpgn-srv /etc/pvpgn /var/lib/pvpgn /usr/games/pvpgn /usr/share/games/pvpgn
```

Now I can run PvPGN as someone other than root (which makes me feel much safer about running a service facing the internet). I start it (through my init script) more or less like this.
```
sudo start-stop-daemon --start --exec /usr/sbin/pvpgn --chuid pvpgn-srv
```

If you set up the user with the same command, you can launch your source compiled version like this:
```
su -c '/path/to/bnetd' pvpgn-srv
```
Just make sure you replace /path/to/bnetd with the path to your executable.

Good luck!

---

