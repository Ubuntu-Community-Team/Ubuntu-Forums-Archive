---
title: "Upgrade from 14.04 to 16.04 fails"
date: 2018-03-16
forum: Installation &amp; Upgrades
---

### Post by markus_b on 2018-03-16
I finally got around to upgrade my daily workhorse from 14.04 to 16.04, but the upgrade is failing.
There is a confirmed bug report which looks similar, but no fix or workaround is mentioned.

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1571146](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1571146)

How to I upgrade ?

```
# sudo do-release-upgrade
Checking for a new Ubuntu release
...
Calculating the changes

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu
...
```

---

### Post by rsteinmetz70112 on 2018-03-16
I've upgraded several machines from 14.04 to 16.04 and although there have been problems I've been successful in all of them. It's been well over a year since I've done a similar upgrade.

The question that comes to mind is why would you (or anyone for that matter) be running a pre-release versions of either 14.04 or 16.04 at this date? 
If you aren't running a pre-release version then it must be something else.

That leaves the third option, are you running any unofficial software and if so what is it?

I'd check to make sure that your 14.04 system is fully updated and everything is configured correctly before trying an upgrade
```
#dpkg --configure -a
```

I'd suggest posting more information about your system and any other error messages you have.

What 14.04 point release are you on?

---

### Post by lvm on 2018-04-17
I also one of many that hit with this issue. The most frequently recommended solution is to look into the /var/log/dist-upgrade/NNNNNNNNNNNN/apt.log and remove broken packages. So I did, but found out that some e.g. xserver-xorg-input-mouse or linux-image-generic-pae are rather important and removing them will break the system completely while some of the broken package complaints are just pure ******** e.g. 'Broken mplayer2:i386 Depends on mplayer'. mplayer2 does not depend on mplayer, it CONFLICTS with mplayer. So at the moment I am stuck.

---

### Post by cruzer001 on 2018-04-17
Please post the output of:

```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

---

### Post by markus_b on 2018-04-17
I did already disable all repositories in sources.list.d, but have added somehting new since. I don't think I modified sources.list.

```

