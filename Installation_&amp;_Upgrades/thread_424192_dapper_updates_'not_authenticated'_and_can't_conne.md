---
title: "dapper updates 'not authenticated' and can't connect?"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by tparker on 2007-04-26
I am using Dapper LTS amd64 and everything had been fine for about 6 months. I applied each update as I was notified of them with the little desktop icon and had no trouble.

About 6 weeks ago when I clicked the icon and told it to apply the updates it came back telling me that the 'connection failed' when trying to download the packages and I couldn't update. I waited a while and kept trying off and on over a few days. 

About two weeks later some of the packages worked, but some still couldn't connect ( [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) , [http://wine.dedicated.com](http://wine.dedicated.com), [http://security.ubuntu.com](http://security.ubuntu.com), [http://archive.ubuntu.com)](http://archive.ubuntu.com)). 

I waited some more to see if it would start working and now when I try to update I am told that everything is 'not authenticated', I also am told 'not authenticated' for anything I try to install through synaptic. When I try using apt-get to update (with the command sudo apt-get update) it says that it fails to connect to all the servers.

This is my first linux install so I don't know what to tear into on my own to try and fix this. I do know that my internet connection works fine, I can be browsing for fix suggestions at the same time the updates can't connect. I know that my ISP doesn't block any sites and that nothing in my firewall or other configurations has changed since the updates did work. I have not applied or installed anything that came back 'not authenticated'.

Any help is appreciated, thanks.

---

### Post by zvacet on 2007-04-26
```
sudo aptitude update
```

---

### Post by tparker on 2007-04-26
<quote> sudo aptitude update </quote>

Thank you. I just tried that and got all the same failure to connect messages as using apt-get.

---

### Post by hypodermicmd on 2007-04-26
I'm having the same problem with my dist upgrade. It goes well until it tries to connect to us.archive.ubuntu.com. Nothing is able to connect to this server so my upgrade bombs pretty badly. Is there an issue with this server?

---

### Post by zvacet on 2007-04-27
Comment (put # sign in front of line) [http://wine.dedicated.com](http://wine.dedicated.com) and last one.

```
sudo aptitude update
```

---

### Post by tparker on 2007-05-12
Learning more about the package management system let me do a better search which eventually led to a thread that solved the problem for me. (only if you aren't using a proxy for internet)([http://ubuntuforums.org/showthread.php?t=206692&page=2](http://ubuntuforums.org/showthread.php?t=206692&page=2))

Short version:
edit apt.conf and remove the line 'Acquire::http::Proxy "false"', update. 

Longer version for other newbies:
open a terminal and type: cd /etc/apt and hit enter.
type: sudo gedit apt.conf and hit enter, do your password and hit enter.
delete the entire line 'Acquire::http::Proxy "false"', in my case that left the file completely empty.
hit save and close the gedit window.
in the terminal type: sudo apt-get update
let it do it's thing then close the terminal and update as normal using the desktop icon, if it shows you still need updates.

---

