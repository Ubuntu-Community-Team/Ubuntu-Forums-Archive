---
title: "I'm getting signaled there are updates available, however I've already updated"
date: 2021-08-29
forum: Installation &amp; Upgrades
---

### Post by kevdog on 2021-08-29
I'm running a bunch of virtualized Ubuntu servers that I control via ssh. 

When I use ssh to access the machines, I'm greeted with something like this:

```
Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 5.4.0-81-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

297 updates can be installed immediately.
167 of these updates are security updates.
To see these additional updates run: apt list --upgradable


The list of available updates is more than a week old.
To check for new updates run: sudo apt update

```

The problem however is that I've already updated/upgraded and there are no updates available:

```
$ sudo apt update && sudo apt upgrade -y && sudo apt autoremove
Hit:1 http://us.archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease              
Hit:3 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease            
Hit:4 https://download.docker.com/linux/ubuntu focal InRelease                 
Hit:5 http://security.ubuntu.com/ubuntu focal-security InRelease               
Hit:6 https://apt.syncthing.net syncthing InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Where exactly are these update messages referencing?  It seems they are out of sync?

---

### Post by zebra2 on 2021-08-29
The update application has aquired the update list. You ran apt from the command line and updated. If you go back to the update application and choose update it will update nothing since as you say you have already updated and then the application will clear it's own list. But the application would have cleared it's list anyway the next time it checked for updates.

---

### Post by kevdog on 2021-09-05
@zebra2 -- not sure what your post means. Still getting this error after upgrading.

---

### Post by deadflowr on 2021-09-05
Is it still the same output?
Look at the settings for motd, or more specifically update-motd, 
Files are located in /etc/update-motd.
Related package is base-files.

See if this gives you anything to go on:
[https://stackoverflow.com/questions/41088877/update-motd-d-scripts-not-running]("https://stackoverflow.com/questions/41088877/update-motd-d-scripts-not-running")

---

### Post by kevdog on 2021-09-06
So I've looked into things and it seems when logging in (via ssh) and using PAM module, scripts are run within /etc/update-motd.d/.  You can see this by manually running:

```

run-parts /etc/update-motd.d/

```

So the relevant part regarding the update notifier is within: /etc/update-motd.d/90-updates-available

When I manually run this file I'm greeted with:

```

#> /etc/update-motd.d/90-updates-available/

297 updates can be installed immediately.
167 of these updates are security updates.
To see these additional updates run: apt list --upgradable


The list of available updates is more than a week old.
To check for new updates run: sudo apt update

```

Specifically looking at the script:

```

#!/bin/sh

stamp="/var/lib/update-notifier/updates-available"

[ ! -r "$stamp" ] || cat "$stamp"

find $stamp -newermt 'now-7 days' 2> /dev/null | grep -q -m 1 '.' || /usr/share/update-notifier/notify-updates-outdated

```

Specifically looking at this script the variable $stamp contains the following:
```

# cat /var/lib/update-notifier/updates-available

297 updates can be installed immediately.
167 of these updates are security updates.
To see these additional updates run: apt list --upgradable

```

So the find command isn't exactly what I'm expecting -- I'm not sure what the newermt switch does but I'm totally confused --- where is the actual process that actually checks if updates are available??? Everything I'm seeing is referencing a static file declaring the number of updates.  I was hoping like an executable would be run upon ssh login that would check for updates to generate these numbers -- not just reference a static file that was run at some other time (???like when the VM was booted)???

---

### Post by kevdog on 2021-09-06
So I think I'm onto something here -- On the one system descried above that isnt' working -- I get the following:

```

/usr/lib/update-notifier/apt-check --human-readable
E: Unknown Error: '<class 'AttributeError'>' ('UbuntuDistroInfo' object has no attribute 'supported_esm')

```

However on another installation that is working:
```

/usr/lib/update-notifier/apt-check --human-readable
0 updates can be applied immediately.

```

So the mystery deepens.

---

### Post by kevdog on 2021-09-06
Well I kind of solved the problem -- however its definitely a bug with likely a python package not being updated.  I likely started out on 16.04 and have just updated my VMs (rather than installing fresh) to currently 20.04.  The problem was in the python3 distro-info package.  Possibly this was installed via pip3 -- honestly I don't really know -- however given the fact I don't really use pip3 most of the time on VMs specifically designed to run docker containers, I honestly have no clue.  My reference for the fix is here: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1874250](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1874250)

I fixed my problem via:

```

python3 -m pip uninstall distro-info
sudo apt reinstall python3-distro-info

```

Now things seem to be working:
```

# /usr/lib/update-notifier/apt-check --human-readable
0 updates can be applied immediately.

# python3 -c "import distro_info; print(distro_info.UbuntuDistroInfo().version('eoan'))"
19.10

```

Thanks for pointing me in the right direction on this issue.  Only took about an hour to track the solution to this down -- which in the debugging world is pretty darn quick.

---

### Post by ajgreeny on 2021-09-06
I wonder if running ```
sudo apt update
sudo apt full-upgrade
``` would have sorted this for you straight away?

From man apt
 > full-upgrade performs the function of upgrade but will remove currently installed packages if this is needed to upgrade the system as a whole.

---

### Post by kevdog on 2021-09-06
@ajgreeny
 
I did not try that option although if I restored the VM from snapshot I probably could.  I don't know the answer to your question. I ran the full-upgrade command on the jail after making the changes I wrote about above and no other packages were listed for update:

```

$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I suspect the full-upgrade command would not have done anything however I honestly can't prove this theory without restoring from snapshot.

---

