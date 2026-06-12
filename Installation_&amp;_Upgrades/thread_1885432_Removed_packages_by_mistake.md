---
title: "Removed packages by mistake"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by timswait on 2011-11-23
I was fiddling with things I shouldn't have been fiddling with in package manager on my kubuntu installation. I was removing packages that I didn't think I needed but I seem to have accidentally removed some that I really did need!
Now my computer turns on, shows the grub screen, but when I try to boot Kubuntu I get the kubuntu logo indefinitely but nothing else happens, no login screen or anything else :(
I can boot to a command line so please can someone tell me a command to either re-install the packages I just removed (I don't know the name of them all! Is there some kind of history for un-doing recent changes?) or alternatively to just install all the packages that are required to successfully boot. I'm worried I've somehow managed to remove the kde desktop, or at least some vital packages. I feel very stupid now :(

---

### Post by nothingspecial on 2011-11-23
A log of the packages you removed will be in /var/log/apt in a file called history.log

Try reinstalling the packages you removed.

---

### Post by timswait on 2011-11-23
This seems to be getting worse!
I typed ```
kate /var/log/apt/history.log
```
to try to open the file so I could read it, but it said kate wasn't installed, so I tried:
```
apt-get install kate
```
but got
> W: Not using locking for read only lock file /var/lib/dpkg/lock
E:dpkg was interupted, you must manuallu run 'dpkg --configure -a' to correct the problem.
So I typed 'dpkg --configure -a' and got:
> dpkg: error: unable to access dpkg status area: Read-only file system
So two questions: Firstly how can I read the log file without kate? Secondly would I be able to re-install the lost packages even if I knew what they were, or is this dpkg error serious?
Thank you

---

### Post by surfer on 2011-11-23
make sure you run these commands with root privilieges:
```
$ sudo dpkg --configure -a
```
and
```
$ sudo apt-get install kate
```

and to just view a log file, more or less might be a lighter option:
```
$ less /var/log/apt/history.log 
```

---

### Post by timswait on 2011-11-23
I already have root privileges as I've entered the command line from the recovery prompt at he boot up as root, so using sudo doesn't make a difference, it still gives the same error message.
Using "less" worked, I accessed the log file. There's a long list with today's date, and several with very important sounding names like "kde-baseapps". However when I try "apt-get install" any of these I still get the same error as for trying to install kate.

---

### Post by surfer on 2011-11-23
hmmm... is your var mounted read-only?
could you post the output of
```
$ cat /etc/mtab
```

---

### Post by timswait on 2011-11-23
Hi there:
> /dev/sda5 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0 
none /sys/kernel/security securityfs rw 0 0
udev /dev devmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gig=5,mode=0620 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda3 /mnt/windocs fuseblk rw,noexec,nosuid,nodev,allow_other,blksize=4096,defaults_permissions 0 0
Cheers

---

### Post by ajgreeny on 2011-11-23
There are other logs which may help.

Try running ```
grep -w remove /var/log/dpkg.log
``` from recovery mode and it should tell you exactly what has gone with output something like
```
2011-10-16 12:40:27 remove appmenu-gtk 0.3.0-0ubuntu1 <none>
2011-10-16 12:40:29 remove appmenu-gtk3 0.3.0-0ubuntu1 <none>
2011-10-16 12:40:30 remove appmenu-qt 0.2.2-0ubuntu1 <none>
2011-10-16 12:40:31 remove firefox-globalmenu 7.0.1+build1+nobinonly-0ubuntu2 <none>
2011-10-16 12:40:32 remove indicator-appmenu 0.3.1-0ubuntu2 <none>
2011-10-16 12:40:33 remove thunderbird-globalmenu 7.0.1+build1+nobinonly-0ubuntu1 <none>
2011-10-21 16:21:32 startup packages remove
2011-10-21 16:21:34 remove overlay-scrollbar 0.2.11-0ubuntu1 <none>
2011-10-21 16:21:34 remove liboverlay-scrollbar-0.2-0 0.2.11-0ubuntu1 <none>
2011-10-21 16:21:35 remove liboverlay-scrollbar3-0.2-0 0.2.11-0ubuntu1 <none>
```
You can then use recovery mode to add it all back with ```
apt-get install <list of packages>
```

---

### Post by drmrgd on 2011-11-23
I usually get this when I'm in recovery mode as well.  You may need to remount your hard drive with read and write permissions in order to fix it.  See this thread for two solutions:

[http://ubuntuforums.org/showthread.php?t=1870817]("http://ubuntuforums.org/showthread.php?t=1870817")

---

### Post by timswait on 2011-11-23
OK, thanks for this, making some progress now, ajgreeny, surfer and nothingspecial's suggestions have given me a list of which packages to re-install. Drmrgd's suggestion of remounting worked, I successfully ran "dpkg --configure -a" and then using apt-get install works to the point of trying to install the package. 
My problem now is that I don't think my internet connection is working. I get a list of "Failed to fetch..." and "Could not resolve gb.archive.ubuntu.com". I don't see either LED flashing on the LAN socket even when I plug in and out the LAN cable. So my (hopefully) final question is how do I get the networking working? I'm now a bit more optimistic that I can fix this if I can download these packages.

---

### Post by nothingspecial on 2011-11-23
Did you choose recovery mode with networking?

If so, maybe you just need to

```
ifconfig eth0 up
```

---

### Post by timswait on 2011-11-23
:D:D:D
Got it sorted. Found out how to turn on the ethernet here:
[http://serverfault.com/questions/21475/starting-network-connection-from-ubuntu-recovery]("http://serverfault.com/questions/21475/starting-network-connection-from-ubuntu-recovery")
Installed the packages I'd removed and now it works!!
Thanks for all you help.

---

