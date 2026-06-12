---
title: "NOOB -please help apt does not have permission to updat or upgrade"
date: 2017-04-02
forum: Installation &amp; Upgrades
---

### Post by wyattlamore on 2017-04-02
Hey guys. I know this is an extremely stupid question. But i have ubuntu 16.04 on a samsung rv515 laptop. Ive had ubuntu, zorinOS, openSUSE, and a few other linux distros on a number of pc's and laptops in the past and have never had a problem updating or upgrading. But for several months now i have been getting errors every time i try using apt. I just tried to ```
sudo apt-get update
``` and this is what i get 

```
sudo: unable to resolve host wyatt-rv515
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

So i ```
ls -lg /var/lib/dpkg/
``` and this is what i get

```
drwxr-xr-x 2 root    4096 Apr  2 13:13 alternatives
-rw-r--r-- 1 root      11 Jun 26  2016 arch
-rw-r--r-- 1 root 2540813 Aug 10  2016 available
-rw-r--r-- 1 root 2538867 Aug 10  2016 available-old
-rw-r--r-- 1 root       8 Jul 22  2014 cmethopt
-rw-r--r-- 1 root    1359 Aug 10  2016 diversions
-rw-r--r-- 1 root    1460 Aug 10  2016 diversions-old
drwxr-xr-x 2 root  581632 Mar 19 22:49 info
-rw-r----- 1 root       0 Apr  2 13:11 lock
drwxr-xr-x 2 root    4096 Mar  7  2014 parts
-rw-r--r-- 1 root     228 Aug 10  2016 statoverride
-rw-r--r-- 1 root     163 Jul 22  2014 statoverride-old
-rw-r--r-- 1 root 3250224 Apr  2 13:13 status
-rw-r--r-- 1 root 3252381 Apr  2 13:11 status-old
drwxr-xr-x 2 root    4096 Apr  2 13:15 triggers
drwxr-xr-x 2 root    4096 Apr  2 13:16 updates
```

The problem is, even after searching on here, on google, and on XDA, i dont understand what any of this means or how to get it working correctly. Could somebody please help me out here. Thanks in advance guys. I really do appreciate it.

---

### Post by Bashing-om on 2017-04-02
wyattlamore; Well ....

Should tell you whats locking dpkg. 
```

sudo lsof /var/lib/dpkg/lock

```
check to make sure you still don't have a package manager running.
```

ps -e | grep apt

```

