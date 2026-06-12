---
title: "Upgraded to 14.04, but can not install libreoffice"
date: 2014-08-19
forum: Installation &amp; Upgrades
---

### Post by srope01 on 2014-08-19
I have upgraded from 12.04 to 14.04 and it more-or-less went without a hitch except that the upgrade stated that the libreoffice-base package was broken. So when everything was finished, I decided to delete libreoffice completely and reinstall. I did the following

```
sudo apt-get install -f
sudo apt-get autoremove
sudo apt-get remove --purge libreoffice-core
```

I had to modify a script according to [these instructions]("http://ubuntuforums.org/showthread.php?t=2239841") to delete libreoffice-base, but I succeeded. Libreoffice appears to be gone... or so I thought. When I go to the Software Centre and try to re-install libreoffice, I get the following message:

```
Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
The following packages have unmet dependencies:


libreoffice: Depends: libreoffice-core (= 1:4.2.4-0ubuntu2) but 1:4.2.4-0ubuntu2 is to be installed

```

Does anyone know what to do next?

---

### Post by Bashing-om on 2014-08-19
srope01; Hi !

Firstly is 'open-office' installed from PPA ? Could be the source of the conflict.
If no other PPA is installed might try the lower level tool 'dpkg'. See how it handles the situation:
```

sudo dpkg --remove --force-remove-reinstreq libreoffice-core

```

Else ->

[INDENT][INDENT][INDENT]a hunt'n we will go
[/INDENT][/INDENT][/INDENT]

---

### Post by srope01 on 2014-08-19
Thanks Bashing-om. I am fairly sure I used only standard sources, but how would I check that?

I tried the dpkg --remove command and all I get is
```
dpkg: warning: ignoring request to remove libreoffice-core which isn't installed
```

I also tried
```
sudo apt-get remove --purge libreoffice*.*

```
and I get the long list and finally
```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I get a fix broken packages error when I tried to install libreoffice using synaptic. 

Any other ideas? I will post logs if needed.

---

### Post by Bashing-om on 2014-08-19
srope01; puzzle'n

Let's work at finding what is:
```

apt-cache policy libreoffice-core
apt-cache policy libreoffice*

```
and maybe from there we can work back.

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by srope01 on 2014-08-19
So here are the results

$ apt-cache policy libreoffice-core
libreoffice-core:
  Installed: (none)
  Candidate: 1:4.2.4-0ubuntu2
  Version table:
     1:4.2.4-0ubuntu2 0
        500 [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main i386 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages


The second command gives a huge amount of output. What I did was to grep for Installed and the output is none installed for every package. I then grepped for 500 and they all point to the same archives. Shall I post the whole output?

---

### Post by Bashing-om on 2014-08-19
srope01; Naww,
If it is not installed, not installed .


OK, let's take a different tack on this.
What is the state of the package manager, and what does it see for problems ?
post back:
```

sudo apt-get -f install
sudo dpkg -C

```

If all comes back clean ->
And then maybe take a poke at installing libre-office .

[INDENT][INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by srope01 on 2014-08-20
OK here are the results.

$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ sudo dpkg -C
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 libjson0:i386        JSON manipulation library (transitional package)


I tried installing libreoffice again using Software Centre. I still get the same ¨Package dependencies cannot be resolved¨ error. When I try it with Synaptic I get ¨Fix broken packages first¨ error.

---

### Post by Bashing-om on 2014-08-20
srope01; Well !

Do not know for sure,yet . But 'libjson0' is the "JSON manipulation library (transitional package) " and I bet that libreoffice also needs it.

Let's follow the package manager's advise and (re-)install 'json0. - it is "Priority: required"
```

sudo apt-get install --reinstall libjson0

```

Let's see how that goes, and then take a poke at libreoffice.

[INDENT][INDENT]our package manager
[INDENT][INDENT][INDENT][INDENT]a wonder to behold
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by srope01 on 2014-08-20
The JSON library is reinstalled.

$ sudo apt-get install --reinstall libjson0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 1,078 B of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates/main libjson0 i386 0.11-3ubuntu1.2 [1,078 B]
Fetched 1,078 B in 0s (14.5 kB/s)
(Reading database ... 578806 files and directories currently installed.)
Preparing to unpack .../libjson0_0.11-3ubuntu1.2_i386.deb ...
Unpacking libjson0:i386 (0.11-3ubuntu1.2) over (0.11-3ubuntu1.2) ...
Setting up libjson0:i386 (0.11-3ubuntu1.2) ...

At least something got fixed! But unfortunately, the same package dependency error occurs when I tried again to install libreoffice.

---

### Post by Bashing-om on 2014-08-20
srope01; Making progress .

OK, show me what you are seeing, so I see the errors and in context where they happen;
Post back the results of:
```

