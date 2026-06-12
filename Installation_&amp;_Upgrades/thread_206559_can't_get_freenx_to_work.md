---
title: "can't get freenx to work"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by krisravn on 2006-06-30
I have follow the guide at [http://www.ubuntuforums.org/showthread.php?t=156019&highlight=freenx](http://www.ubuntuforums.org/showthread.php?t=156019&highlight=freenx)
and every things works fine. But then a upgradet to dapper and nothing working anymore. Here is my output from the client, when I try to connect;
```

NX> 203 NXSSH running with pid: 5753
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 86.58.130.187 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: stoffer
NX> 102 Password: 
NX> 103 Welcome to: serv057
stoffer user: stoffer
NX> 105 listsession --user="stoffer" --status="suspended,running" --geometry="1280x1024x24+render" --type="unix-gnome"
NX> 127 Sessions list of user 'stoffer' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: stoffer
NX> 105 startsession --session="test server" --type="unix-gnome" --cache="8M" --images="32M" --cookie="******" --link="lan" --kbtype="pc102/dk" --nodelay="1" --encryption="1" --backingstore="when_requested" --geometry="800x600+240+188" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="800x600x24+render" 

NX> 1000 NXNODE - Version 1.4.0-45-SVN OS (GPL)
NX> 700 Session id: serv057
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: bc53acb04c14b768f5befb0e94361d6b
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: bc53acb04c14b768f5befb0e94361d6b
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 1001 Bye.
NX> 1004 Error: Session did not start.
NX> 504 Session startup failed.
NX> 999 Bye
NX> 280 Ignoring EOF on the monitored channel
NX> 280 Ignoring CLOSE on the monitored channel
Killed by signal 15.

```

Hope someone is able to help, I have struggle with it for a few days now. I have seen a lot of other post, where people says its a problem with the keys and I have try that tutorials, but nothing works :(

Regards
Kristoffer

---

