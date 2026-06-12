---
title: "updated to 18.04.1 server, now I see errors about failing to connect to bus"
date: 2018-11-11
forum: Installation &amp; Upgrades
---

### Post by zazcallabah on 2018-11-11
Ok, so this is an upgrade from 16.04.1 LTS to 18.04.1 LTS, the server is headless. After the upgrade is finished, and a reboot is completed, the following happens:

Trying to upgrade packages only results in the following:

```
    ~$ sudo apt upgrade
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    Calculating upgrade... Done
    The following packages will be upgraded:
      policykit-1 screen smartmontools
    3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
    1 not fully installed or removed.
    Need to get 0 B/1,081 kB of archives.
    After this operation, 147 kB of additional disk space will be used.
    Do you want to continue? [Y/n] y
    
    (Reading database ... 159133 files and directories currently installed.)
    Preparing to unpack .../smartmontools_6.5+svn4324-1_amd64.deb ...
    Failed to connect to bus: No such file or directory
    [...]
```

Is it Dbus it is talking about?
Anyway, how about a restore?
```

    ~$ sudo apt update
    Err:1 http://security.ubuntu.com/ubuntu bionic-security InRelease
      Temporary failure resolving 'security.ubuntu.com'
    Err:2 http://se.archive.ubuntu.com/ubuntu bionic InRelease
      Temporary failure resolving 'se.archive.ubuntu.com'
    Err:3 http://se.archive.ubuntu.com/ubuntu bionic-updates InRelease
      Temporary failure resolving 'se.archive.ubuntu.com'
    Err:4 http://se.archive.ubuntu.com/ubuntu bionic-backports InRelease
      Temporary failure resolving 'se.archive.ubuntu.com'
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    1 package can be upgraded. Run 'apt list --upgradable' to see it.
    W: Failed to fetch http://se.archive.ubuntu.com/ubuntu/dists/bionic/InRelease  Temporary failure resolving 'se.archive.ubuntu.com'
    W: Failed to fetch http://se.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease  Temporary failure resolving 'se.archive.ubuntu.com'
    W: Failed to fetch http://se.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease  Temporary failure resolving 'se.archive.ubuntu.com'
    W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease  Temporary failure resolving 'security.ubuntu.com'
    W: Some index files failed to download. They have been ignored, or old ones used instead.

```
What? Is dns broken?
```

    ~$ wget www.google.com
    --2018-11-10 01:55:16--  http://www.google.com/
    Resolving www.google.com (www.google.com)... failed: Temporary failure in name resolution.
    wget: unable to resolve host address ‘www.google.com’

```
Looks like it. Hmm, ifconfig doesn't show dns. Google directs me to this [askubuntu question]("https://stackoverflow.com/questions/50299241/ubuntu-18-04-server-how-to-check-dns-ip-server-setting-being-used") ,  let's try it.
```

    ~$ systemd-resolve --status
    sd_bus_open_system: No such file or directory

```
Ok, I'm more and more lost now. Google now finds this [askubuntu question]("https://askubuntu.com/questions/813588/systemctl-failed-to-connect-to-bus-docker-ubuntu16-04-container"), which is about docker, which is not my case, but also mentions a problem where systemd isnt pid 1:
```

    ~$ ps aux
    USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
    root         1  0.1  0.1 159752  9116 ?        Ss   01:25   0:02 /sbin/init splash nomdmonddf nomdmonisw
    root         2  0.0  0.0      0     0 ?        S    01:25   0:00 [kthreadd]
    root         3  0.0  0.0      0     0 ?        S    01:25   0:00 [ksoftirqd/0]
    root         5  0.0  0.0      0     0 ?        S<   01:25   0:00 [kworker/0:0H]
    root         7  0.0  0.0      0     0 ?        S    01:25   0:00 [rcu_sched]
    root         8  0.0  0.0      0     0 ?        S    01:25   0:00 [rcu_bh]
    root         9  0.0  0.0      0     0 ?        S    01:25   0:00 [migration/0]
    root        10  0.0  0.0      0     0 ?        S    01:25   0:00 [watchdog/0]
    root        11  0.0  0.0      0     0 ?        S    01:25   0:00 [watchdog/1]
    [...]

```
I guess? Is this the root problem, or a symptom? How can I fix this?

---

