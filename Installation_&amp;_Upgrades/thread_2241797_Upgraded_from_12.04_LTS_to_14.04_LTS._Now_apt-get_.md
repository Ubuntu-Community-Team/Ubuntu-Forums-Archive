---
title: "Upgraded from 12.04 LTS to 14.04 LTS. Now apt-get autoremove won't work"
date: 2014-08-28
forum: Installation &amp; Upgrades
---

### Post by ertrum on 2014-08-28
I upgraded from Ubuntu 12.04 LTS to Ubuntu 14.04 LTS. When I try any apt-get operations I get an error. 
(Apt-get autoremove is a small example, so that's what I give you here.)

Here's the apt-get dialog:
```

sudo apt-get autoremove
Reading package lists... 0%Reading package lists... 100%Reading package lists... Done
Building dependency tree... 0%Building dependency tree... 0%Building dependency tree... 50%Building dependency tree... 50%Building dependency tree... 81%Building dependency tree       
Reading state information... 0%Reading state information... 0%Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 45 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up python-support (1.0.15) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 449, in <module>
    shutil.rmtree(dir)
  File "/usr/lib/python2.7/shutil.py", line 232, in rmtree
    onerror(os.path.islink, path, sys.exc_info())
  File "/usr/lib/python2.7/shutil.py", line 230, in rmtree
    raise OSError("Cannot call rmtree on a symbolic link")
OSError: Cannot call rmtree on a symbolic link
dpkg: error processing package python-support (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-matplotlib:
 python-matplotlib depends on python-support (>= 0.90.0); however:
  Package python-support is not configured yet.

dpkg: error processing package python-matplotlib (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg: dependency problems prevent configuration of pitivi:
 pitivi depends on python-matplotlib; however:
  Package python-matplotlib is not configured yet.

dpkg: error processing package pitivi (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 python-support
 python-matplotlib
 pitivi
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2014-08-28
ertrum; Hi !

I will start this ball rolling, and see where it goes to !

> 
Package python-support is not configured yet.

Per:
```

apt-cache depends python-matplotlib

```
> 
Depends: python-support


What results when we try and (re-)configure python-support ?
```

sudo dpkg-reconfigure python-support

```

Bearing in mind we may see some unexpected results as there is also this advisory:
> 
 File "/usr/lib/python2.7/shutil.py", line 232, in rmtree
    onerror(os.path.islink, path, sys.exc_info())
  File "/usr/lib/python2.7/shutil.py", line 230, in rmtree
    raise OSError("Cannot call rmtree on a symbolic link")
OSError: Cannot call rmtree on a symbolic link
 as presently I do not know what generates that " Python script, ASCII text executable" file.

[INDENT][INDENT]always;
[INDENT][INDENT][INDENT]a process of learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ertrum on 2014-08-29
Little joy:

sudo dpkg-reconfigure python-support
/usr/sbin/dpkg-reconfigure: python-support is broken or not fully installed

---

### Post by Bashing-om on 2014-08-29
ertrum; Hey ;

Not to shabby;
Let's take the hint from the package manager:
```

sudo apt-get install --reinstall python-support

```

---

### Post by ertrum on 2014-08-29
This does not sound promising...


sudo apt-get install --reinstall python-support
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 29 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for python-support:amd64

---

### Post by Bashing-om on 2014-08-29
ertrum; Well, well ;

It do seem curious !
What returns:
```

dpkg -l  python-support
dpkg -L  python-support
apt-cache policy  python-support

```
Then we look at what it will need to install ( and why the package is required to be installed !).

[INDENT][INDENT]done got interesting
[/INDENT][/INDENT]

---

### Post by ertrum on 2014-08-30
This'll wait till Tuesday, what with the weekend, holiday and all

---

### Post by ertrum on 2014-09-02
Here you go:
```

dpkg -l  python-support
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name              Version       Architecture  Description
+++-=================-=============-=============-========================================
iF  python-support    1.0.15        all           automated rebuilding support for Python 
trumbull@allegro (4) => dpkg -L  python-support
/.
/usr
/usr/sbin
/usr/sbin/update-python-modules
/usr/bin
/usr/bin/dh_pysupport
/usr/share
/usr/share/python
/usr/share/python/runtime.d
/usr/share/python/runtime.d/python-support.rtupdate
/usr/share/python/runtime.d/python-support.rtremove
/usr/share/python/runtime.d/python-support.rtinstall
/usr/share/debhelper
/usr/share/debhelper/autoscripts
/usr/share/debhelper/autoscripts/postinst-python-support
/usr/share/debhelper/autoscripts/prerm-python-support
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/python-support
/usr/share/python-support
/usr/share/python-support/python-support.private
/usr/share/python-support/private
/usr/share/python-support/private/pysupport.py
/usr/share/python-support/private/movemodules
/usr/share/python-support/private/parseversions
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/update-python-modules.8.gz
/usr/share/man/man1
/usr/share/man/man1/dh_pysupport.1.gz
/usr/share/doc
/usr/share/doc/python-support
/usr/share/doc/python-support/README.gz
/usr/share/doc/python-support/copyright
/usr/share/doc/python-support/changelog.gz
/usr/lib
/usr/lib/pymodules
/usr/lib/python2.7
/usr/lib/python2.7/dist-packages
/usr/lib/python2.7/dist-packages/python-support.pth
trumbull@allegro (5) => apt-cache policy  python-support
python-support:
  Installed: 1.0.15
  Candidate: 1.0.15
  Version table:
 *** 1.0.15 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Bashing-om on 2014-09-02
ertrum: Hey;

I do not know yet what is going on, but we do know this:
1)
> 
python-matplotlib depends on python-support (>= 0.90.0); however:
  Package python-support is not configured yet.
 where '>=" is greater than or equal to a old version.
2)
We have the package only hal(F) installed:
> 
i[color=red]F[/color]  python-support    1.0.15

