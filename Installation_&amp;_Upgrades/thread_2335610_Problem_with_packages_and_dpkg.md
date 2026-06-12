---
title: "Problem with packages and dpkg"
date: 2016-08-30
forum: Installation &amp; Upgrades
---

### Post by roddymccoll on 2016-08-30
I have ubuntu 16.04 LTS.
My institution uses Dell KACE for inventory control.

I cannot install the recommended package and what is worse I cannot remove it
so it is effectively impossible to do a software update.

Here is the result of trying to install with dpkg :-

```
root@roddynuc:/home/roddy# dpkg -i ampagent-6.4.522.ubuntu.64.deb
(Reading database ... 205075 files and directories currently installed.)
Preparing to unpack ampagent-6.4.522.ubuntu.64.deb ...
AMPWatchDog: no process found
AMPAgent: no process found
E: 11:10:58 Failed to uninstall service "konea": remove /etc/systemd/system/konea.service: no such file or directory
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: ... it looks like that went OK
Unpacking ampagent (6.4.522-1) over (6.4.522-1) ...
Setting up ampagent (6.4.522-1) ...
insserv: Starting AMPAgentBootup depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting AMPAgentBootup depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting AMPAgentBootup depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service AMPAgentBootup and rc.local if started
insserv: loop involving service rc.local at depth 6
insserv: loop involving service AMPAgentBootup at depth 2
insserv: Starting AMPAgentBootup depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package ampagent (--install):
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
ampagent
```

Here is the result of trying to remove the package :-

```
root@roddynuc:/home/roddy# dpkg -r ampagent
(Reading database ... 205074 files and directories currently installed.)
Removing ampagent (6.4.522-1) ...
AMPWatchDog: no process found
AMPAgent: no process found
E: 11:11:36 Failed to uninstall service "konea": remove /etc/systemd/system/konea.service: no such file or directory
dpkg: error processing package ampagent (--remove):
subprocess installed pre-removal script returned error exit status 1
insserv: Starting AMPAgentBootup depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting AMPAgentBootup depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: Starting AMPAgentBootup depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service AMPAgentBootup and rc.local if started
insserv: loop involving service rc.local at depth 6
insserv: loop involving service AMPAgentBootup at depth 2
insserv: Starting AMPAgentBootup depends on rc.local and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error while cleaning up:
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
ampagent
```

Here is what dpkg thinks of the status of this package now:-

```
root@roddynuc:/home/roddy# dpkg -l ampagent
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name Version Architecture Description
+++-=========================-=================-=================-=======================================================
rF ampagent 6.4.522-1 amd64 Dell KACE Client Management daemon
```

I was not able to find any solutions via google hence my request on this forum.

Any ideas or suggestions or solutions gratefully received!

Thanks
-roddy

[roddy]("http://forums.debian.net/memberlist.php?mode=viewprofile&u=198003") Posts: 1Joined: 2016-08-26 16:14
[LIST]
[*]
[/LIST]
[RIGHT][/RIGHT]

---

