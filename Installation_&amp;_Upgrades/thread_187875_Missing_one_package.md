---
title: "Missing one package"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by ssmithy on 2006-06-03
I'm have a little trouble with my Breezy to Dapper Upgrade.  I went through the sticky thread above to help me solve my dependency problems.

When I run

```
sudo apt-get dist-upgrade
```

I get the error that this package is missing:

```
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: slocate but it is not installed
E: Unmet dependencies. Try using -f.
```

So I do so, and...

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  slocate
The following NEW packages will be installed:
  slocate
0 upgraded, 1 newly installed, 0 to remove and 532 not upgraded.
117 not fully installed or removed.
Need to get 0B/30.1kB of archives.
After unpacking 156kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 90292 files and directories currently installed.)
Unpacking slocate (from .../slocate_3.0.beta.r3-1_i386.deb) ...
Removing `diversion of /etc/cron.daily/find to /etc/cron.daily/find.notslocate by slocate'
dpkg-divert: rename involves overwriting `/etc/cron.daily/find' with
  different file `/etc/cron.daily/find.notslocate', not allowed
dpkg: error processing /var/cache/apt/archives/slocate_3.0.beta.r3-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/slocate_3.0.beta.r3-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have no idea what to next.  Can anyone push me in the right direction on how to solve this?  Thanks in advance!

---

### Post by kingmonkey on 2006-06-03
have you tried apt-get -f remove?

---

### Post by ssmithy on 2006-06-03
I sure did.  It gives me a similar message.

```
$ sudo apt-get -f remove
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  slocate
The following NEW packages will be installed:
  slocate
0 upgraded, 1 newly installed, 0 to remove and 532 not upgraded.
117 not fully installed or removed.
Need to get 0B/30.1kB of archives.
After unpacking 156kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 90292 files and directories currently installed.)
Unpacking slocate (from .../slocate_3.0.beta.r3-1_i386.deb) ...
Removing `diversion of /etc/cron.daily/find to /etc/cron.daily/find.notslocate by slocate'
dpkg-divert: rename involves overwriting `/etc/cron.daily/find' with
  different file `/etc/cron.daily/find.notslocate', not allowed
dpkg: error processing /var/cache/apt/archives/slocate_3.0.beta.r3-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/slocate_3.0.beta.r3-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ssmithy on 2006-06-03
Hmmm... stil nothing.  I've been searching for any other threads with similar problems but I've yet to find anything.  My sources.list looks fine.  Perhaps I need to rename the /etc/cron/.daily/find file?

---

### Post by llamakc on 2006-06-03
This could break stuff, but I've used this trick on Debian:

dpkg --force-overwrite /var/cache/apt/archives/slocate_3.0.beta.r3-1_i386.deb

---

### Post by llamakc on 2006-06-03
dpkg -i --force-overwrite /var/cache/apt/archives/slocate_3.0.beta.r3-1_i386.deb

May actually be the answer. I forget.

---

### Post by christhemonkey on 2006-06-03
That would work, but personally, i would move the offending file (/etc/cron.daily/find) to your home directory an then try again and see what happens :)

```
sudo mv /etc/cron.daily/find ~/ 
```

and if their is a problem, just move it back, and then try the force-overwrite option.  (i never like forcing things, since i completely broke things by force installing some library and having to reinstall)

To revert
```
sudo mv ~/find /etc/cron.daily/find 
```

---

### Post by llamakc on 2006-06-03
Even before doing the --force-overwrite I would make sure I have re-ran `apt-get update` just in case the problem was straightened out by the package maintainers.

---

### Post by ssmithy on 2006-06-03
Same stickin messages as before.

At least it didn't break anything. :D 

Man, I wish I knew how to get aound this thing!  Unfortunately, this is a bit of a speed-bump.

---

### Post by ssmithy on 2006-06-03
I moved the file and it worked like a champ.  Thanks!  I just have to install ubuntu-desktop and reboot.  Thanks a lot guys!

---

