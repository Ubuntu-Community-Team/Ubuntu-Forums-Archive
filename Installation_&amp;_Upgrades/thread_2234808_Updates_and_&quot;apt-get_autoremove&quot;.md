---
title: "Updates and &quot;apt-get autoremove&quot;"
date: 2014-07-17
forum: Installation &amp; Upgrades
---

### Post by Kirkx on 2014-07-17
I'm a Linux newbie trying to figure out the best method to keep the system as clean as possible, without any orphaned files scattered all over the filesystem. I don't want any configuration files from deleted applications laying around in /home or in any other directory. Which is the proper order of running the following three commands when performing updates:

Option-1)
```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade

```

Option-2)
```

sudo apt-get update
sudo apt-get autoremove
sudo apt-get dist-upgrade

```

Option-3)
```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove

```

---

### Post by kc1di on 2014-07-17
option # 3 is the way I would do it,  You may also want to check out[ Ubuntu-tweak]("http://ubuntu-tweak.com/")  it has a nice janitor that works well.

---

### Post by ian-weisser on 2014-07-17
> **Kirkx said:**
> I don't want any configuration files from deleted applications laying around in /home or in any other directory.

See the apt-get manpage.

apt-get remove/autoremove WON'T remove config files from /etc. Either use apt-get's purge option, or manually delete these file after apt-get's removal is complete.

All config files in /home must be deleted manually. apt-get will not remove files in /home under any circumstances. No setting can make it do so.

Running autoremove daily isn't usually helpful. Try running it when you actually remove something.

Running dist-upgrade instead of upgrade daily also isn't usually helpful...though it won't hurt in Ubuntu. dist-update does something very different in Debian than it does in Ubuntu, so be careful giving dist-upgrade as advice to everybody.

---

### Post by Kirkx on 2014-07-18
Thanks for all replies.

1) I've just read on another thread that "apt-get autoremove" apparently removes obsolete kernels (Ubuntu 14.04+). So the key seems to be to learn to use this command wisely. First run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
Look at on-screen messages and if some files have been removed run:
```

sudo apt-get autoremove

```

2)
> ian-weisser: All config files in /home must be deleted manually. apt-get will not  remove files in /home under any circumstances. No setting can make it do  so.

Ok, so it is different than in Windows, where configuration files would be removed if the uninstaller was programmed properly (and it's always a big "if") or if you use some third party uninstall utility like Revo Uninstaller that would hack into the registry, start menu, etc. and do some extra cleaning.

In that case, after installing a new application with:
```

sudo apt-get install <package name>

```
is there a way to view the list of all directories created by the installer (including the directories created in /home), something similar to:
```

dpkg -L <package name>

```
A list like that would be handy if later you decided to uninstall the application, to look for files that were left over.

---

### Post by ian-weisser on 2014-07-18
> **Kirkx said:**
> I've just read on another thread that "apt-get autoremove" apparently removes obsolete kernels (Ubuntu 14.04+)

Well, there's some wiggle room there, and it's a little more complicated than that. Autoremove *should* always have removed obsolete kernels (and obsolete everything else); not doing so was a bug.

apt (not dpkg) keeps track of whether or not a package is installed by human request ('manual') or pulled in as a dependency ('auto'). The *apt-mark* application can toggle those.

autoremove can only remove packages marked 'auto' (plus 'manual' packages specified on the command line)



> **Kirkx said:**
> 
is there a way to view the list of all directories created by the installer (including the directories created in /home), something similar to:
```
dpkg -L <package name>
```
A list like that would be handy if later you decided to uninstall the application, to look for files that were left over.

Well, sure. I think you answered you own question there.
dpkg *is* the installer and uninstaller.
You need to get the package's listing *before* you uninstall the package. Since the listing is provided by the package, of course.

---

### Post by Navneet_Kumar on 2014-07-18
Installing the ubuntu tweak tool surely will help..........

---

### Post by ibjsb4 on 2014-07-18
I like BleachBit and it is in the 14.04 software center.

[https://apps.ubuntu.com/cat/applications/precise/bleachbit/](https://apps.ubuntu.com/cat/applications/precise/bleachbit/)

---

### Post by oldos2er on 2014-07-18
> **Kirkx said:**
> 
In that case, after installing a new application with:
```

sudo apt-get install <package name>

```
is there a way to view the list of all directories created by the installer (including the directories created in /home), something similar to:
```

dpkg -L <package name>

```
A list like that would be handy if later you decided to uninstall the application, to look for files that were left over.

Configuration files in the user's home folder probably won't show up in a dpkg list though, they may not be created until the program is run for the first time.

---

