---
title: "Help Required regarding NIS and NFS setup in Ubuntu 10.04"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by agem.rats on 2010-06-30
[B]Hi all,

I want to setup NIS and NFS in ubuntu 10.04. Can some one tell me how to  set it up.. I am an absolute beginner.

Thanks in advance.. Agem[/B]

---

### Post by Fastjack77 on 2010-07-17
Hi agem.rats,

A quick and tried howto can be found on Ubuntu's 10.04 server guide at [https://help.ubuntu.com/10.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/10.04/serverguide/C/network-file-system.html). Moreover, the following HOWTO is pretty good: [http://ubuntuforums.org/showthread.php?t=249889&highlight=ubuntu+server](http://ubuntuforums.org/showthread.php?t=249889&highlight=ubuntu+server)

Regarding NIS, I am currently considering it myself, but am curious that the most recent documentation I could find was last updated in 2007... Is NIS outdated by a better technology? Most probably, but since I'm new to Linux, I have yet to find something similar (read: provide an environment to the users that make the network transparent, centralized users/passwords, etc.). Still, check out [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo) , [http://www.linux-nis.org/](http://www.linux-nis.org/) , and [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)

Check out "DISCUSSION: NIS vs NIS+ vs LDAP" on unix.derkeiler.com; [http://unix.derkeiler.com/Mailing-Lists/SunManagers/2004-01/0445.html](http://unix.derkeiler.com/Mailing-Lists/SunManagers/2004-01/0445.html) . It seems LDAP took over. I'm curious though, if NIS is still a workable, easy, supported option (especially if only linux workstations are involved.)

---