sudo apt-get install -reinstall libreoffice
apt-cache policy libreoffice

```

[INDENT][INDENT][INDENT]see where the trail leads
[/INDENT][/INDENT][/INDENT]

---

### Post by srope01 on 2014-08-20
apt-get gives a bit more info than synaptic or software centre, but not much.

$ sudo apt-get install --reinstall libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libreoffice : Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-core (= 1:4.2.4-0ubuntu2) but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-report-builder-bin but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
               Depends: libreoffice-avmedia-backend-gstreamer but it is not going to be installed
               Depends: python3-uno (>= 4.0~) but it is not going to be installed
               Recommends: libreoffice-gnome but it is not going to be installed or
                           libreoffice-kde but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

$ apt-cache policy libreoffice
libreoffice:
  Installed: (none)
  Candidate: 1:4.2.4-0ubuntu2
  Version table:
     1:4.2.4-0ubuntu2 0
        500 [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates/universe i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe i386 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages

---

### Post by Bashing-om on 2014-08-20
srope01; YUK,

Something installed somewhere the package manager does not want to cope with:
What have you for software 'fetches" ?
post back:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

To rule out one possibility.

[INDENT][INDENT]it don't just happen
[INDENT][INDENT][INDENT]so gotta be a cause
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by srope01 on 2014-08-20
Ah, the changes due to the upgrade to trusty appears.

$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty main restricted
     6	deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    11	deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty universe
    17	deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty universe
    18	deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates universe
    19	deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty multiverse
    27	deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty multiverse
    28	deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    29	deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    37	deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    38	
    39	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    40	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    41	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    42	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    43	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    44	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    51	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    56	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/fingerprint-fingerprint-gui-precise.list <==
# deb [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) trusty main # disabled on upgrade to trusty
# deb-src [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) trusty main # disabled on upgrade to trusty


==> /etc/apt/sources.list.d/fingerprint-fingerprint-gui-precise.list.distUpgrade <==
deb [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) precise main
deb-src [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) precise main


==> /etc/apt/sources.list.d/fingerprint-fingerprint-gui-precise.list.save <==
deb [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) precise main
deb-src [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) precise main


==> /etc/apt/sources.list.d/insync.list <==
# deb [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu) precise main
# deb [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) trusty main # disabled on upgrade to trusty
# deb [http://apt.insynchq.com/ubuntu](http://apt.insynchq.com/ubuntu) trusty non-free # disabled on upgrade to trusty


==> /etc/apt/sources.list.d/insync.list.distUpgrade <==
# deb [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu) precise main
deb [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) precise main
deb [http://apt.insynchq.com/ubuntu](http://apt.insynchq.com/ubuntu) precise non-free


==> /etc/apt/sources.list.d/insync.list.save <==
deb [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu) precise main
deb [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) precise main
deb [http://apt.insynchq.com/ubuntu](http://apt.insynchq.com/ubuntu) precise non-free


==> /etc/apt/sources.list.d/libreoffice-libreoffice-4-0-precise.list <==
# deb [http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu) trusty main # disabled on upgrade to trusty
# deb-src [http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu) trusty main # disabled on upgrade to trusty


==> /etc/apt/sources.list.d/libreoffice-libreoffice-4-0-precise.list.distUpgrade <==
deb [http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu) precise main
deb-src [http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu) precise main


==> /etc/apt/sources.list.d/libreoffice-libreoffice-4-0-precise.list.save <==
deb [http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu) precise main
deb-src [http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu) precise main


==> /etc/apt/sources.list.d/libreoffice-ppa-precise.list <==
# deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main # disabled on upgrade to trusty
# deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main # disabled on upgrade to trusty


==> /etc/apt/sources.list.d/libreoffice-ppa-precise.list.distUpgrade <==
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) precise main


==> /etc/apt/sources.list.d/libreoffice-ppa-precise.list.save <==
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) precise main


==> /etc/apt/sources.list.d/nilarimogard-webupd8-precise.list <==
# deb-src [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) trusty main # disabled on upgrade to trusty


==> /etc/apt/sources.list.d/nilarimogard-webupd8-precise.list.distUpgrade <==
deb-src [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) precise main


==> /etc/apt/sources.list.d/nilarimogard-webupd8-precise.list.save <==
deb-src [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) precise main


==> /etc/apt/sources.list.d/smart.list <==
# deb file:/home/m/Folder/Smart/ stable non-free # disabled on upgrade to trusty


==> /etc/apt/sources.list.d/smart.list.distUpgrade <==
deb file:/home/m/Folder/Smart/ stable non-free


==> /etc/apt/sources.list.d/smart.list.save <==
deb file:/home/m/Folder/Smart/ stable non-free

---

### Post by ajgreeny on 2014-08-20
This is a bug in one of the control files in /var/lib but at the moment I do not have access to everything needed to tell you the details as I am on an android tablet and I have no idea how to copy any text. I will reort back again tomorrow when I am.on a proper computer. Just ignore the broken package till then as it will not stop you using the rest of LO

---

### Post by Bashing-om on 2014-08-20
srope01; Hey hey !

So the source of our problems !
> 

==> /etc/apt/sources.list.d/libreoffice-libreoffice-4-0-precise.list.distUpgrade <==
deb [http://ppa.launchpad.net/libreoffice...ice-4-0/ubuntu](http://ppa.launchpad.net/libreoffice...ice-4-0/ubuntu) precise main
deb-src [http://ppa.launchpad.net/libreoffice...ice-4-0/ubuntu](http://ppa.launchpad.net/libreoffice...ice-4-0/ubuntu) precise main


==> /etc/apt/sources.list.d/libreoffice-libreoffice-4-0-precise.list.save <==
deb [http://ppa.launchpad.net/libreoffice...ice-4-0/ubuntu](http://ppa.launchpad.net/libreoffice...ice-4-0/ubuntu) precise main
deb-src [http://ppa.launchpad.net/libreoffice...ice-4-0/ubuntu](http://ppa.launchpad.net/libreoffice...ice-4-0/ubuntu) precise main


==> /etc/apt/sources.list.d/libreoffice-ppa-precise.list <==
# deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main # disabled on upgrade to trusty
# deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main # disabled on upgrade to trusty


==> /etc/apt/sources.list.d/libreoffice-ppa-precise.list.distUpgrade <==
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) precise main


==> /etc/apt/sources.list.d/libreoffice-ppa-precise.list.save <==
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) precise main


Guess what ? libreofice is not available for 14.04 from the PPA; 
See: [http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu/dists/](http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu/dists/)
There is no listing for 'trusty' . Need to revert this PPA back to what is in the repository. No idea now what the state of libreoffice is and you can bet the system does not know either. BUt,
We can try ! 
With ALL but one of the listings in " /etc/apt/sources.list.d/ " disabled let's try and see what results:
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:launchpad.net/libreoffice

```
If my surmise is correct and there is a positive result from 'ppa-purge' disable this sourcelist now also.
NOW when the sources.list is all cleaned up and all checked out for what is supported in 14.04;
THEN you may 
update the system
upgrade the system
and finally install libreoffice .


