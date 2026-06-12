---
title: "Upgrade to 14.04 fails while &quot;calculating the upgrade&quot;"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by theyexpectresults on 2014-05-08
Trying to upgrade from Xubuntu 13.10 to 14.04 (64-bit), using either [FONT=courier new]**do-release-upgrade**[/FONT] or the GUI update manager, it fails, giving the following error message:

```
An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.
```

I tried disabling third party software sources, then I tried removing third party repositories completely from the sources list. I have also tried the following, with no success:

```
$ sudo apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

When I check /var/log/dist-upgrade/apt.log, it lists a large number of broken packages. Here is a sample: 
```
$ cat /var/log/dist-upgrade/apt.log | grep Broken
Broken python3:amd64 Depends on python3.4 [ amd64 ] < none -> 3.4.0-2ubuntu1 > ( python ) (>= 3.4.0-0~)
Broken libqt5core5a:amd64 Breaks on libqt5core5 [ amd64 ] < 5.0.2+dfsg1-7ubuntu11.1 > ( libs ) (< 5.2.0+dfsg~)
Broken python3-gi:amd64 Depends on python3 [ amd64 ] < 3.3.2-14ubuntu1 -> 3.4.0-0ubuntu2 > ( python ) (>= 3.4~)
Broken cups-filters:amd64 Conflicts on foomatic-filters [ amd64 ] < 4.0.17-1ubuntu1 > ( universe/text )
Broken dh-python:amd64 Depends on python3:any [ amd64 ] < none > ( none ) (>= 3.3.2-2~)
Broken python3-minimal:amd64 Depends on python3.4-minimal [ amd64 ] < none -> 3.4.0-2ubuntu1 > ( python ) (>= 3.4.0-0~)
Broken lsb-release:amd64 Depends on python3 [ amd64 ] < 3.3.2-14ubuntu1 -> 3.4.0-0ubuntu2 > ( python )
(...many more packages listed)
```

If it's relevant, Python 3 seems to work fine on my system. Can anyone recommend how I might go about fixing this, and upgrading? Sorry if I have left out any details. Thanks.

---

### Post by ibjsb4 on 2014-05-09
Got any third party software?

```
ls /etc/apt/sources.list.d/*.list
```

---

### Post by theyexpectresults on 2014-05-10
Hi, there are a bunch of third party sources listed. I had unchecked all third party sources in the Software & Updates section of settings manager, but the sources below are still listed. Is there another way to disable them? Thanks a lot for your help. 
```
/etc/apt/sources.list.d/dropbox.list
/etc/apt/sources.list.d/irie-blender-quantal.list
/etc/apt/sources.list.d/jon-severinsson-ffmpeg-quantal.list
/etc/apt/sources.list.d/kilian-f_lux-quantal.list
/etc/apt/sources.list.d/mendeleydesktop.list
/etc/apt/sources.list.d/nvbn-rm-ppa-saucy.list
/etc/apt/sources.list.d/openrtm-stable-quantal.list
/etc/apt/sources.list.d/openshot_developers-ppa-raring.list
/etc/apt/sources.list.d/ros-latest.list
/etc/apt/sources.list.d/vincent-c-nevernote-oneiric.list
/etc/apt/sources.list.d/vincent-c-nevernote-quantal.list
/etc/apt/sources.list.d/virtualbox.list
/etc/apt/sources.list.d/webupd8team-java-quantal.list
/etc/apt/sources.list.d/yannubuntu-boot-repair-saucy.list

```

---

### Post by ibjsb4 on 2014-05-10
What are you running right now?  You have a mix of old ppa's and they should just be removed.  Only your current installed system should be there.

My pet way is a package called 'ppa-purge', but there are other ways.

[http://www.google.com/search?client=qupzilla&q=remove%20ppa%20ubuntu](http://www.google.com/search?client=qupzilla&q=remove%20ppa%20ubuntu)

Take a look at your sources list in terminal.

> cat /etc/apt/sources.list

I think you will be good to go after that.

---

### Post by theyexpectresults on 2014-05-12
Hi, I'm pretty sure I have removed all those old and third party ppas, but do-release-upgrade still fails with the same error as above. 
I also realised I was running oracle-java, so I have reverted to openjdk, but it still won't work. 

Is there anything else you can think of? Thanks again. 

```
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu saucy main restricted
deb-src http://archive.ubuntu.com/ubuntu saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu saucy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu saucy universe
deb-src http://archive.ubuntu.com/ubuntu saucy universe
deb http://archive.ubuntu.com/ubuntu saucy-updates universe
deb-src http://archive.ubuntu.com/ubuntu saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu saucy multiverse
deb-src http://archive.ubuntu.com/ubuntu saucy multiverse
deb http://archive.ubuntu.com/ubuntu saucy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu saucy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu saucy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu saucy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu saucy-security main restricted
deb http://archive.ubuntu.com/ubuntu saucy-security universe
deb-src http://archive.ubuntu.com/ubuntu saucy-security universe
deb http://archive.ubuntu.com/ubuntu saucy-security multiverse
deb-src http://archive.ubuntu.com/ubuntu saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu saucy partner
# deb-src http://archive.canonical.com/ubuntu saucy partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu saucy main
# deb-src http://extras.ubuntu.com/ubuntu saucy main
# deb http://archive.canonical.com/ saucy partner
# deb-src http://archive.canonical.com/ saucy partner
```

---

### Post by ibjsb4 on 2014-05-12
OK, your sources.list is good and you cleaned up your sources.list.d.
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
If you get thru that list without errors, try the version upgrade again.  If it fails with the same error, try:
    
```
do-release-upgrade -d
```
Do you have backup in place?  This may be a rough upgrade.

---

### Post by theyexpectresults on 2014-05-12
Hi, thanks again. I got through all the first set of commands with no errors (autoremove removed one package: libjson0:i386), but then the upgrade failed again for the same reason as before. 

Do you think I will need to reinstall completely instead of upgrading? I have backups, so I could do it, but it would be a bit of a pain.

---

### Post by ibjsb4 on 2014-05-12
Using the "-d" switch should of worked.

You say same error?  Are you sure about your sources.list.d?

About doing a fresh install.  It is the highly prefered method.  I usually do both, depends on the situation.  I have had a couple of failed upgrades, for me they are rare, but can happen.

From the look of those old ppa's, I think you have not done a fresh install in a while.  These LTS releases are supported for five years, all others are supported for nine months.  I like my 12.04 setup and will probably keep it for a couple of more years.

---

### Post by theyexpectresults on 2014-05-13
Yeah, I've double checked sources.list.d and there is nothing in there, unfortunately. Looks like I will have to do a full reinstall, which is a bit of a hassle, but maybe easier than chasing down this problem! Thanks a lot for your help.

---

