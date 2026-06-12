---
title: "Auto updates seems to be stuck in a loop"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by txinga on 2013-03-16
Thought I'd post this here as well as over on Opsview's forum.

My Ubuntu 12.04 had a bunch of updates including opsview-core. Kicked off the updates from Ubuntu's update manager. It has been cycling through the following error for about 18 hours now.

Failed to connect to database - requesting root password
Use of Uninitialized value $_[1} in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 111, <GEN0> line {this is incremental. now on 4770221 and counting}

HELP please. I have no idea what to do. I'm afraid to kill the update process as this will probably kill the machine.

Thanks,

tx

---

### Post by schragge on 2013-03-16
Try clicking the *Cancel* button.The upgrade will end in an error, for sure. If you haven't noticed which package was being upgraded as this occured, try to find out in /var/log/dpkg.log, and remove that package. After that, re-run update.

---

### Post by txinga on 2013-03-16
The Cancel button is not actionable.

---

### Post by ibjsb4 on 2013-03-16
I have not delt with this problem, but I may of found the answer.

```
sudo apt-get clean
```

This may resolve the problem.  If not reinstalling "debconf" may work.  I have ran the reinstall command on my box without any ill effects so you should be ok.

You will probably have to kill update manager.  Try ..

```
killall update-manager-core
```

Again, this looks like a (safe) solution, but we will only know for sure on your box.

[http://ubuntuforums.org/showthread.php?t=2068601](http://ubuntuforums.org/showthread.php?t=2068601)

---

### Post by txinga on 2013-03-16
kill all update-manager worked. the -core didn't exist. I then broke the lock with sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock. Rebooted and ran a partial upgrade as all the updates wouldn't go through. Opsview still won't update but it IS running. So I could just say screw it and leave it at that version...

---

### Post by ibjsb4 on 2013-03-16
I don't like partial upgrades, it can be trouble.

[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

May want to follow it up with a dist-upgrade (#3).

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

But if you want to leave it go, thats your call :)

---

### Post by Sef on 2013-03-16
> [COLOR=#000000]kill all update-manager worked. the -core didn't exist. I then broke the lock with sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock. Rebooted and ran a partial upgrade as all the updates wouldn't go through. Opsview still won't update but it IS running. So I could just say screw it and leave it at that version...[/COLOR]

Partial upgrades should never be done unless you like cleaning up the mess afterwards. They often will break a system.

---