markus@W530:~$ cat /etc/apt/sources.list && echo "----------------" && ls /etc/apt/sources.list.d/*.list
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ch.archive.ubuntu.com/ubuntu/ xenial main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ch.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ch.archive.ubuntu.com/ubuntu/ xenial universe
deb-src http://ch.archive.ubuntu.com/ubuntu/ xenial universe
deb http://ch.archive.ubuntu.com/ubuntu/ xenial-updates universe
deb-src http://ch.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ch.archive.ubuntu.com/ubuntu/ xenial multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://ch.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ch.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.

# Samsung printer drivers
# deb http://www.bchemnet.com/suldr/ debian extra
----------------
/etc/apt/sources.list.d/mixxx-mixxx-trusty.list

```

---

### Post by cruzer001 on 2018-04-17
> This can be caused by: 
* Upgrading to a pre-release version of Ubuntu
You are running 16.04, thats why the message.  The next upgrade would be 18.04, a pre-release version.
```
lsb_release -a
```


```
/etc/apt/sources.list.d/mixxx-mixxx-trusty.list
```
Should be removed.

---

### Post by markus_b on 2018-04-17
> **cruzer001 said:**
> You are running 16.04, thats why the message.  The next upgrade would be 18.04, a pre-release version.


No I'm running 14.04:
```

markus@W530:~$ lsb_release -a
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.5 LTS
Release:	14.04
Codename:	trusty


```

I removed the mixxx-mixxx-trusty.list, no change. Still fails with 'Could not calculate the upgrade   An unresolvable problem occurred while calculating the upgrade.'

---

### Post by cruzer001 on 2018-04-17
Very strange, your sources.list is 16.04.  I assume at some point you have rebooted.

Did you use update-manager for the upgrade?

What kernel are you running?
```
uname -r
```

Anything odd in the /apt directory?
```
ls /etc/apt
```

Have you tried a manual (terminal) update/dist-upgrade?

---

### Post by markus_b on 2018-04-17
> **cruzer001 said:**
> Very strange, your sources.list is 16.04.  I assume at some point you have rebooted.


This may be the core of the problem. I always used 'do-release-upgrade'. Where can I find a 14.04 sources.list ?

---

### Post by cruzer001 on 2018-04-17
> This may be the core of the problem.
A reboot?

> I always used 'do-release-upgrade'.
That is a valid way to upgrade.

> Where can I find a 14.04 sources.list ?
It should no longer exist, the only possible exception is /sources.list.save.  Thats why I asked about your /apt directory and also the kernel and updating.

---

### Post by markus_b on 2018-04-17
Unfortunately the sources.list present are all 16.04:

```

root@W530:~# ls -l /etc/apt
total 100
drwxr-xr-x 2 root root  4096 mar 16 01:37 apt.conf.d
-rw-r--r-- 1 root root  2144 mai  6  2013 apt-file.conf
drwxr-xr-x 2 root root  4096 avr 10  2014 preferences.d
-rw-r--r-- 1 root root  3050 avr 17 20:30 sources.list
drwxr-xr-x 3 root root  4096 avr 17 20:29 sources.list.d
-rw-r--r-- 1 root root  3050 avr 17 20:30 sources.list.distUpgrade
-rw-r--r-- 1 root root  3050 avr 16 12:21 sources.list.save
-rw------- 1 root root    40 avr 17  2014 trustdb.gpg
-rw-r--r-- 1 root root 31408 mar 12 16:51 trusted.gpg
-rw-r--r-- 1 root root 29161 fév  5 13:29 trusted.gpg~
drwxr-xr-x 2 root root  4096 mar 16 01:37 trusted.gpg.d
root@W530:~# diff /etc/apt/sources.list*
diff: extra operand '/etc/apt/sources.list.distUpgrade'
diff: Try 'diff --help' for more information.
root@W530:~# diff /etc/apt/sources.list /etc/apt/sources.list.save 
root@W530:~# diff /etc/apt/sources.list /etc/apt/sources.list.distUpgrade 

```

However I found a 14.04 sources.list (google was my friend).

Unfortunately I still get the same error for my do-release-update.

---

### Post by cruzer001 on 2018-04-17
Your skipping some questions.

```
if [ -f /var/run/reboot-required ]; then echo "reboot required"; else echo "No reboot needed"; fi
```

What about that kernel?

---

### Post by markus_b on 2018-04-17
> **cruzer001 said:**
> Your skipping some questions.

```
if [ -f /var/run/reboot-required ]; then echo "reboot required"; else echo "No reboot needed"; fi
```

What about that kernel?

Sorry !

Kernel:
```
root@W530:/etc/apt# uname -r
3.13.0-51-generic
```
-->> 14.04 Kernel, 16.04 has a 4.4 kernel.

Interestingly, this seems to be the original kernel, 14.04.2 had 3.19, for example.

Reboot-required:
```
ls /var/run/reboot-required
ls: cannot access /var/run/reboot-required: No such file or directory
```

There were some reboots after the do-release upgrade.

---

### Post by markus_b on 2018-04-17
I did some more stuff:

* Ran apt-get update && apt-get upgrade with the 14.04 sources.list in place. Among other things it did upgrade the ubuntu-release-upgrader-core package.
* Rebooted the machine
* Ran do-release-upgrade again, failed again with 'Could not calculate the upgrade'

Is there an alternative, maybe manual way to upgrade (without 'do-release-upgrade') ?

---

### Post by cruzer001 on 2018-04-17
Well I was about to post this:

You have one file I'm not familiar with /apt-file.conf.  Whats in it?

> Interestingly, this seems to be the original kernel

Its still a supported kernel, but even at that its been a while since you had a kernel upgrade.  The latest is 3.13.0-133.  Your install for reasons unknown seems to be stuck in time.  I think its time to try a update.

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
```

And reboot.  To be honest, I really don't know what to expect (good or bad).  There is a risk and could set you up for needing a fresh install.

---

### Post by cruzer001 on 2018-04-17
Now since you reverted back, I think its time for a fresh install.

---

### Post by markus_b on 2018-04-17
/apt-file.conf:
```


[root@W530:~# cat /etc/apt/apt-file.conf 
# Apt-file configuration file

# Substitutions are made as follows:
#	host => remote hostname
#	port => remote port
#	uri => complete URI from sources.list
#	path => path from /
#	dist => the distribution name
#	cache => path to the local cache dir
#	dest => the destination file name inside the cache dir
#	cdrom => cdrom mount point

# Where are located Packages
destination = <host>_<path>_dists_<dist>_Contents-<arch>.gz

# common code blocks can be defined as variables and be used as $check_cmd, etc. later
check_cmd = ( ( gunzip -l "<cache>/<dest>_tmp" >/dev/null 2>&1 || (echo "File is not gzipped."; false) ) && mv "<cache>/<dest>_tmp" "<cache>/<dest>" 2>&1 )
error_cmd = ( rm -f "<cache>/<dest>_tmp"; echo "Can't get <uri>/dists/<dist>/Contents-<arch>.gz" )
post_dl_cmd = $check_cmd || $error_cmd 


# Fetch methods using diffindex-download:
# -i : ignore missing files
# -q : be quiet
# -n <num> : download full file if more than <num> patches would be necessary
http = diffindex-download -i "<uri>/dists/<dist>/Contents-<arch>.gz" <cache>/<dest>
https = diffindex-download -i "<uri>/dists/<dist>/Contents-<arch>.gz" <cache>/<dest>
ftp = diffindex-download -i "<uri>/dists/<dist>/Contents-<arch>.gz" <cache>/<dest>
# In debtorrent URLs, we have to replace 'debtorrent' by 'http', and we always download the full file
debtorrent = diffindex-download -i -n 0 "http://<host>:<port|9988><path>/dists/<dist>/Contents-<arch>.gz" <cache>/<dest>

ssh = scp -P <port|22> "<user>@<host>:/<path>/dists/<dist>/Contents-<arch>.gz" "<cache>/<dest>_tmp" && $post_dl_cmd
rsh = rcp -l <user> "<host>:/<path>/dists/<dist>/Contents-<arch>.gz" "<cache>/<dest>_tmp" && $post_dl_cmd
file = cp "/<path>/dists/<dist>/Contents-<arch>.gz" "<cache>/<dest>"
copy = cp "/<path>/dists/<dist>/Contents-<arch>.gz" "<cache>/<dest>"
cdrom = echo "Put CDROM labeled <path> in the cdrom device and press [ENTER]" > /dev/stderr ; read DUMMY ; mount "<cdrom>"; cp "<cdrom>/dists/<dist>/Contents-<arch>.gz" "<cache>/<dest>" ; umount "<cdrom>"

# Schemes that might require user input on 'apt-file update'
# These will be skipped if -N is given
interactive = cdrom rsh ssh

```

```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install

```

> And reboot. To be honest, I really don't know what to expect (good or bad). There is a risk and could set you up for needing a fresh install.

Have done this, but did not help.

One thing I found: the do-release upgrade tool keeps some logs in /var/log/dist-upgrade/20180417-2336. The apt.log has a ton of these error messages inside:
```

Investigating (0) perl-base [ amd64 ] < 5.18.2-2ubuntu1.4 -> 5.22.1-9ubuntu0.3 > ( perl )
Broken perl-base:amd64 Breaks on perl-modules [ amd64 ] < 5.18.2-2ubuntu1.4 > ( perl ) (< 5.22.1~)
  Considering perl-modules:amd64 8 as a solution to perl-base:amd64 5340
  Added perl-modules:amd64 to the remove list
  Fixing perl-base:amd64 via remove of perl-modules:amd64
  MarkDelete perl-modules [ amd64 ] < 5.18.2-2ubuntu1.4 > ( perl ) FU=0

```

> Now since you reverted back, I think its time for a fresh install.

This is what I fear. I never managed to migrate from one lts to the next without reinstall. It looks o me like the do-release-upgrade just never works, it also has no usable error message.

---

### Post by cruzer001 on 2018-04-17
I have successfully used release upgrades, but I have also had some failures.  Its a roll of the dice.  I think easier to do a fresh install than fight it.

---

### Post by markus_b on 2018-04-17
> **cruzer001 said:**
> I have successfully used release upgrades, but I have also had some failures.  Its a roll of the dice.  I think easier to do a fresh install than fight it.

Yep, think so too. Will have to wait a couple of days. Oh well. 

Thanks for your support !

---

### Post by cruzer001 on 2018-04-17
Welcome and good luck

---

### Post by diewke1 on 2018-04-17
in ubuntu 14.04 click on dash update after type in upgrade to 16.04 ubuntu does the rest
takes a hour [type to upgrade 16.04 or just upgrade]

---

### Post by markus_b on 2018-04-18
> **diewke1 said:**
> in ubuntu 14.04 click on dash update after type in upgrade to 16.04 ubuntu does the rest
takes a hour [type to upgrade 16.04 or just upgrade]

Unfortunately, in my case, Ubuntu fails to do the rest. This does not work on my system.

---

### Post by lvm on 2018-04-19
> **lvm said:**
> 'Broken mplayer2:i386 Depends on mplayer'. mplayer2 does not depend on mplayer, it CONFLICTS with mplayer. So at the moment I am stuck.

Anyway, I removed mplayer2 and upgraded successfully. Now I wish I didn't, but it's a different story. I probably should've mentioned that 'Broken mplayer2:i386 Depends on mplayer' record was the last one in apt.log.

---

### Post by markus_b on 2018-04-19
> **lvm said:**
> Anyway, I removed mplayer2 and upgraded successfully. Now I wish I didn't, but it's a different story. I probably should've mentioned that 'Broken mplayer2:i386 Depends on mplayer' record was the last one in apt.log.

I have plenty of 'broke' packages. I suspect if I remove them then my system will be no longer functional. So I think the upgrade check is useless. Is there a way to override the check and upgrade despite it failing ?

Sample 'broken' count
```

root@W530:/var/log/dist-upgrade/20180403-0027# grep "broken count" /var/log/dist-upgrade/20180403-0027/apt.log
Starting pkgProblemResolver with broken count: 162
Starting 2 pkgProblemResolver with broken count: 162
root@W530:/var/log/dist-upgrade/20180403-0027# grep -c ^Broken /var/log/dist-upgrade/20180403-0027/apt.log
438

```

Sample broken packages. How to interpret this ?
```

Broken python3.4-minimal:amd64 Depends on libpython3.4-minimal [ amd64 ] < 3.4.3-1ubuntu1~14.04.6 > ( python ) (= 3.4.3-1ubuntu1~14.04.6)
Broken python3.4-dev:amd64 Depends on libpython3.4-dev [ amd64 ] < 3.4.3-1ubuntu1~14.04.6 > ( libdevel ) (= 3.4.3-1ubuntu1~14.04.6)

```

---

### Post by lvm on 2018-04-19
> **markus_b said:**
> I have plenty of 'broke' packages. I suspect if I remove them then my system will be no longer functional.
Same story here - over a hundred, including system kernel, but as I said, the package I removed was the last one - perhaps it was the one where the release upgrader was not able to find a solution.

---

### Post by markus_b on 2018-04-19
> **lvm said:**
> Same story here - over a hundred, including system kernel, but as I said, the package I removed was the last one - perhaps it was the one where the release upgrader was not able to find a solution.

So, after deleting the last offending package the upgrade worked ?

```

Broken gnuplot-tex:amd64 Breaks on gnuplot-nox [ amd64 ] < 4.6.4-2 -> 4.6.6-3 > ( universe/math ) (< 4.6.5-5)
  Considering gnuplot-nox:amd64 0 as a solution to gnuplot-tex:amd64 1
  Upgrading gnuplot-nox:amd64 due to Breaks field in gnuplot-tex:amd64
Investigating (9) gnuplot-nox [ amd64 ] < 4.6.4-2 -> 4.6.6-3 > ( universe/math )
Broken gnuplot-nox:amd64 Depends on gnuplot-data [ amd64 ] < none -> 4.6.6-3 > ( universe/doc ) (= 4.6.6-3)
  Considering gnuplot-data:amd64 -1 as a solution to gnuplot-nox:amd64 0
  MarkKeep gnuplot-nox [ amd64 ] < 4.6.4-2 -> 4.6.6-3 > ( universe/math ) FU=0
  Holding Back gnuplot-nox:amd64 rather than change gnuplot-data:amd64

```

Just removed gnuplot (was not straigtforward):
```

root@W530:/var/log/dist-upgrade/20180403-0027# dpkg -r gnuplot-tex gnuplot-nox
dpkg: warning: ignoring request to remove gnuplot-tex which isn't installed
dpkg: dependency problems prevent removal of gnuplot-nox:
 gnuplot depends on gnuplot-nox | gnuplot-x11 | gnuplot-qt; however:
  Package gnuplot-nox is to be removed.
  Package gnuplot-x11 is not installed.
  Package gnuplot-qt is not installed.

dpkg: error processing package gnuplot-nox (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 gnuplot-nox
root@W530:/var/log/dist-upgrade/20180403-0027# dpkg -r gnuplot-nox 
dpkg: dependency problems prevent removal of gnuplot-nox:
 gnuplot depends on gnuplot-nox | gnuplot-x11 | gnuplot-qt; however:
  Package gnuplot-nox is to be removed.
  Package gnuplot-x11 is not installed.
  Package gnuplot-qt is not installed.

dpkg: error processing package gnuplot-nox (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 gnuplot-nox
root@W530:/var/log/dist-upgrade/20180403-0027# dpkg -r gnuplot
(Reading database ... 1952955 files and directories currently installed.)
Removing gnuplot (4.6.4-2) ...
root@W530:/var/log/dist-upgrade/20180403-0027# dpkg -r gnuplot-nox 
(Reading database ... 1952950 files and directories currently installed.)
Removing gnuplot-nox (4.6.4-2) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for tex-common (4.04) ...
Running mktexlsr. This may take some time... done.

```

Now do-release-upgrade seems to work !

```

root@W530:/var/log/dist-upgrade/20180403-0027# do-release-upgrade

........

Fetching and installing the upgrade can take several hours. Once the 
download has finished, the process cannot be canceled. 

 Continue [yN]  Details [d]

```

---

### Post by lvm on 2018-04-20
> **markus_b said:**
> Just removed gnuplot (was not straigtforward):
```

root@W530:/var/log/dist-upgrade/20180403-0027# dpkg -r gnuplot-tex gnuplot-nox
dpkg: warning: ignoring request to remove gnuplot-tex which isn't installed
dpkg: dependency problems prevent removal of gnuplot-nox:

```
If you use apt-get to remove the packages instead of dpkg it will handle the dependencies for you.

> 
Now do-release-upgrade seems to work !

Looks like we did it.

---

### Post by markus_b on 2018-04-20
> **lvm said:**
> Looks like we did it.

I'm afraid we lost in the end. The do-release-upgrade did run, but didn't actually upgrade. It just changed the apt.sources.list. Running apt get upgrade did not work due to broken dependencies. apt-get -f upgrade did run, but resulted in a broken system. I've re-installed from scratch now :-(.

Oh well, thanks for the help, folks !

---

