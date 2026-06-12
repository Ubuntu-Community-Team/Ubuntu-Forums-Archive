---
title: "update manager fails with sources list error"
date: 2014-05-26
forum: Installation &amp; Upgrades
---

### Post by kmastin on 2014-05-26
Hi all;
I've been having problems with the update manager. It fails to open. After much reasearch, as sudo I've run apt-get update, apt-get upgrade, apt-get clean and apt-get --reinstall install software-center. This is a distribution upgrade from 10.4 to 12.04 a few months back.

A click on the update manager icon still results in nothing and running update-manager in the term spouts out a bunch of Hit and Ign addresses and ends suddenly with:
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

I went to /etc/apt/sources.list to search for duplicares but could find none. I also took a look at /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages but could find no duplicate entries there either. Any ideas?

TIA

---

### Post by Bashing-om on 2014-05-26
kmastin; Hi !

Many times that duplicate entry is in the 3rd party directory " /etc/apt/sources.list.d ".

If you want we can look also and see what we can find. Post back - between code tags to maintain readability - the outputs of the terminal commands:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]and a tale will be told
[/INDENT][/INDENT]

---

### Post by kmastin on 2014-05-26
Bashing-om;
Thanks for the qucik reply
```

keith@keith:~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
     2	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     3	# newer versions of the distribution.
     4	
     5	deb http://archive.ubuntu.com/ubuntu precise main restricted
     6	deb-src http://archive.ubuntu.com/ubuntu precise main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
    11	deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb http://archive.ubuntu.com/ubuntu precise universe
    17	deb-src http://archive.ubuntu.com/ubuntu precise universe
    18	deb http://archive.ubuntu.com/ubuntu precise-updates universe
    19	deb-src http://archive.ubuntu.com/ubuntu precise-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb http://archive.ubuntu.com/ubuntu precise multiverse
    27	deb-src http://archive.ubuntu.com/ubuntu precise multiverse
    28	deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
    29	deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse
    30	
    31	## Uncomment the following two lines to add software from the 'backports'
    32	## repository.
    33	## N.B. software from this repository may not have been tested as
    34	## extensively as that contained in the main release, although it includes
    35	## newer versions of some applications which may provide useful features.
    36	## Also, please note that software in backports WILL NOT receive any review
    37	## or updates from the Ubuntu security team.
    38	# deb http://ca.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
    39	# deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
    40	
    41	## Uncomment the following two lines to add software from Canonical's
    42	## 'partner' repository.
    43	## This software is not part of Ubuntu, but is offered by Canonical and the
    44	## respective vendors as a service to Ubuntu users.
    45	deb http://archive.canonical.com/ubuntu precise partner
    46	# deb-src http://archive.canonical.com/ubuntu lucid partner
    47	
    48	deb http://archive.ubuntu.com/ubuntu precise-security main restricted
    49	deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
    50	deb http://archive.ubuntu.com/ubuntu precise-security universe
    51	deb-src http://archive.ubuntu.com/ubuntu precise-security universe
    52	deb http://archive.ubuntu.com/ubuntu precise-security multiverse
    53	deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

keith@keith:~$ cat /etc/apt/sources.list.d/*.list
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main
# channel for the lucid (10.04) partner channel
# 
#:description:This channel contains the partner software for lucid
deb http://archive.canonical.com/ubuntu precise partner
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

keith@keith:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google-talkplugin.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main


==> /etc/apt/sources.list.d/lucid-partner.list <==
# channel for the lucid (10.04) partner channel
# 
#:description:This channel contains the partner software for lucid
deb http://archive.canonical.com/ubuntu precise partner


==> /etc/apt/sources.list.d/lucid-partner.list.distUpgrade <==
# channel for the lucid (10.04) partner channel
# 
#:description:This channel contains the partner software for lucid
deb http://archive.canonical.com/ubuntu lucid partner


==> /etc/apt/sources.list.d/steam.list <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

```

---

### Post by Bashing-om on 2014-05-26
kmastin; Yeah !

The duplications (2) lie in the /etc/apt/sources.list.d directory.
remove them thusly:
```

sudo rm /etc/apt/sources.list.d/lucid-partner.list
sudo rm /etc/apt/sources.list.d/lucid-partner.list.distUpgrade

```
Now see what the package manager thinks:
```

sudo apt-get update
sudo apt-get upgrade

```

I expect
[INDENT][INDENT][INDENT]all better now
[/INDENT][/INDENT][/INDENT]

---

### Post by kmastin on 2014-05-26
Almost... better though. Still can't get the update manager gui daemon thingy to work, still dies. It should still run on the desktop and say nothing to update. Here's the last bit of the last 2 commands:
```

Fetched 2,452 kB in 4s (503 kB/s)                 
Reading package lists... Done
keith@keith:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  chromium-browser chromium-browser-l10n linux-generic linux-headers-generic linux-headers-generic-pae linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

```

---

### Post by Bashing-om on 2014-05-26
kmastin; Look'n Good !

OK. Let's take care of this little detail:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
"apt-get update" will not install 'new' packages, where as the "dist-upgrade" will. I expect then that 
> 
 chromium-browser chromium-browser-l10n linux-generic linux-headers-generic linux-headers-generic-pae linux-image-generic

will be taken care of.

[INDENT][INDENT]process of learning and it is
[INDENT][INDENT][INDENT]all in knowing how
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kmastin on 2014-05-26
I just rebooted, and still get a system error message and the other numerous pop-ups that accompany it, making this box almost as hard to run as windohs. The details of the error is the Executable Path of /usr/bin/do-release-upgrade. I keep sending the error reports etc., but the pop-ups continue to cycle for quite a while. Maybe this is info I should have mentioned earlier? I just supposed that getting to the root of the problem would be quicker/easier.

---

### Post by kmastin on 2014-05-26
Almost there. After a second reboot, the error messages no longer appear. However, the icon to the update manager is still kaput. If it was only me on this machine, it wouldn't be an issue as I've been running Debian for 10 yrs before I got married and I'm more than comfortable with the command line. My wife also uses this box, and I've been getting others to switch to ubuntu to get them away from the sloppiness of windohs, and if this happens to them they may shy away rather than having me fix something that shouldn't be happening. I guess the question is, what is the main root of the problem and how can I help fix it? BTW, thanks for your generous help so far.

---

### Post by Bashing-om on 2014-05-26
kmastin; Welp;

Problems with the update manager may be unrelated. - needs fix'n never the less.

OK. does the file exist and what are the permissions ?
show:
```

ls -la /usr/bin/do-release-upgrade

```

What options have you enabled in "ubuntu Software Cenrer" as to updates and times and "new release" advisements ? maybe change them around and see what results ?

Can you provide a screen shot of the update manager when it is activated ?

-----------------
We can not show off with a crippled system
[INDENT][INDENT][INDENT]now can we 
[/INDENT][/INDENT][/INDENT]

---

### Post by kmastin on 2014-05-26
This is a screenshot of the software center. I still have no joy with the update manager gui
[ATTACH=CONFIG]253483[/ATTACH]```

-rwxr-xr-x 1 root root 4855 Apr 11 16:11 /usr/bin/do-release-upgrade

```

---

### Post by Bashing-om on 2014-05-26
kmastin; humm,

Looks good to me.
How about see'n what the package manager thinks ? :
```

sudo dpkg --configure update-manager

```

Maybe get a hint of what is not going on.

[INDENT][INDENT]gotta be a cause
[INDENT][INDENT][INDENT]we be look'n
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

