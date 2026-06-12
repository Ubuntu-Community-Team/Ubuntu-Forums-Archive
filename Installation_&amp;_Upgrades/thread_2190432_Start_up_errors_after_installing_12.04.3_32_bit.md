---
title: "Start up errors after installing 12.04.3 32 bit"
date: 2013-11-27
forum: Installation &amp; Upgrades
---

### Post by patdundee on 2013-11-27
Hi guys
I have just completed a clean install of Ubuntu Server 12.04.3 LTS and i get the following errors on start up in this order

fd0: read error
cannot display analouge
Could not write bytes. Broken Pipe

With the fdo read error it was hanging and not moving on, however after i updated the nvidia driver it moves past this and also past the display error.

I am mainly concerned about the 3rd error Could not write bytes broken pipe.

Has anyone got any ideas or come across this?

Many thanks
P

---

### Post by Bashing-om on 2013-11-27
patdundee; Hi !

1st - Do you really have a floppy disk device installed on that box ? .. if not by all means disable all reference to the floppy drive in bios.

2nd - no idea what "analouge" is refering to (??)
3rd - "Could not write bytes. Broken Pipe" could be from a number of sources; let's put things in context,
Post back -between code tags - the out put of terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```
and see where the package manager points to.

[INDENT]where there are solutions there are no problems
[/INDENT]

---

### Post by patdundee on 2013-11-27
Hi Many thanks for the response. I have actually disabled all drive selections in BIOS that are not used. Only the Hard drives in use and the DVD/CD drives are selected.
Analouge was to do with the monitor and i am sure it is an outdated driver but that one is not a major issue as it is only displaying in SU mode via cmd line

Here is the output from the apt-get update and apt-get upgrade
The sources files would have been written during the fresh install so i would have thought they would all have been correct :) I have also tried with --fix-missing but to no avail.

> apt-get update


Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
  Temporary failure resolving âppa.launchpad.netâ
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
  Temporary failure resolving âsecurity.ubuntu.comâ
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg
  Temporary failure resolving âgb.archive.ubuntu.comâ
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg
  Temporary failure resolving âgb.archive.ubuntu.comâ
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg
  Temporary failure resolving âgb.archive.ubuntu.comâ
Reading package lists... Done
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Temporary failure resolving âgb.archive.ubuntu.comâ


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Temporary failure resolving âgb.archive.ubuntu.comâ


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Temporary failure resolving âgb.archive.ubuntu.comâ


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Temporary failure resolving âsecurity.ubuntu.comâ


W: Failed to fetch [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/precise/Release.gpg](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/precise/Release.gpg)  Temporary failure resolving âppa.launchpad.netâ


W: Some index files failed to download. They have been ignored, or old ones used instead.


apt-get upgrade


Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  libruby1.8
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,787 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main libruby1.8 i386 1.8.7.352-2ubuntu1.4
  Temporary failure resolving âgb.archive.ubuntu.comâ
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main libruby1.8 i386 1.8.7.352-2ubuntu1.4
  Temporary failure resolving âsecurity.ubuntu.comâ
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/ruby1.8/libruby1.8_1.8.7.352-2ubuntu1.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/ruby1.8/libruby1.8_1.8.7.352-2ubuntu1.4_i386.deb)  Temporary failure resolving âsecurity.ubuntu.comâ
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?




---

### Post by Bashing-om on 2013-11-27
patdundee; Well well,

New one on me "Temporary failure resolving âgb.archive.ubuntu.comâ"

Are we looking at a mirror site in Great Britain, as the syntax is strange to me?

But, let us look at the sources list files anyway, just to make sure it is not an error.
-code tag - is the "#" symbol in the tools bar.
```

cat -n /etc/apt/sources.list
ls -la  /etc/apt/sources.list.d/

