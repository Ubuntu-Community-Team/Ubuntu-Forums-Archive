---
title: "removing a partially-installed package"
date: 2017-08-31
forum: Installation &amp; Upgrades
---

### Post by TheHitcher on 2017-08-31
I tried to install google chrome, and even with gdebi it fails, but now everytime i try to update it fails due to this in terminal, ubuntu software etc

running 17.04

i get this error for a normal apt-get upgrade:

```
Processing triggers for man-db (2.7.6.1-2) ...
Setting up google-chrome-stable:i386 (42.0.2311.90-1) ...
xdg-icon-resource: size argument must be numeric
Try 'xdg-icon-resource --help' for more information.
dpkg: error processing package google-chrome-stable:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 google-chrome-stable:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2017-08-31
TheHitcher; Hello;

Google a bit back dropped all support for 32 bit code.

Try and install the 64 bit version ?

[INDENT][INDENT]what can I say else ?
[/INDENT][/INDENT]

---

### Post by TheHitcher on 2017-08-31
Ah that'd explain that!

I still need the 386 version removed to proceed with any additional installs or upgrades though :(

---

### Post by Bashing-om on 2017-08-31
TheHitcher; Hey .

Try:
```

sudo apt --purge autoremove google-chrome-stable

```
If that runs clean we also want to make sure that the sources fetch is also removed prior to any system updates.
Should be in the 3rd party directory .
```

tail -v -n +1 /etc/apt/sources.list.d/*

```

If there one can uncheck the PPA from within software and updates GUI ( one way - else from a text editor ) 

[INDENT][INDENT]maybe Yes
[/INDENT][/INDENT]

---

### Post by TheHitcher on 2017-09-01
Hi Bashing-om, I've tried that already unfortunately, but it seems like everything (even synaptic) can't complete because of the same error as in the original post :(

---

### Post by Bashing-om on 2017-09-01
TheHitcher; Humm ...

Let's see what the package manager does when we remove the PPA .
Post back:
```

tail -v -n +1 /etc/apt/sources.list.d/*
apt policy google-chrome-stable

```
to get the source ID for the ' sudo add-apt-repository -r' command.

[INDENT][INDENT]find a way to-do
[/INDENT][/INDENT]

---

### Post by TheHitcher on 2017-09-01
Here's the output from that:

```
<me>@laptop:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/papirus-ubuntu-papirus-zesty.list <==
deb http://ppa.launchpad.net/papirus/papirus/ubuntu zesty main
# deb-src http://ppa.launchpad.net/papirus/papirus/ubuntu zesty main
<me>@laptop:~$ apt policy google-chrome-stable
google-chrome-stable:i386:
  Installed: 42.0.2311.90-1
  Candidate: 42.0.2311.90-1
  Version table:
 *** 42.0.2311.90-1 100
        100 /var/lib/dpkg/status

```

---

### Post by Bashing-om on 2017-09-01
TheHitcher; Huh ?

Well no google-chrome listing ... strange , is it elsewhere ?

Post :
```

cat -n /etc/apt/sources.list

```

[INDENT][INDENT]gotta - find - a way
[/INDENT][/INDENT]

---

### Post by TheHitcher on 2017-09-01
```
  1	# deb cdrom:[Ubuntu 17.04 _Zesty Zapus_ - Release amd64 (20170412)]/ zesty main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) zesty main restricted
     6	# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) zesty main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) zesty-updates main restricted
    11	# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) zesty-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) zesty universe
    17	# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) zesty universe
    18	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) zesty-updates universe
    19	# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) zesty-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) zesty multiverse
    27	# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) zesty multiverse
    28	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) zesty-updates multiverse
    29	# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) zesty-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) zesty-backports main restricted universe multiverse
    37	# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) zesty-backports main restricted universe multiverse
    38	
    39	## Uncomment the following two lines to add software from Canonical's
    40	## 'partner' repository.
    41	## This software is not part of Ubuntu, but is offered by Canonical and the
    42	## respective vendors as a service to Ubuntu users.
    43	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty partner
    44	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty partner
    45	
    46	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security main restricted
    47	# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security main restricted
    48	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security universe
    49	# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security universe
    50	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security multiverse
    51	# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security multiverse

```

i know it's so awkward not seeing it, it's in a state of limbo!

---

### Post by TheHitcher on 2017-09-01
it was downloaded from the chrome site as a .deb if that helps any?

---

### Post by Bashing-om on 2017-09-01
TheHitcher:Uh Huh / 

> 
it was downloaded from the chrome site as a .deb if that helps any?

Then the package manager should have a track on a .deb .

What shows :
```

dpkg -l google-chrome-stable

```
where when we get the right name, the package manager will deal with it .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by TheHitcher on 2017-09-01
Output below:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
pF  google-chrome- 42.0.2311.90 i386         The web browser from Google

```

---

### Post by Bashing-om on 2017-09-01
TheHitcher; Humm ...

Again, not what I expected, but ---

try:
```

sudo dpkg -P google-chrome

```

Maybe yes
[INDENT][INDENT]could be not so yes
[/INDENT][/INDENT]

---

### Post by TheHitcher on 2017-09-02
sigh!! haha

> dpkg: warning: ignoring request to remove google-chrome which isn't installed


---

### Post by Bashing-om on 2017-09-02
TheHitcher; Well ....

Let's say the name was truncated, and try as:
```

sudo dpkg -P google-chrome-stable

```

[INDENT][INDENT]maybe now ?
[/INDENT][/INDENT]

---

### Post by TheHitcher on 2017-09-04
output:

```
 sudo dpkg -P google-chrome-stable
(Reading database ... 284240 files and directories currently installed.)
Removing google-chrome-stable:i386 (42.0.2311.90-1) ...
xdg-icon-resource: size argument must be numeric
Try 'xdg-icon-resource --help' for more information.
dpkg: error processing package google-chrome-stable:i386 (--purge):
 subprocess installed pre-removal script returned error exit status 1
xdg-icon-resource: size argument must be numeric
Try 'xdg-icon-resource --help' for more information.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 google-chrome-stable:i386

```

---

### Post by Bashing-om on 2017-09-04
TheHitcher; Well;


A new one on me ... See what we can learn.
Take the package manager's advise and have a looksee:
```

xdg-icon-resource --help

```
Points to the icon for google-chrome.
We need now " xdg-icon-resource uninstall [--theme theme] " to find that icon location and name.

Does the Desktop file exist ?
```

 ls -al /home/<username>/Desktop/

```
And did 'dpkg' do something ?
```

dpkg -l | grep -i google-chrome
sudo find / -name "*google-chrome*"

```

[INDENT][INDENT]one of those times
[INDENT][INDENT][INDENT]we just have to find out
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by TheHitcher on 2017-09-11
Hi, i think this may be solved!

i did 

sudo nano /var/lib/dpkg/status

and removed the entry for chrome in there, and did apt-get upgrade, now everything seems to go fine in the terminal when upgrading everything else :)

It's still present as an installed entry in the ubuntu software GUI but I can live with just ignoring that. thanks for all your help :)

---

