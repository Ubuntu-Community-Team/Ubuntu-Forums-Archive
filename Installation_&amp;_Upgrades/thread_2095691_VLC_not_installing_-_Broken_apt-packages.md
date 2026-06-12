---
title: "VLC not installing - Broken apt-packages"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by am6465 on 2012-12-17
Hi all,

Something happened a few weeks ago and my VLC packages was uninstalled. I don't know exactly what caused this but I tried installing libavformat53. Either way, now I'm trying to install vlc again and I get a long string of conflicts and unresolveable dependencies. Here is the terminal output. 

```

**>> sudo apt-get install vlc**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 1.0.6-1ubuntu1.8) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1.0.6-1ubuntu1.8) but it is not going to be installed
E: Broken packages

**>> sudo apt-get install vlc-nox**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc-nox: Depends: libavformat52 (>= 4:0.5.1-1) but it is not going to be installed or
                    libavformat-extra-52 (>= 4:0.5.1-1)
E: Broken packages

**>> sudo apt-get install libavformat52**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libavformat52: Depends: libavcodec-extra-52 (>= 6:0.7.13~) but it is not going to be installed
E: Broken packages

**>> sudo apt-get install libavcodec-extra-52**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libavutil-extra-49 libx264-85 libxvidcore4
Suggested packages:
  libfaad0
The following NEW packages will be installed:
  libavcodec-extra-52 libavutil-extra-49 libx264-85 libxvidcore4
0 upgraded, 4 newly installed, 0 to remove and 3 not upgraded.
Need to get 2,810kB of archives.
After this operation, 7,303kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse libavutil-extra-49 4:0.5.9-0ubuntu0.10.04.1 [74.4kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libx264-85 2:0.85.1448+git1a6d32-4 [244kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid/universe libxvidcore4 2:1.2.2+debian-0ubuntu2 [271kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse libavcodec-extra-52 4:0.5.9-0ubuntu0.10.04.1 [2,221kB]
Fetched 2,810kB in 0s (3,320kB/s)              
Selecting previously deselected package libavutil-extra-49.
(Reading database ... 430564 files and directories currently installed.)
Unpacking libavutil-extra-49 (from .../libavutil-extra-49_4%3a0.5.9-0ubuntu0.10.04.1_amd64.deb) ...
Selecting previously deselected package libx264-85.
Unpacking libx264-85 (from .../libx264-85_2%3a0.85.1448+git1a6d32-4_amd64.deb) ...
Selecting previously deselected package libxvidcore4.
Unpacking libxvidcore4 (from .../libxvidcore4_2%3a1.2.2+debian-0ubuntu2_amd64.deb) ...
Selecting previously deselected package libavcodec-extra-52.
Unpacking libavcodec-extra-52 (from .../libavcodec-extra-52_4%3a0.5.9-0ubuntu0.10.04.1_amd64.deb) ...
Setting up libavutil-extra-49 (4:0.5.9-0ubuntu0.10.04.1) ...

Setting up libx264-85 (2:0.85.1448+git1a6d32-4) ...

Setting up libxvidcore4 (2:1.2.2+debian-0ubuntu2) ...

Setting up libavcodec-extra-52 (4:0.5.9-0ubuntu0.10.04.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

**>>sudo apt-get install libavformat52**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libavformat52: Depends: libavcodec-extra-52 (>= 6:0.7.13~) but 4:0.5.9-0ubuntu0.10.04.1 is to be installed
E: Broken packages

**>>sudo apt-get purge libavcodec52**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libavcodec52 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

**>>sudo apt-get purge libavformat-extra-52**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libavformat-extra-52 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

>> sudo apt-get install libavformat-extra-52
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libavformat-extra-52: Depends: libavformat52 but it is not going to be installed
E: Broken packages

**>>sudo apt-get install libavformat52**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libavformat52: Depends: libavcodec-extra-52 (>= 6:0.7.13~) but 4:0.5.9-0ubuntu0.10.04.1 is to be installed
E: Broken packages

**>>sudo apt-get install libavformat-extra-52**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libavformat-extra-52: Depends: libavformat52 but it is not going to be installed
E: Broken packages

**>>sudo apt-get install libavformat52**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libavformat52: Depends: libavcodec-extra-52 (>= 6:0.7.13~) but 4:0.5.9-0ubuntu0.10.04.1 is to be installed
E: Broken packages


```

I am stuck and I'm working on a project that requires my using VLC. Any ideas? Thanks in advance.

---

### Post by darkod on 2012-12-17
Have you tried fixing any broken packages with:
sudo apt-get install -f

Also, installing VLC from Software Centre? Although software centre will probably give the same errors until they are sorted out.

---

### Post by am6465 on 2012-12-18
> **darkod said:**
> Have you tried fixing any broken packages with:
sudo apt-get install -f

Also, installing VLC from Software Centre? Although software centre will probably give the same errors until they are sorted out.

Yes, same thing happens.

---

### Post by Ozymandias_117 on 2012-12-19
What version of Ubuntu are you running?

Have you enabled any extra repositories/PPAs?

Also please post the output of ```
cat /etc/apt/sources.list
```

