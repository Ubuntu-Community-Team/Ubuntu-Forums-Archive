---
title: "How to fix python3 - after messing it up?"
date: 2019-12-20
forum: Installation &amp; Upgrades
---

### Post by Arjunanda on 2019-12-20
I was doing dist-upgrade to my system, but something didn't work as expected, and I also was running the upgrade while doing some other work.

Result python 3 got messed up and I can't run apt updates and cant upgrade the system

Error message:
```
dpkg: error processing package python3 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Käsittelyssä tapahtui liian monta virhettä:
 python3
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

My commandline history:

```
276  sudo apt-get update && sudo apt-get dist-upgrade
  277  sudo apt-get dist-upgrade
  278  sudo apt autoremove
  279  sudo apt-get dist-upgrade
  280  man apt
  281  man dist-upgrade
  282  sudo do-release-upgrade
  283  /usr/bin/python3
  284  sudo do-release-upgrade
  285  sudo rm /usr/bin/python
  286  sudo ln -s /usr/bin/python2.7 /usr/bin/python
  287  sudo do-release-upgrade
  288  sudo ln -sf /usr/bin/python2.7 /usr/bin/python
  289  sudo do-release-upgrade
  290  sudo update-alternatives --remove-all python
  291  sudo update-alternatives --remove-all python3
  292  sudo ln -sf /usr/bin/python3.6 /usr/bin/python3
  293  sudo do-release-upgrade
  294  sudo apt-get install --reinstall python3
  295  sudo do-release-upgrade
  296  sudo dpkg --remove --force-remove-reinstreq --force-depends python3
  297  sudo apt-get -f install
  298  sudo do-release-upgrade
  299  sudo apt-get update
  300  sudo apt-get upgrade
  301  sudo apt-get reinstall python3
  302  man apt-get
  303  sudo apt-get install python3 --reinstall
  304  sudo ln -sf /usr/bin/python2.7 /usr/bin/python
  305  sudo apt-get install python3 --reinstall
  306  sudo do-release-upgrade
  307  history
  308  update-manager 
  309  sudo apt-get update && sudo apt-get upgrade
  310  sudo apt-get install python3
  311  sudo apt-get reinstall python3
  312* sudo dpkg --remove --force-remove-reinstr
  313  sudo dpkg --remove --force-remove-reinstreq python3 && sudo apt-get install python3
```

Now I do not remember anymore what I was actually doing, as this happened before my vacation, and now three weeks later I don't remember anymore what actually happened leading to this situation.

What should I do here?

---

### Post by TheFu on 2019-12-20
I'd do one of these:

a) restore from the backup I had prior to the problem
or
b) reinstall a fresh OS

YMMV.

3 weeks ago was Nov 29th .... since I do daily, versioned, backups ... let's see ... 
```

...
Tue Dec  3 00:07:03 2019         83.3 MB           19.7 GB
Mon Dec  2 00:07:04 2019         36.9 MB           19.8 GB
Wed Nov 27 00:07:04 2019          118 MB           19.9 GB
Tue Nov 26 10:02:40 2019         83.9 MB           20.0 GB
Tue Nov 26 09:20:04 2019         5.99 MB           20.0 GB
Mon Nov 25 09:20:04 2019         38.7 MB           20.0 GB
Sat Nov 23 00:33:04 2019         1.14 GB           21.2 GB
...
Tue Sep 17 00:03:04 2019         90.8 MB           26.1 GB

```
So my laptop doesn't have a backup for 11/29 - I was travelling.
Need to check the desktop:

```

...
Tue Dec  3 01:15:06 2019          405 KB           5.95 GB
Mon Dec  2 01:15:11 2019         8.21 MB           5.96 GB
Sun Dec  1 01:15:11 2019         1.01 KB           5.96 GB
Sat Nov 30 01:15:11 2019       893 bytes           5.96 GB
**Fri Nov 29 01:15:11 2019         5.96 KB           5.96 GB**
Thu Nov 28 01:15:11 2019         2.56 KB           5.96 GB
Wed Nov 27 01:15:05 2019         26.5 KB           5.96 GB
...
Tue Sep 17 01:15:06 2019         1.97 MB           6.62 GB