AND MORE !

Need to disable all 'precise' repositories, check and see if you want these softwares, and if so. -  IF they are currently available for the 14.04 release.

AND I have no idea what this is ; or what the function is !
> 

==> /etc/apt/sources.list.d/smart.list <==
# deb file:/home/m/Folder/Smart/ stable non-free # disabled on upgrade to trusty


==> /etc/apt/sources.list.d/smart.list.distUpgrade <==
deb file:/home/m/Folder/Smart/ stable non-free


==> /etc/apt/sources.list.d/smart.list.save <==
deb file:/home/m/Folder/Smart/ stable non-free


Get all these 'sources' squared away to something that is now valid for release 14.04
[INDENT][INDENT]all be finer than a frog's hair
[/INDENT][/INDENT]

---

### Post by srope01 on 2014-08-21
Some new packages got installed with the ppa-purge installation.
> $ sudo apt-get install ppa-purge 
...
The following extra packages will be installed:
  aptitude aptitude-common libcwidget3
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
The following NEW packages will be installed:
  aptitude aptitude-common libcwidget3 ppa-purge
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
...

$ sudo ppa-purge ppa:launchpad.net/libreoffice
Updating packages lists
PPA to be removed: launchpad.net libreoffice
Warning:  Could not find package list for PPA: launchpad.net libreoffice


So the latest version of libreoffice is not available for 14.04. I am not sure what to do next as I do not have a clear understanding of the PPA/repository system. Today, I found [this info]("http://askubuntu.com/questions/505368/how-to-update-libreoffice-from-4-2-to-4-3-in-ubuntu-14-04-1-lts") which also mentions that the libreoffice 4.3 packages are not in the repository. So I followed the instructions to just get the 4.3 packages directly.

