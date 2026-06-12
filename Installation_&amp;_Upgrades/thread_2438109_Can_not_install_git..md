---
title: "Can not install git."
date: 2020-03-05
forum: Installation &amp; Upgrades
---

### Post by saladavid293 on 2020-03-05
I am trying to install git so I can get kali linux tools. here is the output

root@ubuntu:/home/dbb3881# apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 git : Depends: liberror-perl but it is not installable
E: Unable to correct problems, you have held broken packages.

I haven't installed anything yet expect what you need.

---

### Post by Bashing-om on 2020-03-05
saladavid293; Hello - Welcome to the forum.

 For diagnostic purposes, please post back the outputs of terminal commands:
```

lsb_release -a
sudo apt update
sudo apt upgrade
dpkg -l liberror-perl
apt policy liberror-perl

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]then we look in that horse's mouth[/INDENT]

---

### Post by saladavid293 on 2020-03-05
@bashing-om 
root@ubuntu:/home/dbb3881# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.4 LTS
Release:	18.04
Codename:	bionic

  Could not resolve 'us.archive.ubuntu.com'
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
  Could not resolve 'security.ubuntu.com'
Err:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease
  Could not resolve 'us.archive.ubuntu.com'
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/bionic/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/bionic/InRelease)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease)  Could not resolve 'us.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease](http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease)  Could not resolve 'security.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.



root@ubuntu:/home/dbb3881# sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@ubuntu:/home/dbb3881# dpkg -l liberror-perl
dpkg-query: no packages found matching liberror-perl

root@ubuntu:/home/dbb3881# apt policy liberror-perl
liberror-perl:
  Installed: (none)
  Candidate: (none)
  Version table:

---

### Post by saladavid293 on 2020-03-05
[COLOR=#000000]@bashing-om[/COLOR]
[COLOR=#000000]root@ubuntu:/home/dbb3881# lsb_release -a[/COLOR]
[COLOR=#000000]No LSB modules are available.[/COLOR]
[COLOR=#000000]Distributor ID: Ubuntu[/COLOR]
[COLOR=#000000]Description: Ubuntu 18.04.4 LTS[/COLOR]
[COLOR=#000000]Release: 18.04[/COLOR]
[COLOR=#000000]Codename: bionic[/COLOR]

[COLOR=#000000]Could not resolve 'us.archive.ubuntu.com'[/COLOR]
[COLOR=#000000]Err:2 [/COLOR][http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)[COLOR=#000000] bionic-security InRelease[/COLOR]
[COLOR=#000000]Could not resolve 'security.ubuntu.com'[/COLOR]
[COLOR=#000000]Err:3 [/COLOR][http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)[COLOR=#000000] bionic-updates InRelease[/COLOR]
[COLOR=#000000]Could not resolve 'us.archive.ubuntu.com'[/COLOR]
[COLOR=#000000]Err:4 [/COLOR][http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu)[COLOR=#000000] bionic-backports InRelease[/COLOR]
[COLOR=#000000]Could not resolve 'us.archive.ubuntu.com'[/COLOR]
[COLOR=#000000]Reading package lists... Done[/COLOR]
[COLOR=#000000]Building dependency tree[/COLOR]
[COLOR=#000000]Reading state information... Done[/COLOR]
[COLOR=#000000]All packages are up to date.[/COLOR]
[COLOR=#000000]W: Failed to fetch [/COLOR][http://us.archive.ubuntu.com/ubuntu/...onic/InRelease]("http://us.archive.ubuntu.com/ubuntu/dists/bionic/InRelease")[COLOR=#000000] Could not resolve 'us.archive.ubuntu.com'[/COLOR]
[COLOR=#000000]W: Failed to fetch [/COLOR][http://us.archive.ubuntu.com/ubuntu/...ates/InRelease]("http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease")[COLOR=#000000] Could not resolve 'us.archive.ubuntu.com'[/COLOR]
[COLOR=#000000]W: Failed to fetch [/COLOR][http://us.archive.ubuntu.com/ubuntu/...orts/InRelease]("http://us.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease")[COLOR=#000000] Could not resolve 'us.archive.ubuntu.com'[/COLOR]
[COLOR=#000000]W: Failed to fetch [/COLOR][http://security.ubuntu.com/ubuntu/di...rity/InRelease]("http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease")[COLOR=#000000] Could not resolve 'security.ubuntu.com'[/COLOR]
[COLOR=#000000]W: Some index files failed to download. They have been ignored, or old ones used instead.[/COLOR]



[COLOR=#000000]root@ubuntu:/home/dbb3881# sudo apt upgrade[/COLOR]
[COLOR=#000000]Reading package lists... Done[/COLOR]
[COLOR=#000000]Building dependency tree[/COLOR]
[COLOR=#000000]Reading state information... Done[/COLOR]
[COLOR=#000000]Calculating upgrade... Done[/COLOR]
[COLOR=#000000]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]

[COLOR=#000000]root@ubuntu:/home/dbb3881# dpkg -l liberror-perl[/COLOR]
[COLOR=#000000]dpkg-query: no packages found matching liberror-perl[/COLOR]

[COLOR=#000000]root@ubuntu:/home/dbb3881# apt policy liberror-perl[/COLOR]
[COLOR=#000000]liberror-perl:[/COLOR]
[COLOR=#000000]Installed: (none)[/COLOR]
[COLOR=#000000]Candidate: (none)[/COLOR]
[COLOR=#000000]Version table:[/COLOR]

---

### Post by Bashing-om on 2020-03-05
saladavid293; Huh ?

Are you behind some kind of proxy that blocks access ?

What results:
```

ping -c3 us.archive.ubuntu.com
ping -c3 91.189.91.26

```

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by saladavid293 on 2020-03-05
root@ubuntu:/home/dbb3881# ping -c3 us.archive.ubuntu.com
ping: us.archive.ubuntu.com: Name or service not known

root@ubuntu:/home/dbb3881# ping -c3 91.189.91.26
connect: Network is unreachable

---

### Post by Bashing-om on 2020-03-05
saladavid293; Hokay 1

Proxy ? what on your system is blocking access ?

My results:
> 
sysop@x1804mini:~$ ping -c3 us.archive.ubuntu.com
PING us.archive.ubuntu.com (91.189.91.26) 56(84) bytes of data.
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=1 ttl=52 time=68.6 ms
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=2 ttl=52 time=67.3 ms
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=3 ttl=52 time=65.9 ms

--- us.archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 65.916/67.293/68.661/1.120 ms


sysop@x1804mini:~$ ping -c3 91.189.91.26
PING 91.189.91.26 (91.189.91.26) 56(84) bytes of data.
64 bytes from 91.189.91.26: icmp_seq=1 ttl=52 time=63.2 ms
64 bytes from 91.189.91.26: icmp_seq=2 ttl=52 time=101 ms
64 bytes from 91.189.91.26: icmp_seq=3 ttl=52 time=69.7 ms

--- 91.189.91.26 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 63.275/78.271/101.823/16.861 ms
sysop@x1804mini:~$ 


[INDENT]gots to be a reason
[/INDENT]

---

### Post by saladavid293 on 2020-03-05
>_< I just realized I wasn't connected to the internet. I'm so sorry for wasting your time.

---

### Post by Bashing-om on 2020-03-05
saladavid293' LOL -

Yeah; That will cause it :D

If this matter is now concluded to your satisfaction:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]Up Up and away
[/INDENT][/INDENT]

---