```

I'll see from here what happens.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by patdundee on 2013-11-27
It is a strange one i have never seen the agb one previously either. You are correct it is a GB repository :)

> cat -n /etc/apt/sources.list
     1  #
     2
     3  # deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release i386                                                                                         (20130820.2)]/ precise main restricted
     4
     5  # deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release i386                                                                                         (20130820.2)]/ precise main restricted
     6
     7  # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade t                                                                                        o
     8  # newer versions of the distribution.
     9  deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
    10  deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
    11
    12  ## Major bug fix updates produced after the final release of the
    13  ## distribution.
    14  deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    15  deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restri                                                                                        cted
    16
    17  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubu                                                                                        ntu
    18  ## team. Also, please note that software in universe WILL NOT receive an                                                                                        y
    19  ## review or updates from the Ubuntu security team.
    20  deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
    21  deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
    22  deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
    23  deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
    24
    25  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubu                                                                                        ntu
    26  ## team, and may not be under a free licence. Please satisfy yourself as                                                                                         to
    27  ## your rights to use the software. Also, please note that software in
    28  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    29  ## security team.
    30  deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
    31  deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
    32  deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    33  deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    34
    35  ## N.B. software from this repository may not have been tested as
    36  ## extensively as that contained in the main release, although it includ                                                                                        es
    37  ## newer versions of some applications which may provide useful features                                                                                        .
    38  ## Also, please note that software in backports WILL NOT receive any rev                                                                                        iew
    39  ## or updates from the Ubuntu security team.
    40  deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restrict                                                                                        ed universe multiverse
    41  deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main rest                                                                                        ricted universe multiverse
    42
    43  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    44  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restrict                                                                                        ed
    45  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    46  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    47  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    48  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    49
    50  ## Uncomment the following two lines to add software from Canonical's
    51  ## 'partner' repository.
    52  ## This software is not part of Ubuntu, but is offered by Canonical and                                                                                         the
    53  ## respective vendors as a service to Ubuntu users.
    54  # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    55  # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    56
    57  ## Uncomment the following two lines to add software from Ubuntu's
    58  ## 'extras' repository.
    59  ## This software is not part of Ubuntu, but is offered by third-party
    60  ## developers who want to ship their latest software.
    61  # deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    62  # deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main




ls -la  /etc/apt/sources.list.d/
total 12
drwxr-xr-x 2 root root 4096 Nov 27 12:13 .
drwxr-xr-x 6 root root 4096 Nov 27 12:13 ..
-rw-r--r-- 1 root root  150 Nov 27 12:13 ubuntu-x-swat-x-updates-precise.list


---

### Post by Bashing-om on 2013-11-27
patdundee; Well,

I also do not see the error yet.
Maybe in "ubuntu-x-swat-x-updates-precise.list" (??)
```

cat /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list

```

[INDENT]we still be looking
[/INDENT]

---

### Post by patdundee on 2013-11-27
Hi Bashing-om
I did say it was a strange one :)
At least the server does start up though after about 2 or 3 minutes. The broken pipe is a concern but it is a process of elimination at the moment. I might rem out the swat-x line and see what happens 
Many thanks
P

---

### Post by Bashing-om on 2013-11-27
patdundee; Hey;

A good puzzle is a matter of entertainment !

The better method to isolate that "broken pipe" is through the package manager.
The package manager is hollering about:
> 
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main libruby1.8 i386 1.8.7.352-2ubuntu1.4
Temporary failure resolving âgb.archive.ubuntu.comâ

However, I am really mystified why "gb.archive.ubuntu.com/ubuntu/ precise-updates/main" is attempting to resolve at "âgb.archive.ubuntu.comâ"...
recon this is an Italian mirror site ? As I can seemingly access the gb. mirror with no problem, presently I have no idea what is transpiring ! 

As indeed the package is valid !
> 
You have searched for packages that names contain ibruby1.8 in suite(s) precise-updates, all sections, and all architectures. Found 2 matching packages.

Package libruby1.8

precise-updates (libs): Libraries necessary to run Ruby 1.8 
1.8.7.352-2ubuntu1.4: amd64 i386


As a thought, how about changing your mirror site and see what results from "update/upgrade" ???

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-11-27
I think the â characters are just a charset conversion artifact - I see them quite often when running PuTTY sessions from Windows with the default ISO-8859-1:1998 (Latin-1, West Europe) translation instead of UTF-8. It's possibly a unicode hyphen (\u2010 = e2 80 90) getting translated as \00e2 (Latin small letter a combining with circumflex)

```

$ echo -e '\u2010'
&#8208;
$ 
$ echo -ne '\u2010' | od -tx1
0000000 e2 80 90
0000003
$ 
$ echo -e '\u00e2'
â

```

---

### Post by Bashing-om on 2013-11-27
@steeldriver; I appreciate the explanation !

Recon the "Temporary failure resolving âgb.archive.ubuntu.comâ" is indeed only temporary, like the mirror is presently updating ??

[INDENT][INDENT]solutions= no problems
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-11-27
I'm not claiming to understand why there are *any* extra characters there though (mistranslated or otherwise)... fwiw the 'Temporary failure resolving' error often just means the network is down I think - I would try pinging gb.archive.ubuntu.com (by name, and then by IP if that doesn't work) if you haven't already done so - are you in the recovery shell btw? if so networking won't be enabled by default

---

### Post by patdundee on 2013-11-27
Hi Guys
The update was not working because for some reason the server had lost its DNS server settings. 
After putting these back it still had issues so i copied a sources file from another server and replaced the existing one. 
The  ubuntu-x-swat-x-updates-precise.list was in the sources.list.d folder so i removed that also 
It is now updating and upgrading and also seems to boot up a lot quicker. I am currently accessing through SSH and am not in front of the screen so I cannot yet see if the pipe issue is resolved. I would think though that as it is rebooting in normal time now (approx 30 seconds) and not taking some 3 minutes that it has also resolved this issue. I will check in a few hours in the morning and will let you know.
Many thanks for the help and advice.

It is strange as this was a clean install from the download of 12.04.3 direct from Ubuntu site as an ISO file 

P

---

### Post by Bashing-om on 2013-11-27
patdundee; Well !

Strange things do happen, but I saw nothing amiss with the original sources.list file, and I was able to access the mirror in question. I will go long with steeldriver and say some where something got xlated - DNS activities (??) .. Will await further advisements. 

@ steeldriver, as always I appreciate your thoughts and it is a pleasure when ya drop in.

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

