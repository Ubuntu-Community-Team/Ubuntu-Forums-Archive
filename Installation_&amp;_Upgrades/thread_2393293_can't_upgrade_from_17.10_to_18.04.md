---
title: "can't upgrade from 17.10 to 18.04"
date: 2018-06-01
forum: Installation &amp; Upgrades
---

### Post by gibsonsimswilson on 2018-06-01
Hello

First all I can do is post the message and fingers crossed someone can walk me through the solution. I really have no idea what to do when I open the terminal so I hope someone can explain in detail how I can correct this error.

I am trying to upgrade 

Thanks in advance...

```
Preconfiguring packages ...
(Reading database ... 828801 files and directories currently installed.)
Removing systemd-shim (9-1bzr4ubuntu1) ...
Removing 'diversion of /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service to /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd by systemd-shim'
dpkg-divert: error: rename involves overwriting '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service' with
  different file '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd', not allowed
dpkg: error processing package systemd-shim (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 systemd-shim
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2018-06-01
gibsonsimswilson; Hello -

I do not find the package " systemd-shim " in the software repository; so that raises the question of where it originates.
Do we get any hints:
```

apt policy systemd-shim

```
Post back that terminal command and it's output - Between Code Tags .
code tag tutorial:
[http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)

where the suspect is 3rd party software.

[INDENT][INDENT]maybe Yes
[INDENT][INDENT]could be, not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by deadflowr on 2018-06-01
One "solution" I've seen is to move the mentioned file like
```
sudo mv /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.bak
```
then try running the upgrade commands.

reference:
[https://askubuntu.com/questions/838491/systemd-shim-error-after-upgrading-from-16-04-to-16-10]("https://askubuntu.com/questions/838491/systemd-shim-error-after-upgrading-from-16-04-to-16-10")

---

### Post by gibsonsimswilson on 2018-06-02
Here is the output

```
apt policy systemd-shim
systemd-shim:
  Installed: 9-1bzr4ubuntu1
  Candidate: 9-1bzr4ubuntu1
  Version table:
 *** 9-1bzr4ubuntu1 100
        100 /var/lib/dpkg/status
```

---

### Post by monkeybrain20122 on 2018-06-02
Is there any reason why you don't do a clean install?

The first post was posted a day ago. You would have 18.04 up and running 23 3/4 hrs ago if you had backed up your data and did a clean install. But now you are still here waiting for answers to some cryptic outputs.

---

### Post by PaulW2U on 2018-06-02
> **gibsonsimswilson said:**
> Here is the output

```
apt policy systemd-shim
systemd-shim:
  Installed: 9-1bzr4ubuntu1
  Candidate: 9-1bzr4ubuntu1
  Version table:
 *** 9-1bzr4ubuntu1 100
        100 /var/lib/dpkg/status
```
Are you sure you're running Ubuntu 17.10? 

According to the [publishing history]("https://launchpad.net/ubuntu/+source/systemd-shim/+publishinghistory") for that package, systemd-shim was deleted from the Ubuntu archive on 1st June 2016 as it was no longer required. If you are still still seeing it as both installed and as a candidate for installation then there is something very wrong with your system. It seems strange that you're only now seeing this problem.

In any case, as has already been advised,  a clean installation of Ubuntu 18.04 is the easiest way forward.

---