3) We know from:
 [http://packages.ubuntu.com/search?keywords=python-support&searchon=names&suite=trusty&section=all](http://packages.ubuntu.com/search?keywords=python-support&searchon=names&suite=trusty&section=all)
that the required version is:
> 
Package python-support

trusty (14.04LTS) (python): automated rebuilding support for Python modules [universe] 
1.0.15: all


SO, as other means have failed, let's try this approach - carefully - !
```

sudo apt-get remove --purge python-support

```observe what the package manager relates
and hopefully we can fix the issue with :
```

sudo apt-get install python-support

```
Else; at least get some additional info as to what is going on that 'python-support' is being withheld.
----------------------------------
EDIT: 2nd thoughts after consideration, a safer approach:
As there is the hint of "python-support (>= 0.90.0)" consider some package is holding to that version.
Let's disable ALL 3rd party sources and then see what the package manager relates:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C

```
--------------------------
[INDENT][INDENT][INDENT]makes sense to me
[/INDENT][/INDENT][/INDENT]

---

### Post by ertrum on 2014-09-03
It looks like that worked - at least apt-get autoremove now runs without complaining.
Thanks for the help!

---

### Post by ertrum on 2014-09-03
I spoke too soon :-(

When I reboot the system after running the updates yesterday, I saw a prompt to send a problem report to ubuntu. (If there was a program named in the prompt, I missed it, sorry). I selected submit problem report and this popped up:
```

"Problem in packagekitd"
Sorry, the program "packagekitd" closed unexpectedly

Your computer does not have enough free memory to automatically analyze the problem and send a report to the developers.

```

Also when I try to run apper, and query for new updates, it complains that there's no network configured despite the network being configured and available.

It's a step forward, but apparently we're not done yet.

---

### Post by ertrum on 2014-09-03
deleted duplicate post

---

### Post by Bashing-om on 2014-09-03
ertrum; Hummm;

Maybe we best check that :
> 
Your computer does not have enough free memory to automatically analyze the problem <snip>


Let's look:
```

free -m
df -h
df -i

```
as not having the memory can and does result in all kinds of problems.

Yeah
[INDENT][INDENT]1 step forward
[INDENT][INDENT][INDENT]and 3 back
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ertrum on 2014-09-03
I appear to have 2GB on this system. I thought I had more memory than that.
I'll boost the memory...

---

### Post by Bashing-om on 2014-09-03
ertrum; Hey;

2 Gigs should be enough for common everyday applications ( though that is the lower limit for a "good" experience). More would for sure be better.

For now check the status of the package manager once more:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C

```

If the package manager is not happy
[INDENT][INDENT][INDENT][INDENT]no one is happy
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ertrum on 2014-09-05
The memory upgrade may not have been necessary, but it sure made for an interesting day or two - the system refused to boot with upgraded memory, and then decided not to boot with the original memory either, just for spite.

The newly replaced system is considerably quicker, and has a sufficient amount of memory (16G)...

We return to the problem at hand.

apt-get update output:
```

sudo apt-get update
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://us.archive.ubuntu.com trusty-updates InRelease
Ign http://archive.canonical.com trusty InRelease
Hit http://us.archive.ubuntu.com trusty Release.gpg
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Get:2 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://archive.canonical.com trusty Release.gpg
Get:3 http://us.archive.ubuntu.com trusty-updates Release [59.7 kB]            
Hit http://archive.canonical.com trusty Release                              
Hit http://us.archive.ubuntu.com trusty/main Sources                     
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Get:4 http://security.ubuntu.com trusty-security Release [59.7 kB]
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                    
Hit http://archive.canonical.com trusty/partner amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://security.ubuntu.com trusty-security/main Sources
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted Sources
Hit http://archive.canonical.com trusty/partner i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://security.ubuntu.com trusty-security/universe Sources
Hit http://security.ubuntu.com trusty-security/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://security.ubuntu.com trusty-security/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://security.ubuntu.com trusty-security/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://security.ubuntu.com trusty-security/universe i386 Packages
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Get:5 http://us.archive.ubuntu.com trusty-updates/main Sources [116 kB]
Get:6 http://us.archive.ubuntu.com trusty-updates/restricted Sources [1,408 B]
Get:7 http://us.archive.ubuntu.com trusty-updates/universe Sources [82.6 kB]   
Ign http://archive.canonical.com trusty/partner Translation-en_US
Ign http://archive.canonical.com trusty/partner Translation-en        
Get:8 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [3,230 B]
Ign http://archive.canonical.com trusty/partner Translation-en_US.utf8
Get:9 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [311 kB]
Get:10 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [5,820 B]
Get:11 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [199 kB]
Get:12 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [8,221 B]
Get:13 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [304 kB]
Get:14 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:15 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [199 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [8,437 B]
Get:17 http://us.archive.ubuntu.com trusty-updates/main Translation-en [138 kB]
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Get:18 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [99.1 kB]
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US.utf8
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US.utf8
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US.utf8
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US.utf8
Fetched 1,602 kB in 5s (296 kB/s)
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ trusty/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ trusty/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```
(I especially like that apt-get tells me to run update while I'm running update, but no matter)
apt-get upgrade gives:
```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

apt-get -f install gives:
```

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

Finally, dpkg -C gives
```

sudo dpkg -C
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 dhcp3-client         ISC DHCP server (transitional package)
 libjson0:amd64       JSON manipulation library (transitional package)
 dhcp3-common         ISC DHCP common files (transitional package)

```

(I don't use DHCP on this system. I would be completely OK with losing the dchp filesets if that would help)

---

### Post by Bashing-om on 2014-09-05
ertrum; Well, Not too shabby.

Let's take these issues one at a time - as that is all me little mind can cope with -
Let's get the source list file corrected ( W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty/partner ):
That duplication can exist on 1 or either of two places: Let's look at both:
Post back the outputs of terminal commands
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

``` We knock this little matter out, and 
deal with the equally small "3 not upgraded." and the hopefully small " they need to be reinstalled ".

[INDENT][INDENT]one thing at a time.
[INDENT][INDENT][INDENT][INDENT]we getter done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ertrum on 2014-09-08
sources.list:
```

     1  # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
     2  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     3  # newer versions of the distribution.
     4
     5  deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     6  deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     7
     8  ## Major bug fix updates produced after the final release of the
     9  ## distribution.
    10  deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11  deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12
    13  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14  ## team. Also, please note that software in universe WILL NOT receive any
    15  ## review or updates from the Ubuntu security team.
    16  deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
    17  deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
    18  deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19  deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    20
    21  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22  ## team, and may not be under a free licence. Please satisfy yourself as to 
    23  ## your rights to use the software. Also, please note that software in 
    24  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25  ## security team.
    26  deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    27  deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    28  deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29  deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    30
    31  ## Uncomment the following two lines to add software from the 'backports'
    32  ## repository.
    33  ## N.B. software from this repository may not have been tested as
    34  ## extensively as that contained in the main release, although it includes
    35  ## newer versions of some applications which may provide useful features.
    36  ## Also, please note that software in backports WILL NOT receive any review
    37  ## or updates from the Ubuntu security team.
    38  # deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
    39  # deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
    40
    41  ## Uncomment the following two lines to add software from Canonical's
    42  ## 'partner' repository.
    43  ## This software is not part of Ubuntu, but is offered by Canonical and the
    44  ## respective vendors as a service to Ubuntu users.
    45  # deb http://archive.canonical.com/ubuntu karmic partner
    46  # deb-src http://archive.canonical.com/ubuntu karmic partner
    47
    48  deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    49  deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    50  deb http://security.ubuntu.com/ubuntu trusty-security universe
    51  deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    52  deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    53  deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    54
    55  ## Added to get xmms -- ert 01jun2010
    56  # deb http://www.pvv.ntnu.no/~knuta/xmms/karmic ./ # disabled on upgrade to precise
    57  # deb-src http://www.pvv.ntnu.no/~knuta/xmms/karmic ./ # disabled on upgrade to precise
    58

```
tail -v -n +1 /etc/apt/sources.list.d/*:
```

==> /etc/apt/sources.list.d/karmic-partner.list <==
# channel for the karmic (9.10) partner channel
# 
#:description:This channel contains the partner software for karmic
deb http://archive.canonical.com/ubuntu trusty partner

==> /etc/apt/sources.list.d/karmic-partner.list.distUpgrade <==
# channel for the karmic (9.10) partner channel
# 
#:description:This channel contains the partner software for karmic
deb http://archive.canonical.com/ubuntu precise partner

==> /etc/apt/sources.list.d/lucid-partner.list <==
# channel for the karmic (10.04) partner channel
# 
#:description:This channel contains the partner software for karmic
deb http://archive.canonical.com/ubuntu trusty partner

==> /etc/apt/sources.list.d/lucid-partner.list.distUpgrade <==
# channel for the karmic (10.04) partner channel
# 
#:description:This channel contains the partner software for karmic
deb http://archive.canonical.com/ubuntu precise partner

```

---

### Post by Bashing-om on 2014-09-08
ertrum; Hello ;

I see you have been working on the source.list file.
To put things to right I would:
remove all the entries in that 3rd party directory where the current duplication exists of "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner"  there in "/etc/apt/sources.list.d" ; and I suggest activating that source from the "etc/apt/sources.list" file.
As an example to remove the files:
```

sudo rm /etc/apt/sources.list.d/karmic-partner.list
sudo rm /etc/apt/sources.list.d/karmic-partner.list.distUpgrade

```
Removing every file in the directory.

There is this in the "/etc/apt/sources.list"file:
> 
45  # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
46  # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

remove the comment (#) character at the start of lines to enable the source and change "karmic" to "trusty"

Now lets see if the 1st little thing is taken care of:
```

sudo apt-get update
sudo apt-get upgrade

```
If that runs clean we can proceed to the next item on the list.
[INDENT][INDENT]one thing at a time
[INDENT][INDENT][INDENT]we will get there
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ertrum on 2014-09-08
"I see you have been working on the source.list file." 
I think I tried changing some entries in it about four years ago, but I've left it alone since.

Here's apt-get update output:
```

sudo apt-get update
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://us.archive.ubuntu.com trusty-updates InRelease
Ign http://security.ubuntu.com trusty-security InRelease
Hit http://us.archive.ubuntu.com trusty Release.gpg
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Get:2 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Hit http://us.archive.ubuntu.com trusty Release                                
Get:3 http://security.ubuntu.com trusty-security Release [59.7 kB]             
Ign http://archive.canonical.com trusty InRelease                            
Get:4 http://us.archive.ubuntu.com trusty-updates Release [59.7 kB]
Hit http://us.archive.ubuntu.com trusty/main Sources                          
Hit http://archive.canonical.com trusty Release.gpg                   
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Get:5 http://security.ubuntu.com trusty-security/main Sources [43.4 kB]
Hit http://archive.canonical.com trusty Release                               
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Get:6 http://archive.canonical.com trusty/partner Sources [7,010 B]            
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Get:7 http://security.ubuntu.com trusty-security/restricted Sources [14 B]     
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Get:8 http://security.ubuntu.com trusty-security/universe Sources [10.8 kB]
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en     
Get:9 http://security.ubuntu.com trusty-security/multiverse Sources [699 B]
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en     
Get:10 http://security.ubuntu.com trusty-security/main amd64 Packages [136 kB]
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Get:11 http://us.archive.ubuntu.com trusty-updates/main Sources [116 kB]       
Get:12 http://us.archive.ubuntu.com trusty-updates/restricted Sources [1,408 B]
Get:13 http://us.archive.ubuntu.com trusty-updates/universe Sources [82.7 kB]  
Get:14 http://security.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Get:15 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [3,230 B]
Get:16 http://security.ubuntu.com trusty-security/universe amd64 Packages [47.1 kB]
Get:17 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [311 kB]
Get:18 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [1,154 B]
Get:19 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [5,820 B]
Get:20 http://security.ubuntu.com trusty-security/main i386 Packages [132 kB]  
Get:21 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [199 kB]
Get:22 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [8,221 B]
Get:23 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [303 kB] 
Get:24 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:25 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:26 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [199 kB]
Get:27 http://security.ubuntu.com trusty-security/universe i386 Packages [47.2 kB]
Get:28 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,398 B]
Get:29 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [8,437 B]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://security.ubuntu.com trusty-security/main Translation-en    
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Ign http://archive.canonical.com trusty/partner Translation-en_US
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://archive.canonical.com trusty/partner Translation-en
Ign http://archive.canonical.com trusty/partner Translation-en_US.utf8
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US.utf8
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US.utf8
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US.utf8
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US.utf8
Fetched 1,792 kB in 4s (418 kB/s)
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ trusty/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ trusty/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

And apt-get upgrade:
```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common cups-core-drivers cups-daemon
  cups-ppdc cups-server-common freespacenotifier kde-style-oxygen
  kde-window-manager kde-window-manager-common kde-workspace kde-workspace-bin
  kde-workspace-data kde-workspace-kgreet-plugins kdebase-workspace-bin
  kinfocenter klipper kmenuedit ksysguard ksysguardd libcups2 libcupscgi1
  libcupsimage2 libcupsmime1 libcupsppdc1 libkdecorations4abi1 libkephal4abi1
  libkscreensaver5 libksgrd4 libksignalplotter4 libkwineffects1abi4
  libkwinglesutils1 libkwinglutils1abi3 libkworkspace4abi2
  libplasma-geolocation-interface4 libplasmaclock4abi4 libplasmagenericshell4
  libprocesscore4abi1 libprocessui4a libtaskmanager4abi5 libweather-ion6
  plasma-dataengines-workspace plasma-desktop plasma-widgets-workspace
  systemsettings
47 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 16.0 MB of archives.
After this operation, 18.4 kB of additional disk space will be used.
Do you want to continue? [Y/n] y      
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main cups-server-common all 1.7.2-0ubuntu1.2 [513 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libcupsmime1 amd64 1.7.2-0ubuntu1.2 [12.1 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main cups-core-drivers amd64 1.7.2-0ubuntu1.2 [25.7 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libcupscgi1 amd64 1.7.2-0ubuntu1.2 [26.2 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libcupsimage2 amd64 1.7.2-0ubuntu1.2 [15.3 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libcupsppdc1 amd64 1.7.2-0ubuntu1.2 [44.0 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main cups-common all 1.7.2-0ubuntu1.2 [160 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main cups-bsd amd64 1.7.2-0ubuntu1.2 [26.6 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main cups-client amd64 1.7.2-0ubuntu1.2 [195 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main cups-ppdc amd64 1.7.2-0ubuntu1.2 [25.4 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main cups-daemon amd64 1.7.2-0ubuntu1.2 [268 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libcups2 amd64 1.7.2-0ubuntu1.2 [179 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main cups amd64 1.7.2-0ubuntu1.2 [185 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe freespacenotifier amd64 4:4.11.11-0ubuntu0.1 [36.0 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe kinfocenter amd64 4:4.11.11-0ubuntu0.1 [483 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe systemsettings amd64 4:4.11.11-0ubuntu0.1 [235 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe kde-window-manager amd64 4:4.11.11-0ubuntu0.1 [964 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe plasma-desktop amd64 4:4.11.11-0ubuntu0.1 [1,154 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe plasma-widgets-workspace amd64 4:4.11.11-0ubuntu0.1 [438 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe plasma-dataengines-workspace amd64 4:4.11.11-0ubuntu0.1 [554 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe kde-workspace-bin amd64 4:4.11.11-0ubuntu0.1 [1,887 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe kde-window-manager-common amd64 4:4.11.11-0ubuntu0.1 [1,680 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libkdecorations4abi1 amd64 4:4.11.11-0ubuntu0.1 [50.6 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libkwineffects1abi4 amd64 4:4.11.11-0ubuntu0.1 [74.1 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libkwinglesutils1 amd64 4:4.11.11-0ubuntu0.1 [66.5 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libkwinglutils1abi3 amd64 4:4.11.11-0ubuntu0.1 [79.7 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libkephal4abi1 amd64 4:4.11.11-0ubuntu0.1 [23.3 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libplasmagenericshell4 amd64 4:4.11.11-0ubuntu0.1 [295 kB]
Get:29 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libplasmaclock4abi4 amd64 4:4.11.11-0ubuntu0.1 [75.6 kB]
Get:30 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe ksysguard amd64 4:4.11.11-0ubuntu0.1 [212 kB]
Get:31 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libksignalplotter4 amd64 4:4.11.11-0ubuntu0.1 [42.2 kB]
Get:32 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libprocessui4a amd64 4:4.11.11-0ubuntu0.1 [90.5 kB]
Get:33 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libtaskmanager4abi5 amd64 4:4.11.11-0ubuntu0.1 [136 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libprocesscore4abi1 amd64 4:4.11.11-0ubuntu0.1 [43.2 kB]
Get:35 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe ksysguardd amd64 4:4.11.11-0ubuntu0.1 [61.3 kB]
Get:36 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libksgrd4 amd64 4:4.11.11-0ubuntu0.1 [38.7 kB]
Get:37 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libplasma-geolocation-interface4 amd64 4:4.11.11-0ubuntu0.1 [21.3 kB]
Get:38 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libweather-ion6 amd64 4:4.11.11-0ubuntu0.1 [20.9 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libkworkspace4abi2 amd64 4:4.11.11-0ubuntu0.1 [57.5 kB]
Get:40 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libkscreensaver5 amd64 4:4.11.11-0ubuntu0.1 [24.7 kB]
Get:41 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe kde-workspace-data all 4:4.11.11-0ubuntu0.1 [4,680 kB]
Get:42 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe kde-workspace-kgreet-plugins amd64 4:4.11.11-0ubuntu0.1 [38.4 kB]
Get:43 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe kde-style-oxygen amd64 4:4.11.11-0ubuntu0.1 [305 kB]
Get:44 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe klipper amd64 4:4.11.11-0ubuntu0.1 [101 kB]
Get:45 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe kde-workspace all 4:4.11.11-0ubuntu0.1 [15.7 kB]
Get:46 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe kmenuedit amd64 4:4.11.11-0ubuntu0.1 [301 kB]
Get:47 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe kdebase-workspace-bin all 4:4.11.11-0ubuntu0.1 [13.9 kB]
Fetched 16.0 MB in 7s (2,069 kB/s)                                             
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 565793 files and directories currently installed.)
Preparing to unpack .../cups-server-common_1.7.2-0ubuntu1.2_all.deb ...
Unpacking cups-server-common (1.7.2-0ubuntu1.2) over (1.7.2-0ubuntu1.1) ...
Preparing to unpack .../libcupsmime1_1.7.2-0ubuntu1.2_amd64.deb ...
Unpacking libcupsmime1:amd64 (1.7.2-0ubuntu1.2) over (1.7.2-0ubuntu1.1) ...
Preparing to unpack .../cups-core-drivers_1.7.2-0ubuntu1.2_amd64.deb ...
Unpacking cups-core-drivers (1.7.2-0ubuntu1.2) over (1.7.2-0ubuntu1.1) ...
Preparing to unpack .../libcupscgi1_1.7.2-0ubuntu1.2_amd64.deb ...
Unpacking libcupscgi1:amd64 (1.7.2-0ubuntu1.2) over (1.7.2-0ubuntu1.1) ...
Preparing to unpack .../libcupsimage2_1.7.2-0ubuntu1.2_amd64.deb ...
Unpacking libcupsimage2:amd64 (1.7.2-0ubuntu1.2) over (1.7.2-0ubuntu1.1) ...
Preparing to unpack .../libcupsppdc1_1.7.2-0ubuntu1.2_amd64.deb ...
Unpacking libcupsppdc1:amd64 (1.7.2-0ubuntu1.2) over (1.7.2-0ubuntu1.1) ...
Preparing to unpack .../cups-common_1.7.2-0ubuntu1.2_all.deb ...
Unpacking cups-common (1.7.2-0ubuntu1.2) over (1.7.2-0ubuntu1.1) ...
Preparing to unpack .../cups-bsd_1.7.2-0ubuntu1.2_amd64.deb ...
Unpacking cups-bsd (1.7.2-0ubuntu1.2) over (1.7.2-0ubuntu1.1) ...
Preparing to unpack .../cups-client_1.7.2-0ubuntu1.2_amd64.deb ...
Unpacking cups-client (1.7.2-0ubuntu1.2) over (1.7.2-0ubuntu1.1) ...
Preparing to unpack .../cups-ppdc_1.7.2-0ubuntu1.2_amd64.deb ...
Unpacking cups-ppdc (1.7.2-0ubuntu1.2) over (1.7.2-0ubuntu1.1) ...
Preparing to unpack .../cups-daemon_1.7.2-0ubuntu1.2_amd64.deb ...
cups stop/waiting
Unpacking cups-daemon (1.7.2-0ubuntu1.2) over (1.7.2-0ubuntu1.1) ...
Preparing to unpack .../libcups2_1.7.2-0ubuntu1.2_amd64.deb ...
Unpacking libcups2:amd64 (1.7.2-0ubuntu1.2) over (1.7.2-0ubuntu1.1) ...
Preparing to unpack .../cups_1.7.2-0ubuntu1.2_amd64.deb ...
Unpacking cups (1.7.2-0ubuntu1.2) over (1.7.2-0ubuntu1.1) ...
Preparing to unpack .../freespacenotifier_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking freespacenotifier (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../kinfocenter_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking kinfocenter (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...     
Preparing to unpack .../systemsettings_4%3a4.11.11-0ubuntu0.1_amd64.deb ...      
Unpacking systemsettings (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...  
Preparing to unpack .../kde-window-manager_4%3a4.11.11-0ubuntu0.1_amd64.deb ...  
Unpacking kde-window-manager (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...                                                                               
Preparing to unpack .../plasma-desktop_4%3a4.11.11-0ubuntu0.1_amd64.deb ...      
Unpacking plasma-desktop (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...  
Preparing to unpack .../plasma-widgets-workspace_4%3a4.11.11-0ubuntu0.1_amd64.deb ...                                                                             
Unpacking plasma-widgets-workspace (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...                                                                         
Preparing to unpack .../plasma-dataengines-workspace_4%3a4.11.11-0ubuntu0.1_amd64.deb ...                                                                         
Unpacking plasma-dataengines-workspace (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...                                                                     
Preparing to unpack .../kde-workspace-bin_4%3a4.11.11-0ubuntu0.1_amd64.deb ...   
Unpacking kde-workspace-bin (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...                                                                                
Preparing to unpack .../kde-window-manager-common_4%3a4.11.11-0ubuntu0.1_amd64.deb ...                                                                            
Unpacking kde-window-manager-common (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...                                                                        
Preparing to unpack .../libkdecorations4abi1_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking libkdecorations4abi1 (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...                                                                             
Preparing to unpack .../libkwineffects1abi4_4%3a4.11.11-0ubuntu0.1_amd64.deb ... 
Unpacking libkwineffects1abi4 (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...                                                                              
Preparing to unpack .../libkwinglesutils1_4%3a4.11.11-0ubuntu0.1_amd64.deb ...   
Unpacking libkwinglesutils1 (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../libkwinglutils1abi3_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking libkwinglutils1abi3 (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../libkephal4abi1_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking libkephal4abi1 (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../libplasmagenericshell4_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking libplasmagenericshell4 (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../libplasmaclock4abi4_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking libplasmaclock4abi4 (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../ksysguard_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking ksysguard (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../libksignalplotter4_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking libksignalplotter4 (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../libprocessui4a_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking libprocessui4a (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../libtaskmanager4abi5_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking libtaskmanager4abi5 (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../libprocesscore4abi1_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking libprocesscore4abi1 (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../ksysguardd_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking ksysguardd (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../libksgrd4_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking libksgrd4 (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../libplasma-geolocation-interface4_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking libplasma-geolocation-interface4 (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../libweather-ion6_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking libweather-ion6 (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../libkworkspace4abi2_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking libkworkspace4abi2 (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../libkscreensaver5_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking libkscreensaver5 (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../kde-workspace-data_4%3a4.11.11-0ubuntu0.1_all.deb ...
Unpacking kde-workspace-data (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../kde-workspace-kgreet-plugins_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking kde-workspace-kgreet-plugins (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../kde-style-oxygen_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking kde-style-oxygen (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../klipper_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking klipper (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../kde-workspace_4%3a4.11.11-0ubuntu0.1_all.deb ...
Unpacking kde-workspace (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../kmenuedit_4%3a4.11.11-0ubuntu0.1_amd64.deb ...
Unpacking kmenuedit (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Preparing to unpack .../kdebase-workspace-bin_4%3a4.11.11-0ubuntu0.1_all.deb ...
Unpacking kdebase-workspace-bin (4:4.11.11-0ubuntu0.1) over (4:4.11.10-0ubuntu0.1) ...
Processing triggers for doc-base (0.10.5) ...
Processing 1 changed doc-base file...
Registering documents with scrollkeeper...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw (0.34~rc-0ubuntu2) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Setting up cups-server-common (1.7.2-0ubuntu1.2) ...
Setting up libcups2:amd64 (1.7.2-0ubuntu1.2) ...
Setting up libcupsmime1:amd64 (1.7.2-0ubuntu1.2) ...
Setting up cups-daemon (1.7.2-0ubuntu1.2) ...
cups start/running, process 15174
Setting up cups-core-drivers (1.7.2-0ubuntu1.2) ...
Setting up libcupscgi1:amd64 (1.7.2-0ubuntu1.2) ...
Setting up libcupsimage2:amd64 (1.7.2-0ubuntu1.2) ...
Setting up libcupsppdc1:amd64 (1.7.2-0ubuntu1.2) ...
Setting up cups-common (1.7.2-0ubuntu1.2) ...
Setting up cups-client (1.7.2-0ubuntu1.2) ...
Setting up cups-bsd (1.7.2-0ubuntu1.2) ...
Setting up cups-ppdc (1.7.2-0ubuntu1.2) ...
Setting up cups (1.7.2-0ubuntu1.2) ...
Updating PPD files for cups ...
Setting up freespacenotifier (4:4.11.11-0ubuntu0.1) ...
Setting up kinfocenter (4:4.11.11-0ubuntu0.1) ...
Setting up libkdecorations4abi1 (4:4.11.11-0ubuntu0.1) ...
Setting up systemsettings (4:4.11.11-0ubuntu0.1) ...
Setting up libkwineffects1abi4 (4:4.11.11-0ubuntu0.1) ...
Setting up libkwinglesutils1 (4:4.11.11-0ubuntu0.1) ...
Setting up libkwinglutils1abi3 (4:4.11.11-0ubuntu0.1) ...
Setting up kde-style-oxygen (4:4.11.11-0ubuntu0.1) ...
Setting up libkworkspace4abi2 (4:4.11.11-0ubuntu0.1) ...
Setting up kde-window-manager-common (4:4.11.11-0ubuntu0.1) ...
Setting up kde-window-manager (4:4.11.11-0ubuntu0.1) ...
Setting up libkephal4abi1 (4:4.11.11-0ubuntu0.1) ...
Setting up libplasmagenericshell4 (4:4.11.11-0ubuntu0.1) ...
Setting up libprocesscore4abi1 (4:4.11.11-0ubuntu0.1) ...
Setting up libtaskmanager4abi5 (4:4.11.11-0ubuntu0.1) ...
Setting up libplasmaclock4abi4 (4:4.11.11-0ubuntu0.1) ...
Setting up libksgrd4 (4:4.11.11-0ubuntu0.1) ...
Setting up libplasma-geolocation-interface4 (4:4.11.11-0ubuntu0.1) ...
Setting up libweather-ion6 (4:4.11.11-0ubuntu0.1) ...
Setting up plasma-dataengines-workspace (4:4.11.11-0ubuntu0.1) ...
Setting up plasma-widgets-workspace (4:4.11.11-0ubuntu0.1) ...
Setting up plasma-desktop (4:4.11.11-0ubuntu0.1) ...
Setting up libkscreensaver5 (4:4.11.11-0ubuntu0.1) ...
Setting up libprocessui4a (4:4.11.11-0ubuntu0.1) ...
Setting up kde-workspace-data (4:4.11.11-0ubuntu0.1) ...
Setting up kde-workspace-kgreet-plugins (4:4.11.11-0ubuntu0.1) ...
Setting up kde-workspace-bin (4:4.11.11-0ubuntu0.1) ...
Setting up libksignalplotter4 (4:4.11.11-0ubuntu0.1) ...
Setting up ksysguardd (4:4.11.11-0ubuntu0.1) ...
Setting up ksysguard (4:4.11.11-0ubuntu0.1) ...
Setting up klipper (4:4.11.11-0ubuntu0.1) ...
Setting up kde-workspace (4:4.11.11-0ubuntu0.1) ...
Setting up kmenuedit (4:4.11.11-0ubuntu0.1) ...
Setting up kdebase-workspace-bin (4:4.11.11-0ubuntu0.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...

```

I can't say I like seeing the duplicate sources message again, but the upgrade appears to have run cleanly.

---

### Post by Bashing-om on 2014-09-08
ertrum; Erm !


What did I miss ? We still have :
> 
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

Let's double check the sources, before delving in deeper .
Post once more the updated:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

[INDENT][INDENT]still at step 1
[INDENT][INDENT][INDENT][INDENT]gotta make the package manager happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ertrum on 2014-09-08
If I knew what we were missing, I'd have fixed it long ago :)

/etc/apt/sources.list:
```

 cat -n /etc/apt/sources.list
     1  # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
     2  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     3  # newer versions of the distribution.
     4
     5  deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     6  deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     7
     8  ## Major bug fix updates produced after the final release of the
     9  ## distribution.
    10  deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11  deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12
    13  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14  ## team. Also, please note that software in universe WILL NOT receive any
    15  ## review or updates from the Ubuntu security team.
    16  deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
    17  deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
    18  deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19  deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    20
    21  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22  ## team, and may not be under a free licence. Please satisfy yourself as to 
    23  ## your rights to use the software. Also, please note that software in 
    24  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25  ## security team.
    26  deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    27  deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    28  deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29  deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    30
    31  ## Uncomment the following two lines to add software from the 'backports'
    32  ## repository.
    33  ## N.B. software from this repository may not have been tested as
    34  ## extensively as that contained in the main release, although it includes
    35  ## newer versions of some applications which may provide useful features.
    36  ## Also, please note that software in backports WILL NOT receive any review
    37  ## or updates from the Ubuntu security team.
    38  # deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
    39  # deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
    40
    41  ## Uncomment the following two lines to add software from Canonical's
    42  ## 'partner' repository.
    43  ## This software is not part of Ubuntu, but is offered by Canonical and the
    44  ## respective vendors as a service to Ubuntu users.
    45  deb http://archive.canonical.com/ubuntu trusty partner
    46  deb-src http://archive.canonical.com/ubuntu trusty partner
    47
    48  deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    49  deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    50  deb http://security.ubuntu.com/ubuntu trusty-security universe
    51  deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    52  deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    53  deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    54
    55  ## Added to get xmms -- ert 01jun2010
    56  # deb http://www.pvv.ntnu.no/~knuta/xmms/karmic ./ # disabled on upgrade to precise
    57  # deb-src http://www.pvv.ntnu.no/~knuta/xmms/karmic ./ # disabled on upgrade to precise
    58

```

/etc/apt/sources.list.d:
```

tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/lucid-partner.list <==
# channel for the karmic (10.04) partner channel
# 
#:description:This channel contains the partner software for karmic
deb http://archive.canonical.com/ubuntu trusty partner

==> /etc/apt/sources.list.d/lucid-partner.list.distUpgrade <==
# channel for the karmic (10.04) partner channel
# 
#:description:This channel contains the partner software for karmic
deb http://archive.canonical.com/ubuntu precise partner

```

I think I goofed the last one where precise should be trusty. Mea Culpa, and I'll go try fixing it.

---

### Post by ertrum on 2014-09-08
Hope sprang eternal, and was eternally dashed...

I changed the lucid-partner.list.distUpgrade file, removing the reference to precise and replacing it with trusty, as I had done for the lucid-partner.list

They now look like:
```

tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/lucid-partner.list <==
# channel for the karmic (10.04) partner channel
# 
#:description:This channel contains the partner software for karmic
deb http://archive.canonical.com/ubuntu trusty partner

==> /etc/apt/sources.list.d/lucid-partner.list.distUpgrade <==
# channel for the karmic (10.04) partner channel
# 
#:description:This channel contains the partner software for karmic
deb http://archive.canonical.com/ubuntu trusty partner

```

Then I tried the sudo apt-get update again, and got:
```

sudo apt-get update
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://us.archive.ubuntu.com trusty-updates InRelease
Hit http://us.archive.ubuntu.com trusty Release.gpg
Ign http://security.ubuntu.com trusty-security InRelease
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://us.archive.ubuntu.com trusty Release                                
Get:2 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Get:3 http://us.archive.ubuntu.com trusty-updates Release [59.7 kB]            
Ign http://archive.canonical.com trusty InRelease                        
Hit http://us.archive.ubuntu.com trusty/main Sources                  
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://archive.canonical.com trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Get:4 http://security.ubuntu.com trusty-security Release [59.7 kB]
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://archive.canonical.com trusty Release 
Hit http://us.archive.ubuntu.com trusty/main i386 Packages             
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Get:5 http://security.ubuntu.com trusty-security/main Sources [43.5 kB]
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages              
Hit http://archive.canonical.com trusty/partner Sources  
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://archive.canonical.com trusty/partner amd64 Packages
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Get:6 http://security.ubuntu.com trusty-security/restricted Sources [14 B]
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Get:7 http://security.ubuntu.com trusty-security/universe Sources [10.8 kB]
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Get:8 http://security.ubuntu.com trusty-security/multiverse Sources [699 B]
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [136 kB]
Get:10 http://us.archive.ubuntu.com trusty-updates/main Sources [116 kB]      
Get:11 http://us.archive.ubuntu.com trusty-updates/restricted Sources [1,408 B]
Get:12 http://us.archive.ubuntu.com trusty-updates/universe Sources [82.7 kB]  
Get:13 http://security.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Get:14 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [3,230 B]
Get:15 http://security.ubuntu.com trusty-security/universe amd64 Packages [47.2 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [311 kB]
Get:17 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [1,154 B]
Get:18 http://security.ubuntu.com trusty-security/main i386 Packages [132 kB]  
Get:19 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [5,820 B]
Get:20 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [199 kB]
Get:21 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:22 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [8,221 B]
Get:23 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [304 kB] 
Get:24 http://security.ubuntu.com trusty-security/universe i386 Packages [47.2 kB]
Get:25 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,398 B]
Get:26 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:27 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [200 kB]
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Ign http://archive.canonical.com trusty/partner Translation-en_US              
Get:28 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [8,437 B]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Ign http://archive.canonical.com trusty/partner Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://archive.canonical.com trusty/partner Translation-en_US.utf8
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US.utf8
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US.utf8
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US.utf8
trumbull@allegro (25) => cat /tmp/bar
sudo apt-get update
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://us.archive.ubuntu.com trusty-updates InRelease
Hit http://us.archive.ubuntu.com trusty Release.gpg
Ign http://security.ubuntu.com trusty-security InRelease
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://us.archive.ubuntu.com trusty Release                                
Get:2 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Get:3 http://us.archive.ubuntu.com trusty-updates Release [59.7 kB]            
Ign http://archive.canonical.com trusty InRelease                        
Hit http://us.archive.ubuntu.com trusty/main Sources                  
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://archive.canonical.com trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Get:4 http://security.ubuntu.com trusty-security Release [59.7 kB]
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://archive.canonical.com trusty Release 
Hit http://us.archive.ubuntu.com trusty/main i386 Packages             
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Get:5 http://security.ubuntu.com trusty-security/main Sources [43.5 kB]
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages              
Hit http://archive.canonical.com trusty/partner Sources  
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://archive.canonical.com trusty/partner amd64 Packages
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Get:6 http://security.ubuntu.com trusty-security/restricted Sources [14 B]
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Get:7 http://security.ubuntu.com trusty-security/universe Sources [10.8 kB]
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Get:8 http://security.ubuntu.com trusty-security/multiverse Sources [699 B]
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [136 kB]
Get:10 http://us.archive.ubuntu.com trusty-updates/main Sources [116 kB]      
Get:11 http://us.archive.ubuntu.com trusty-updates/restricted Sources [1,408 B]
Get:12 http://us.archive.ubuntu.com trusty-updates/universe Sources [82.7 kB]  
Get:13 http://security.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Get:14 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [3,230 B]
Get:15 http://security.ubuntu.com trusty-security/universe amd64 Packages [47.2 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [311 kB]
Get:17 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [1,154 B]
Get:18 http://security.ubuntu.com trusty-security/main i386 Packages [132 kB]  
Get:19 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [5,820 B]
Get:20 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [199 kB]
Get:21 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:22 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [8,221 B]
Get:23 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [304 kB] 
Get:24 http://security.ubuntu.com trusty-security/universe i386 Packages [47.2 kB]
Get:25 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,398 B]
Get:26 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:27 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [200 kB]
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Ign http://archive.canonical.com trusty/partner Translation-en_US              
Get:28 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [8,437 B]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Ign http://archive.canonical.com trusty/partner Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Ign http://archive.canonical.com trusty/partner Translation-en_US.utf8
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US.utf8
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US.utf8
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US.utf8
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US.utf8
Fetched 1,786 kB in 4s (439 kB/s)
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ trusty/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ trusty/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

And there was weeping and wailing and gnashing of teeth.

---

### Post by Bashing-om on 2014-09-08
ertrum; Yepper.

All those sources as listed in the directory "/etc/apt/sources.list.d" are outdated and of no use or value .
Remove them from the system.
this one:
> 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
##and##
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


are duplicates of the entry in "/etc/apt/sources.list"
> 
45  deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
46  deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

where you had correctly made the edits.
The one we are going to keep.

Now we try this again:
```

sudo apt-get update
sudo apt-get upgrade

```

and we move merrily along
[INDENT][INDENT][INDENT]to the next thing
[/INDENT][/INDENT][/INDENT]

---

### Post by ertrum on 2014-09-09
Woot Woot!
apt-get update and apt-get upgrade both ran cleanly!

... Moving right along...

---

### Post by Bashing-om on 2014-09-09
ertrum; Great !

Well done. OK, 
Moving right on along:
```

sudo apt-get dist-upgrade

```
This is not related to a release upgrade, rather - the command "apt-get upgrade" upgrades installed packages but will not install anything new, "dist-upgrade, however, does and will, in this case those new kernels.
Let's run this and see what the package manager screams and hollers about... maye (hopefully) will just do it's thing on it's own, and we can then move to the last thing on the list. Those little dependency issues.

[INDENT][INDENT]maybe yes,
[INDENT][INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ertrum on 2014-09-09
apt-get dist-upgrade ran with no problems. I'm now running 3.13.0-35-generic #62-Ubuntu SMP 
apt-get -f install now gives:
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-67 linux-headers-3.2.0-67-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

apt-get autoremove ran fine

And dpkg -C now gives:
```

sudo dpkg -C
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 dhcp3-client         ISC DHCP server (transitional package)
 libjson0:amd64       JSON manipulation library (transitional package)
 dhcp3-common         ISC DHCP common files (transitional package)

```

---

### Post by Bashing-om on 2014-09-09
ertrum; Hey hey !

Moving  right smartly right on along !

Try:
```

sudo apt-get install --reinstall dhcp3-client libjson0:amd64 dhcp3-common

```
See then what the package manager has to relate to the situation.

[INDENT][INDENT]could be, YES
[/INDENT][/INDENT]

---

### Post by ertrum on 2014-09-09
Or it could be no...

libjson0 reinstalled with no problem

The other two give me this:
Reinstallation of dhcp3-client is not possible, it cannot be downloaded.
Reinstallation of dhcp3-common is not possible, it cannot be downloaded.

---

### Post by Bashing-om on 2014-09-09
ertrum; Well !

That is a fact !
> 
Reinstallation of dhcp3-client is not possible, it cannot be downloaded.
Reinstallation of dhcp3-common is not possible, it cannot be downloaded.


As per:
```

sysop@1404mini:~$ apt-cache show dhcp3-client
N: Can't select versions from package 'dhcp3-client' as it is purely virtual
N: No packages found

sysop@1404mini:~$ apt-cache show dhcp3-common
N: Can't select versions from package 'dhcp3-common' as it is purely virtual
N: No packages found
sysop@1404mini:~$

```
They are no longer available .. humm, I wonder what took their places ?

The question now is what are we going to do about it ?
Before getting drastic, let's take a look:
```

dpkg -l dhcp3-client dhcp3-common

```

As it is sorta confusing to me at this time; Per:
> 
sysop@1404mini:~$ apt-cache search dhcp3-client
isc-dhcp-client - ISC DHCP client
sysop@1404mini:~$ 

sysop@1404mini:~$ apt-cache search dhcp3-common
isc-dhcp-common - common files used by all the isc-dhcp* packages
sysop@1404mini:~$

those are still in use ??????

So looks like we are going to go hunting the "parent" package that controls these.
When we see the outputs of 'dpkg' we start look'n anew.


still
[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ertrum on 2014-09-10
Here's what dpgk says:
```
dpkg -l dhcp3-client dhcp3-common
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  dhcp3-client   4.1.ESV-R4-0 all          ISC DHCP server (transitional pac
ii  dhcp3-common   4.1.ESV-R4-0 all          ISC DHCP common files (transition

```

---

### Post by ertrum on 2014-09-10
For curiosity's sake, I did dpkg -l and grepped for dhcp. I got the following:

```

dpkg -l | grep -i dhcp
ii  dhcp3-client                                                4.1.ESV-R4-0ubuntu5.9                               all          ISC DHCP server (transitional package)
ii  dhcp3-common                                                4.1.ESV-R4-0ubuntu5.9                               all          ISC DHCP common files (transitional package)
ii  dnsmasq-base                                                2.68-1                                              amd64        Small caching DNS proxy and DHCP/TFTP server
ii  isc-dhcp-client                                             4.2.4-7ubuntu12                                     amd64        ISC DHCP client
ii  isc-dhcp-common                                             4.2.4-7ubuntu12                                     amd64        common files used by all the isc-dhcp* packages

```

I wonder if the "transitional" packages, which are the ones that dpkg -C flags as invalid, have been superseded by the 
isc-dhcp-packages (which look to be newer)?

---

### Post by Bashing-om on 2014-09-10
ertrum; Humm;

I am sorta in a quandry here trying to understand the packaging .
We have :
> 
dpkg -l dhcp3-client dhcp3-common
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  dhcp3-client   4.1.ESV-R4-0 all          ISC DHCP server (transitional pac
ii  dhcp3-common   4.1.ESV-R4-0 all          ISC DHCP common files (transition

Which shows to be fully installed, no problem noted here
But: We also know:
> 
sysop@1404mini:~$ apt-cache show dhcp3-client
N: Can't select versions from package 'dhcp3-client' as it is purely virtual
N: No packages found

sysop@1404mini:~$ apt-cache show dhcp3-common
N: Can't select versions from package 'dhcp3-common' as it is purely virtual
N: No packages found
sysop@1404mini:~$


HUH ?

I am at a disadvantage as I do not have 'dhcp' on my system. I manage my networking manually.
You may be correct that the virtual package has been superseded.
Let's see if we can find what is on the system:
post back the results:
```

sysop@1404mini:~$ apt-cache depends dhcp3-client
sysop@1404mini:~$ apt-cache rdepends dhcp3-client
sysop@1404mini:~$ apt-cache depends dhcp3-common
sysop@1404mini:~$ apt-cache rdepends dhcp3-common

``` we see where we go from there .

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ertrum on 2014-09-11
```

foreach i ( dhcp3-client dhcp3-common )
foreach? echo $i
foreach? apt-cache depends $i
foreach? apt-cache rdepends $i
foreach? end
dhcp3-client
dhcp3-client
  Depends: isc-dhcp-client
dhcp3-client
Reverse Depends:
  ifupdown:i386
  resolvconf
  ifupdown
  ntpdate:i386
  ntp:i386
  isc-dhcp-client:i386
    isc-dhcp-client
  ifupdown:i386
  zentyal-network
    isc-dhcp-client
  rootstrap
    isc-dhcp-client
 |netscript-2.4-upstart
    isc-dhcp-client
 |netscript-2.4
    isc-dhcp-client
  resolvconf
  ntpdate
  ntp
  isc-dhcp-client
    isc-dhcp-client
  ifupdown
dhcp3-common
dhcp3-common
  Depends: isc-dhcp-common
dhcp3-common
Reverse Depends:
  isc-dhcp-common:i386
    isc-dhcp-common
  isc-dhcp-common
    isc-dhcp-common

```

And I'd be just as happy to be rid of dhcp as well. Like you, I don't use it, but it came in the distro.

---

### Post by Bashing-om on 2014-09-11
ertrum; Well, 

I am just a tad bit wiser.
OK, Output on my system for "isc-dhcp-client".
> 
sysop@1404mini:~$ dpkg -l isc-dhcp-client
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  isc-dhcp-clien 4.2.4-7ubunt amd64        ISC DHCP client
sysop@1404mini:~$


Seems to me that it is required.

Now I have for " dpkg -l dhcp3-common "
> 
sysop@1404mini:~$ dpkg -l dhcp3-common
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  dhcp3-common   <none>       <none>       (no description available)
sysop@1404mini:~$

And that indicates that it is not required:

So, what results with:
```

sudo apt-get remove --purge dhcp3-common
sudo dpkg -C

```
And let's see what breaks, or what me might then have to fix. Might prove to be a good thing to have a record of what gets removed.

Make double sure that networking is operable at this time, reboot also just to make triple sure - I would think - .

[INDENT][INDENT]as we proceed
[INDENT][INDENT][INDENT]on out merry way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ertrum on 2014-09-12
I removed dhcp3-common with no problems.
dpkg -C now only shows dhcp3-client as needing to be reinstalled.

Networking does not appear to have been affected.

---

### Post by ertrum on 2014-09-12
I've rebooted, and networking is still fine.

I have repeated the process removing dhcp3-client.

dpkg -C now shows no errors!

and apt-get update / apt-get upgrade run without whining!

I think that, at long last, we have reached the end of this problem, much thanks.

---

### Post by Bashing-om on 2014-09-12
ertrum; outstanding !

I am pleased to be of some small assistance.

As this matter is now concluded:
Please mark this thread solved; 
aides others seeking the solution, 
helps keep the forum clean and 
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]come back when you have more time
[INDENT][INDENT][INDENT]and stay awhile, helping others
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