Depending, maybe we find and remove the lock on dpkg .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by SeijiSensei on 2017-04-02
Take a look at the file /etc/apt/sources.list and see what server it lists.  It sounds like you inadvertently replaced the name of the main repository mirror with "wyatt-rv515".  To fix this, open the GUI software sources app, and follow the "sources" link.  Choose a server near you. (I'm in the Boston area so I use MIT.)  Then try "sudo apt-get update" again.

---

### Post by wyattlamore on 2017-04-02
> **Bashing-om said:**
> wyattlamore; Well ....

Should tell you whats locking dpkg. 
```

sudo lsof /var/lib/dpkg/lock

```
check to make sure you still don't have a package manager running.
```

ps -e | grep apt

```

Depending, maybe we find and remove the lock on dpkg .
[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]



lsof gave me 

```
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME
dpkg    2424 root    3uW  REG    8,2        0 4195445 /var/lib/dpkg/lock
```

And thank you for the reply by the way.

---

### Post by wyattlamore on 2017-04-02
> **wyattlamore said:**
> lsof gave me 

```
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME
dpkg    2424 root    3uW  REG    8,2        0 4195445 /var/lib/dpkg/lock
```

And thank you for the reply by the way.

I just tried the ps command you gave me as well and this is what i got


 ```
 2280 ?        00:00:04 aptd
```

---

### Post by wyattlamore on 2017-04-02
> **SeijiSensei said:**
> Take a look at the file /etc/apt/sources.list and see what server it lists.  It sounds like you inadvertently replaced the name of the main repository mirror with "wyatt-rv515".  To fix this, open the GUI software sources app, and follow the "sources" link.  Choose a server near you. (I'm in the Boston area so I use MIT.)  Then try "sudo apt-get update" again.

Actually the "wyatt-rv515" is something i put in there. The terminal output had my computers name in that portion and i wasn't sure if that was something that needed to be kept private. Sorry. I should have mentioned that in the post.

---

### Post by Bashing-om on 2017-04-02
wyattlamore; K;

We know dpkg has the lock .

In small steps to correct . let us 1st address SeijiSensei's advise as a 1st priority !
post back :
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

``` and we check that your sources are valid .

Then look at :
```

pstree -p -s 2280 2424

```
so we know what we are dealing with here .

Finally we see what we can do about clearing that lock .

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by wyattlamore on 2017-04-02
> **Bashing-om said:**
> wyattlamore; K;

We know dpkg has the lock .

In small steps to correct . let us 1st address SeijiSensei's advise as a 1st priority !
post back :
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

``` and we check that your sources are valid .

Then look at :
```

pstree -p -s 2280 2424

```
so we know what we are dealing with here .

Finally we see what we can do about clearing that lock .
[INDENT][INDENT]just what I think
[/INDENT]
[/INDENT]

Alright, the first two commands gave me

```
rv415-rv515:~$ cat -n /etc/apt/sources.list
     1    deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe #Added by software-properties
     6    
     7    ## Major bug fix updates produced after the final release of the
     8    ## distribution.
     9    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe #Added by software-properties
    10    
    11    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12    ## team. Also, please note that software in universe WILL NOT receive any
    13    ## review or updates from the Ubuntu security team.
    14    deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
    15    deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
    16    
    17    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    18    ## team, and may not be under a free licence. Please satisfy yourself as to 
    19    ## your rights to use the software. Also, please note that software in 
    20    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    21    ## security team.
    22    
    23    ## N.B. software from this repository may not have been tested as
    24    ## extensively as that contained in the main release, although it includes
    25    ## newer versions of some applications which may provide useful features.
    26    ## Also, please note that software in backports WILL NOT receive any review
    27    ## or updates from the Ubuntu security team.
    28    
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-security universe #Added by software-properties
    30    deb http://us.archive.ubuntu.com/ubuntu/ xenial-security universe
    31    
    32    ## Uncomment the following two lines to add software from Canonical's
    33    ## 'partner' repository.
    34    ## This software is not part of Ubuntu, but is offered by Canonical and the
    35    ## respective vendors as a service to Ubuntu users.
    36    deb http://archive.canonical.com/ubuntu trusty partner
    37    deb-src http://archive.canonical.com/ubuntu trusty partner
    38    
    39    # deb-src http://archive.ubuntu.com/ubuntu xenial main
wyatt@gorgoroth-rv415-rv515:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_audacious-themes_ubuntu.list <==
#  deb  https://private-ppa.launchpad.net/commercial-ppa-uploaders/audacious-themes/ubuntu  xenial main #Added by software-center; credentials stored in  /etc/apt/auth.conf disabled on upgrade to xenial

==>  /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_audacious-themes_ubuntu.list.distUpgrade  <==
deb  https://private-ppa.launchpad.net/commercial-ppa-uploaders/audacious-themes/ubuntu  trusty main #Added by software-center; credentials stored in  /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_audacious-themes_ubuntu.list.save <==
#  deb  https://private-ppa.launchpad.net/commercial-ppa-uploaders/audacious-themes/ubuntu  xenial main #Added by software-center; credentials stored in  /etc/apt/auth.conf disabled on upgrade to xenial

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_intellij-idea-ce_ubuntu.list <==
#  deb  https://private-ppa.launchpad.net/commercial-ppa-uploaders/intellij-idea-ce/ubuntu  xenial main #Added by software-center; credentials stored in  /etc/apt/auth.conf disabled on upgrade to xenial

==>  /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_intellij-idea-ce_ubuntu.list.distUpgrade  <==
deb  https://private-ppa.launchpad.net/commercial-ppa-uploaders/intellij-idea-ce/ubuntu  trusty main #Added by software-center; credentials stored in  /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_intellij-idea-ce_ubuntu.list.save <==
#  deb  https://private-ppa.launchpad.net/commercial-ppa-uploaders/intellij-idea-ce/ubuntu  xenial main #Added by software-center; credentials stored in  /etc/apt/auth.conf disabled on upgrade to xenial

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_varicad-viewer_ubuntu.list <==
#  deb  https://private-ppa.launchpad.net/commercial-ppa-uploaders/varicad-viewer/ubuntu  xenial main #Added by software-center; credentials stored in  /etc/apt/auth.conf disabled on upgrade to xenial

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_varicad-viewer_ubuntu.list.distUpgrade <==
deb   https://private-ppa.launchpad.net/commercial-ppa-uploaders/varicad-viewer/ubuntu  trusty main #Added by software-center; credentials stored in  /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_varicad-viewer_ubuntu.list.save <==
#  deb  https://private-ppa.launchpad.net/commercial-ppa-uploaders/varicad-viewer/ubuntu  xenial main #Added by software-center; credentials stored in  /etc/apt/auth.conf disabled on upgrade to xenial
```

and the second one gave this

```

Usage: pstree [ -a ] [ -c ] [ -h | -H PID ] [ -l ] [ -n ] [ -p ] [ -g ] [ -u ]
              [ -A | -G | -U ] [ PID | USER ]
       pstree -V
Display a tree of processes.

  -a, --arguments     show command line arguments
  -A, --ascii         use ASCII line drawing characters
  -c, --compact       don't compact identical subtrees
  -h, --highlight-all highlight current process and its ancestors
  -H PID,
  --highlight-pid=PID highlight this process and its ancestors
  -g, --show-pgids    show process group ids; implies -c
  -G, --vt100         use VT100 line drawing characters
  -l, --long          don't truncate long lines
  -n, --numeric-sort  sort output by PID
  -N type,
  --ns-sort=type      sort by namespace type (ipc, mnt, net, pid, user, uts)
  -p, --show-pids     show PIDs; implies -c
  -s, --show-parents  show parents of the selected process
  -S, --ns-changes    show namespace transitions
  -u, --uid-changes   show uid transitions
  -U, --unicode       use UTF-8 (Unicode) line drawing characters
  -V, --version       display version information
  -Z     show         SELinux security contexts
  PID    start at this PID; default is 1 (init)
  USER   show only trees rooted at processes of this use
```

---

### Post by Bashing-om on 2017-04-02
wyattlamore; well, well.

Sources:
line 1 -  deb cdrom: - : disable it in " software sources"  as there is no need to obtain any softwares from the installer .


pstree: mea cuppa ; can not run 2 PIDs on same command:
run as :
```

pstree -p -s 2280
pstree -p -s 2424

```
providing you have not rebooted the machine since last running " sudo lsof /var/lib/dpkg/lock and ps -e | grep apt". Such that the PIDs have not changed .

where we are looking to apply 'fuser' to remove the lock .

[INDENT][INDENT]which way did he go
[/INDENT][/INDENT]

---

### Post by wyattlamore on 2017-04-03
Hey guys. Sorry I quit replying. I had to run to the hospital. And yes, I powered the computer down so I will have to get you the new PID's next time I reboot it. I don't know if I'll have time to mess with it tonight though. It might be this weekend before I have a chance because I have a lot to do at work this week and won't have much free time.

---

### Post by Bashing-om on 2017-04-03
wyattlamore; K;

We work t your pace :)

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by wyattlamore on 2017-04-03
> **Bashing-om said:**
> wyattlamore; K;

We work t your pace :)

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

Thank you. I really do appreciate all your help!

---

### Post by wyattlamore on 2017-04-07
Hey guys. I just wanted to let you know that i think i may have fixed it with 
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a

i was able to update my computer but im going to wait a day or two before i mark this thread as solved just to be sure i dont run into any problems. Would that be alright?

P.S. thanks for all the help guys. i sincerely appreciate it.

---

### Post by Bashing-om on 2017-04-07
wyattlamore; Great :)

> 
im going to wait a day or two before i mark this thread as solved just to be sure i dont run into any problems. Would that be alright?


Sure - Only you can say when the situation is resolved.

[INDENT][INDENT]you do good work
[/INDENT][/INDENT]

---