---

### Post by am6465 on 2012-12-24
> **Ozymandias_117 said:**
> What version of Ubuntu are you running?

Have you enabled any extra repositories/PPAs?

Also please post the output of ```
cat /etc/apt/sources.list
```

```

# deb cdrom:[Ubuntu-Server 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2)]/ lucid main restricted

# deb cdrom:[Ubuntu-Server 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security multiverse

```

---

### Post by NikTh on 2012-12-24
Hi ,

it would be better if we can see all the software-sources . 

Give the results of the command below 
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```

Thanks

---

### Post by am6465 on 2012-12-26
> **NikTh said:**
> Hi ,

it would be better if we can see all the software-sources . 

Give the results of the command below 
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```

Thanks

```

>>find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list.d/google-talkplugin.list

     1	### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2	# You may comment out this entry, but any other modifications may be lost.
     3	deb http://dl.google.com/linux/talkplugin/deb/ stable main

/etc/apt/sources.list.d/lucid-partner.list

     1	# channel for the lucid (10.04) partner channel
     2	# 
     3	#:description:This channel contains the partner software for lucid
     4	deb http://archive.canonical.com/ubuntu lucid partner

/etc/apt/sources.list.d/dropbox.list

     1	deb http://linux.dropbox.com/ubuntu lucid main

/etc/apt/sources.list.d/jon-severinsson-ffmpeg-lucid.list

     1	deb http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu lucid main

/etc/apt/sources.list.d/google-chrome.list

     1	### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2	# You may comment out this entry, but any other modifications may be lost.
     3	deb http://dl.google.com/linux/chrome/deb/ stable main

/etc/apt/sources.list

     1	# 
     2	# deb cdrom:[Ubuntu-Server 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2)]/ lucid main restricted
     3	
     4	# deb cdrom:[Ubuntu-Server 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2)]/ lucid main restricted
     5	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     6	# newer versions of the distribution.
     7	
     8	deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
     9	deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
    10	
    11	## Major bug fix updates produced after the final release of the
    12	## distribution.
    13	deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
    14	deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
    15	
    16	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17	## team. Also, please note that software in universe WILL NOT receive any
    18	## review or updates from the Ubuntu security team.
    19	deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
    20	deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
    21	deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
    22	deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
    23	
    24	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25	## team, and may not be under a free licence. Please satisfy yourself as to 
    26	## your rights to use the software. Also, please note that software in 
    27	## multiverse WILL NOT receive any review or updates from the Ubuntu
    28	## security team.
    29	deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
    30	deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
    31	deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
    32	deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
    33	
    34	## Uncomment the following two lines to add software from the 'backports'
    35	## repository.
    36	## N.B. software from this repository may not have been tested as
    37	## extensively as that contained in the main release, although it includes
    38	## newer versions of some applications which may provide useful features.
    39	## Also, please note that software in backports WILL NOT receive any review
    40	## or updates from the Ubuntu security team.
    41	# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
    42	# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
    43	
    44	## Uncomment the following two lines to add software from Canonical's
    45	## 'partner' repository.
    46	## This software is not part of Ubuntu, but is offered by Canonical and the
    47	## respective vendors as a service to Ubuntu users.
    48	deb http://archive.canonical.com/ubuntu lucid partner
    49	deb-src http://archive.canonical.com/ubuntu lucid partner
    50	
    51	deb http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted
    52	deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security main restricted
    53	deb http://us.archive.ubuntu.com/ubuntu/ lucid-security universe
    54	deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security universe
    55	deb http://us.archive.ubuntu.com/ubuntu/ lucid-security multiverse
    56	deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-security multiverse



```

---

### Post by fo3 on 2013-01-13
I've got the same problem.  VLC has broken the entire package manager due to what seems to a missing dependancy called libzvbi0.

Trying to install libzvbi0 in the terminal gives me this error:

installArchives() failed: dpkg: error: parsing file '/var/lib/dpkg/status' near line 30124 package 'im-switch':
 duplicate value for `Status' field
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)


Everything is diasabled and nothing else can be installed at the moment, keeps going into repair mode and failing.

Tried cleaning, repairing, purging, disabling some 3rd party repositories etc etc that I've read hre and elsewhere about this problem, but nothing has worked.
eg: sudo apt-get install -f
sudo apt-get --purge remove vlc



If I go into Ubuntu Software Centre, I get an error message saying" Items cannot be installed or removed until the package catalogue is repaired. Do you want to repair it now?"  And it fails to repair.
Error message:
installArchives() failed: dpkg: error: parsing file '/var/lib/dpkg/status' near line 30124 package 'im-switch':
 duplicate value for `Status' field
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)


edit:  Nevermind, it's working now after another reboot.
Running apt-get install -f again found and installed libzvbi0 OK, so problem gone.

---

### Post by darkod on 2013-01-13
Sorry, I'm not an expert to help with this type of errors, but I have VLC Player installed from Software Centre and it installed and is working without any issues.

Just as information. This might be related to some other program/package even though it happens when you try to install vlc. Try googling for any information about that 'im-switch' mentioned. I would focus on that error line.

---