```
sudo add-apt-repository ppa:libreoffice/libreoffice-4-3
sudo apt-get update
sudo apt-get dist-upgrade
```
A new source list appeared (/etc/apt/sources.list.d/libreoffice-libreoffice-4-3-trusty.list). I then installed libreoffice

```
sudo apt-get install libreoffice
```

Success! OK, I will be stuck on this version of 4.3 until they properly update the repository, but I can live with this for the moment. Many thanks Bashing-om!

Now I gotta figure out what to do with the other 12.04 precise repositories...

---

### Post by ajgreeny on 2014-08-21
LO 4.3 is available from the ppa at [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty) so I am surprised at bashing-om's finding.  I have the ppa enabled on my Xubuntu 14.04 with LO 4.3 running absolutely fine.

There was, however a problem with the recent upgrade details of which are shown at [http://ubuntuforums.org/showthread.php?t=2239916&p=13100243#post13100243](http://ubuntuforums.org/showthread.php?t=2239916&p=13100243#post13100243) and I thought this was the problem you were seeing.

---

### Post by Bashing-om on 2014-08-21
srope01; Hey great !

If ya have additional problems feel free to open a new thread to address the issue.

@ AJ; It really perturbs me when I do make an error.
Basing my judgment for the availability of LO per this site:
[http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu/dists/](http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu/dists/)
I see that last listing for availability as 'raring'.
I ask your guidance on how I should have insured there is in fact a release of LO supporting 14.04 from the information provided by the PPA .
What should I have done different ?

[INDENT][INDENT][INDENT]I hate when that happens
[/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2014-08-21
> **Bashing-om said:**
> srope01; Hey great !

If ya have additional problems feel free to open a new thread to address the issue.

@ AJ; It really perturbs me when I do make an error.
Basing my judgment for the availability of LO per this site:
[http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu/dists/](http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu/dists/)
I see that last listing for availability as 'raring'.
I ask your guidance on how I should have insured there is in fact a release of LO supporting 14.04 from the information provided by the PPA .
What should I have done different ?[INDENT][INDENT][INDENT]I hate when that happens
[/INDENT]
[/INDENT]
[/INDENT]

Go to [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa) and scroll down a little to the drop-down boxes for "Any series" "Filter" and you will see that there are versions for Trusty and Precise.

You were using the ppa at [https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-4-0](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-4-0) which you are correct, does not contain packages for trusty.  However, there are so many different ppa sites for LO's different versions, ie, 4.0, 4.1, 4.2, (though I did not find one specifically for 4.3) that I can understand how it could be so complicated to get the best one.  I think I was just lucky when I stumbled on the one I mention and used.

---

### Post by Bashing-om on 2014-08-21
AJ; Thanks for that.

I do feel somewhat better about that procedure that I employ(ed) .
However, it is flawed !
At this time there are many people who are in a somewhat similar situation of release upgrading with the 3rd party repos left on the system. And yes the installer is "supposed" to disable them, sometimes not. So, the question in my mind is there a better way to determine the availability of that 3rd party software in 14.04 ?
Sometimes a release upgrade does fail as a result of attempting to cope with non-existent software.

A case by case basis, and just bite the bullet and go take the time to extensively check things out ?

Thoughts ?

[INDENT][INDENT]get them
[INDENT][INDENT][INDENT][INDENT]over the hump
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2014-08-21
I have never done a distro upgrade so have no experience of that, nor the possible problems that I might have, and with a clean installation, of course, you have to start again with any ppa repos that you might have used previously, both to find out if they are needed, and to add them again if they are.

Regrettably, I think it really requires a search to find out for all of them if they will still work for a new distro version, but I always do a google search first using either my own custom search engine at google ([https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao](https://www.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao)) or [www.googlubuntu.com](www.googlubuntu.com) with search term "libreoffice ppa" which is how I know there are many LO ppa repos.

---

### Post by Bashing-om on 2014-08-21
AJ; Thanks again for your insights.

Yeah, play each situation we encounter by ear.

[INDENT][INDENT]we do this
[/INDENT][/INDENT]

---

### Post by srope01 on 2014-08-22
I marked the thread as solved. The important lesson for me here is that an upgrade requires carefully managing the PPAs after the upgrade. Next time I will keep track of the repositories. Thanks again for your help.

---

### Post by Bashing-om on 2014-08-22
srope01; Yepper !

Ya got that one.

[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