```
Ok, we're fine there.  Backup versions go back into September for both systems.

Having excellent, versioned backups, is required with malware, viruses, and dumb user mistakes.  Every year I'll make at least 1, perhaps 2-3 dumb user mistakes where restoring from a backup is the best solution.  Backups solve a few issues, not just the obvious things.  Versioned backups solve 100x more issues.

Looking through the history, you've tried more than I would have. These are probably the real issues:
```
sudo update-alternatives --remove-all python
sudo update-alternatives --remove-all python3
```
Python is a core capability required for any server/desktop Linux OS to work.  Best to never mess with it.

If you need a specific version for software development, use **pyenv**.  Do not touch the OS versions of python, perl, php, ruby.  Leave those alone.  Each tool has something like pyenv, rbenv, perlbrew, etc ... to have different versions, libraries, and self-contained scripting environments for developers.

---

### Post by TheFu on 2019-12-20
```
$  sudo do-release-upgrade
```

NEVER do this on a broken system.  NEVER. It won't fix anything and will likely end with a system that won't boot.

---

### Post by Impavidus on 2019-12-21
If you've got a backup of your system, restore it. Else, reinstall.

I don't keep backups of my system, only of my documents. If my system ever gets messed up, I'll reinstall.

---

### Post by TheFu on 2019-12-21
> **Impavidus said:**
> If you've got a backup of your system, restore it. Else, reinstall.

I don't keep backups of my system, only of my documents. If my system ever gets messed up, I'll reinstall.

I don't keep 100% backups of my systems either.  Rather, I keep the things that make putting everything back quickly possible.
[LIST]
[*]* My settings. /home/
[*]* My data. /home/
[*]* Server settings. /etc/
[*]* Server data. /var/lib/lib* and /var/www/* and /opt/ and a few other places, perhaps?
[*]* Any manually installed programs/tools. Stuff in /usr/local/ and  /root/
[*]* List of any manually installed packages.  Captured by *apt-mark  showmanual*
[/LIST]
By restoring those things, in that order, it will effectively recreate a system in 30-45 minutes after a fresh, minimal, OS install so it feels and behaves the same as before.  Plus, it saves 4-8GB of OS stuff that is easily reproduced via re-install of the same version OS. The fresh install solves new HW issues, desired storage layout issues, boot loader changes (legacy -to- UEFI), and moving from 32-bit to 64-bit releases.

There are lots of other techniques too.  For a home, desktop, user, getting everything in /home/ and *apt-mark  showmanual* alone would make almost all the pain of doing a fresh install go away.

---

### Post by Arjunanda on 2020-01-13
Got it fixed. Did the following: ```
apt install --reinstall python3 python python3-minimal --broken
```

my command line history quoted below:

  ```
282  sudo apt-get --reinstall python3
  283  sudo apt-get install --reinstall python3
  284  sudo apt-get install --reinstall python3
  285  man apt-get
  286  apt list --installed
  287  apt list --installed |grep python
  288  apt list --installed |grep python > installed.python.txt
  289  ls list*
  290  ls inst*
  291  less installed.python.txt 
  292  pwd
  293  ls -l `which python`
  294  which python3
  295  which python
  296  ls -la /usr/bin/python
  297  history
  298  sudo apt-get install --reinstall python3
  299  sudo apt-get install --reinstall python
  300  sudo apt-get install --reinstall python3
  301  sudo apt-get install --reinstall python3-minimal
  302  sudo apt-get install --fix-broken
  303  sudo apt-get install --reinstall python
  304  sudo apt-get install --reinstall python3
  305  sudo apt-get install --reinstall python3-minimal
  306  sudo apt-get install --fix-broken
  307  sudo apt autoremove
  308  sudo apt-get update
  309  sudo apt-get upgrade
  310  sudo reboot
```

Now everything is working as expected.

---

### Post by TheFu on 2020-01-13
If someone needs a different python than those installed by the OS, I just finished using pyenv to setup python 3.6.10 and took notes.  Best practice is to never screw with the system-installed versions of any scripting languages.  Always use a local, user-controlled install, if you need a different version.  rbenv, pyenv, perlbrew will do allow this.

---

