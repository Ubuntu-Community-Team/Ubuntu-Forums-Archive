---
title: "Ubuntu Software Center - frozen installation"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by olamina on 2010-12-19
I'm using Ubuntu 10.04, and yesterday  I started installing K3B via Ubuntu Software Center evening, the process got to 51% and then just "froze". I closed the program and opened it again thinking that would "shock" it back into starting (n00b, i know) but no dice. It has been spinning its wheels for 12 hours now, still at 51%. What should I do? I cannot abort it or pause it or anything, and in the meantime, I can't download anything else. 

Thanks in advance.

---

### Post by sikander3786 on 2010-12-19
If it is still stuck there even after more than 12 hours, just close it, kill it or log out and back in or simply reboot.

Then from Applications > Accessories > Terminal, post the output of these commands.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

What these commands do is to try and fix any broken packages caused by cancelling the download ;-)

---

### Post by olamina on 2010-12-19
[QUOTE=sikander3786;10255933]If it is still stuck there even after more than 12 hours, just close it, kill it or log out and back in or simply reboot.

I closed it. Then re-opened. Then I killed it and re-opened. Now I've just closed it.

The output of 
```
sudo apt-get install -f
```

is

```
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-24 gettext
  linux-headers-2.6.32-21-generic cvs linux-headers-2.6.32-24-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libflac++6
The following packages will be upgraded:
  libflac++6
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/40.4kB of archives.
After this operation, 160kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `libflac++6' missing, assuming package has no files currently installed.
(Reading database ... 206768 files and directories currently installed.)
Preparing to replace libflac++6 1.2.1-2build2 (using .../libflac++6_1.2.1-2build2_i386.deb) ...
Unpacking replacement libflac++6 ...
```

at the moment it just seems to be frozen there...couldn't enter the next one.

---

### Post by sikander3786 on 2010-12-19
You mean apt-get also got stuck at unpacking libflac++6?

If so, I wonder if you are running out of disc space. Post the output of this one as well.

```
df -h
```

---

### Post by olamina on 2010-12-19
this is possible....

here is the output 

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             360G   13G  330G   4% /
none                  493M  344K  493M   1% /dev
none                  497M  5.9M  491M   2% /dev/shm
none                  497M  344K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sdc1             101G   13G   83G  13% /media/bigdaddy
/dev/sdc2              42G  4.2G   38G  11% /media/lilmama
/dev/sdd1             931G  261G  670G  29% /media/LaCie
/dev/sdf2              28G   19G  9.7G  66% /media/RESTORATION
/dev/sde1             7.8G  7.4G  932K 100% /media/c02941b0-5a56-44e7-b0c2-793526ff7038
```

---

### Post by sikander3786 on 2010-12-19
You've got plenty of space on your Ubuntu partition. sde1 is a bit over-crowded but that should matter here.

So, once again quit the process and try these commands.

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

```
sudo apt-get install -f
```

What happens?

---

### Post by olamina on 2010-12-19
```
sudo apt-get clean
```

yielded
```

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

```

seems like i need to deal with this lock situation first, right?

---

### Post by sikander3786 on 2010-12-19
Means there is another instance of apt-get or Synaptic or Software Center or Update Manager running. You can't run them simultaneously ;-)

If anything is running, close it. If not, log out and back in and do those commands.

---

### Post by olamina on 2010-12-22
thanks for your help. 

i ended up rebooting my computer, then i went into software center and nothing was installing, so i tried again to install K3B and got this error message

> Previous Installation Hasn't Completed: The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software.i went into terminal and did a 
> sudo killall apt-getwhich did absolutely nothing. 

i then found this thread 

[HTML]http://ubuntuforums.org/showthread.php?t=1459800[/HTML] and did this

```
sudo dpkg --configure -a
```THEN

```
sudo apt-get -f install
```to which I got

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-24 gettext
  linux-headers-2.6.32-21-generic cvs linux-headers-2.6.32-24-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libflac++6
The following packages will be upgraded:
  libflac++6
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/40.4kB of archives.
After this operation, 160kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
``````
cat /etc/apt/sources.list
``` which allowed the installation to start.

The installation got to 3% and then stopped and gave me an error message. Here are the details

> E:I wasn't able to locate a file for the libflac++6 package. This might mean you need to manually fix this package. (due to missing arch): I'm not sure where to go from here....looking forward to your reply.

---

### Post by olamina on 2010-12-22
OK, problem solved. 

i ran ```
 sudo apt-get -f install
``` again 

and when it said
> 
After this operation, 160kB of additional disk space will be used.
Do you want to continue [Y/n]?

I answered "y" instead of "n"

The libflac was reinstalled and the installation worked perfect.

---

