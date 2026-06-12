---
title: "xenial sources.list broken"
date: 2017-02-28
forum: Installation &amp; Upgrades
---

### Post by kmkwood on 2017-02-28
I upgraded from 14.04 to 16.04 a year or so ago.  I noticed that I have not been receiving any updates.  When I run 'sudo apt update' I get

```
% sudo apt update
Hit:2 http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu xenial InRelease
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Err:2 http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu xenial InRelease
  At least one invalid signature was encountered.
Get:1 http://id.archive.ubuntu.com/ubuntu xenial InRelease [247 kB]            
Err:3 http://security.ubuntu.com/ubuntu xenial-security InRelease              
  At least one invalid signature was encountered.
Ign:6 https://private-ppa.launchpad.net/commercial-ppa-uploaders/drfinance/ubuntu xenial InRelease
Get:4 http://id.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Err:1 http://id.archive.ubuntu.com/ubuntu xenial InRelease                     
  At least one invalid signature was encountered.
Err:7 https://private-ppa.launchpad.net/commercial-ppa-uploaders/drfinance/ubuntu xenial Release
  404  Not Found
Get:5 http://id.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Err:4 http://id.archive.ubuntu.com/ubuntu xenial-updates InRelease             
  At least one invalid signature was encountered.
Err:5 http://id.archive.ubuntu.com/ubuntu xenial-backports InRelease
  At least one invalid signature was encountered.
Get:8 http://deb.opera.com/opera stable InRelease [2,592 B]
Err:8 http://deb.opera.com/opera stable InRelease
  At least one invalid signature was encountered.
Get:9 https://deb.opera.com/opera-stable stable InRelease [2,592 B]
Err:9 https://deb.opera.com/opera-stable stable InRelease
  At least one invalid signature was encountered.
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu xenial InRelease: At least one invalid signature was encountered.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com/ubuntu xenial-security InRelease: At least one invalid signature was encountered.
W: GPG error: http://id.archive.ubuntu.com/ubuntu xenial InRelease: At least one invalid signature was encountered.
E: The repository 'http://id.archive.ubuntu.com/ubuntu xenial InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'https://private-ppa.launchpad.net/commercial-ppa-uploaders/drfinance/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://id.archive.ubuntu.com/ubuntu xenial-updates InRelease: At least one invalid signature was encountered.
E: The repository 'http://id.archive.ubuntu.com/ubuntu xenial-updates InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://id.archive.ubuntu.com/ubuntu xenial-backports InRelease: At least one invalid signature was encountered.
E: The repository 'http://id.archive.ubuntu.com/ubuntu xenial-backports InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://deb.opera.com/opera stable InRelease: At least one invalid signature was encountered.
E: The repository 'http://deb.opera.com/opera stable InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://deb.opera.com/opera-stable stable InRelease: At least one invalid signature was encountered.
```

Is sources.list broken?  Have I lost or mangled the signatures?  How do I get a new sources.list, or fix the signatures?

---

### Post by DuckHook on 2017-02-28
...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar. I have also stripped your output of interfering formatting that was an artifact of not using code tags.

One year is a long time to go without any updates. Once you get your system properly updating again, you will have a tremendous backlog of updates to install, so the absolute non-negotiable first order of business at this point is to:

***BACKUP your critical data.***

Nothing is as important as this first step. Once you are satisfied that your data is safe and demonstrably restorable, then:

[LIST=1]
[*]Post your *sources.list* to this thread. Let's see what it actually consists of:```
cat /etc/apt/sources.list
```
[*]I am unfamiliar with "id.archive.ubuntu.com".  Is it a mirror? If not, then it is a malformed reference to the standard repository.
[*]You have a lot of PPAs. This is a potential source of really bad problems. As a rule, I do not recommend the addition of *any* PPAs for new users&#8212;and yet it is new users who usually add them indiscriminately(not calling you a new user, but others will read this thread). PPAs are often the cause of system breakage and especially so with package management.
[*]Once you get your updates working, I recommend a serious review of your PPAs. It is not enough to disable them because some of them may have dragged in incompatible libraries and packages to your system. The best way to rid yourself of PPAs is using PPA-Purge:```
sudo apt install ppa-purge
```&#8230;which will attempt to purge the PPA gracefully and restore any default system libraries that the PPA may have substituted with its own.
[/LIST]

---

### Post by kmkwood on 2017-03-01
Thank you, Duckhook.

```


 % cat sources.list
# deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://id.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://id.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://id.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://id.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://id.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://id.archive.ubuntu.com/ubuntu/ xenial universe
deb http://id.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://id.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://id.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://id.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://id.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://id.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://id.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://id.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse


```

---

### Post by DuckHook on 2017-03-01
[LIST=1]
[*]Please fire up a terminal and do:```
sudo sed -i 's/id.archive/archive/g' /etc/apt/sources.list
```This resets your download repo from the one you presently use to the main repo.
[*]Then disable your PPAs, or better, downright purge any that you don't absolutely need. I notice that you have Opera and something called: commercial-ppa-uploaders that installs something presumably called drfinance. Even if this is indispensable to you, disable it for now.
[*]```
sudo apt update
```If this is successful (returns no errors) then,
[*]```
sudo apt upgrade
```Expect a lot of updates. Again, if no errors:
[*]```
sudo apt full-upgrade
```Expect even more updates.
[*]Enable PPAs and go through the whole update/upgrade cycle above. If anything chokes at this point, then you know the problem is with a PPA
[/LIST]
Let us know how it goes.

---

### Post by deadflowr on 2017-03-01
It's a key problem.
Let's see what the permissions for them are in /etc/apt/trusted.gpg.d are
```
ls -la /etc/apt/trusted.gpg.d
```

Here's a quick (or long, depending on your outlook on length) but report on the issue, in a way,
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1642386]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1642386")

---

### Post by kmkwood on 2017-03-04
Whatever I've done in the last few days broke something loose, because Software Updater is running again daily -- but it still won't install updates.

DuckHook, after seeing your post I cleaned up sources.list as you suggested, and removed the PPA references from sources.list.d.  That made a big difference!

```


# cat sources.list
## deb cdrom:[Ubuntu-Studio 12.04.1 _Precise Pangolin_ - Release i386 (20120818)]/ precise main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ xenial universe
deb http://archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.

## for Tor
deb http://deb.torproject.org/torproject.org xenial main # disabled on upgrade to xenial
deb http://archive.ubuntu.com/ubuntu/ xenial-backports multiverse main restricted universe

```

...a big difference, but not enough:

```

# sudo apt upgrade
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-4.4.0-64 linux-headers-4.4.0-64-lowlatency
  linux-image-4.4.0-64-lowlatency
The following packages will be upgraded:
  apport apport-gtk apt apt-transport-https apt-utils bind9-host
  chromium-codecs-ffmpeg-extra dnsutils ffmpeg firefox firefox-globalmenu

...more package names deleted...

  samba-libs samba-vfs-modules tar tcpdump thunderbird thunderbird-globalmenu
  thunderbird-gnome-support tor tor-geoipdb tzdata uno-libs3 ure vim-common
  vim-tiny xul-ext-calendar-timezones xul-ext-gdata-provider xul-ext-lightning
199 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 401 MB of archives.
After this operation, 279 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  tar libapt-pkg5.0 libapt-inst2.0 apt apt-utils libpython3.5 libssl1.0.0
  python3.5 libpython3.5-stdlib python3.5-minimal libpython3.5-minimal
  libgnutls-openssl27 libhogweed4 libnettle6 libgnutls30 ntfs-3g

...more package names deleted...

  xul-ext-gdata-provider xul-ext-lightning thunderbird
  thunderbird-gnome-support thunderbird-globalmenu tor-geoipdb tor
  xul-ext-calendar-timezones libav-tools oxideqt-codecs-extra
Install these packages without verification? [y/N] n
E: Some packages could not be authenticated


```
I was not willing to install that many -- nearly 50 -- packages without authentication.

Did I lose signatures?  Can I refresh key files somehow?

deadflowr, here is trusted.gpg.d:

```

# ls -la trusted.gpg.d
total 60
drwxr-xr-x 2 root root 4096 Aug 24  2016 .
drwxr-xr-x 6 root root 4096 Mar  4 11:34 ..
-rw-r--r-- 1 root root 5138 Nov 30  2014 debian-archive-jessie-automatic.gpg
-rw-r--r-- 1 root root 5147 Nov 30  2014 debian-archive-jessie-security-automatic.gpg
-rw-r--r-- 1 root root 2775 Nov 30  2014 debian-archive-jessie-stable.gpg
-rw-r--r-- 1 root root 4084 Nov 30  2014 debian-archive-squeeze-automatic.gpg
-rw-r--r-- 1 root root 2853 Nov 30  2014 debian-archive-squeeze-stable.gpg
-rw-r--r-- 1 root root 3780 Nov 30  2014 debian-archive-wheezy-automatic.gpg
-rw-r--r-- 1 root root 2851 Nov 30  2014 debian-archive-wheezy-stable.gpg
-rw-r--r-- 1 root root 2652 Aug 22  2016 deb.torproject.org-keyring.gpg
-rw------- 1 root root 1216 Jan 20  2013 jockey-drivers.gpg
-rw------- 1 root root    0 Jan 20  2013 jockey-drivers.gpg~
-rw-r--r-- 1 root root  392 May 26  2015 mscore-ubuntu-mscore-stable.gpg
-rw-r--r-- 1 root root    0 May 26  2015 mscore-ubuntu-mscore-stable.gpg~
-rw-r--r-- 1 root root  363 Jun 27  2015 yg-jensge-gupnp.gpg
-rw-r--r-- 1 root root    0 Jun 27  2015 yg-jensge-gupnp.gpg~

```

I followed your link, then noticed the 2 files that were 640 root.root, and removed them.  I think you found it:

```

# apt update
Get:1 http://archive.canonical.com/ubuntu xenial InRelease [11.5 kB]
Get:2 http://deb.torproject.org/torproject.org xenial InRelease [3,521 B]     
Get:3 http://archive.ubuntu.com/ubuntu xenial InRelease [247 kB]      

...more package names deleted, no errors ...

Get:52 http://archive.ubuntu.com/ubuntu xenial-backports/universe i386 DEP-11 Metadata [212 B]
Get:53 http://archive.ubuntu.com/ubuntu xenial-backports/universe DEP-11 64x64 Icons [29 B]
Fetched 29.0 MB in 7s (3,976 kB/s)                                            
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
Building dependency tree      
Reading state information... Done
351 packages can be upgraded. Run 'apt list --upgradable' to see them.


```

apt update and apt upgrade both ran fine.  I rebooted then ran Software Updater; it said all software is up to date.

It looks like I needed both these fixes -- removing old PPA references and removing the not-world-readable files in trusted.gpg.d -- to get past the problem.  Many thanks to both of you.

I am puzzled how these things happened.  I don't understand the repository process well enough to go mucking about in it.  I think when I installed MuseScore, Darhon Finance, and Opera -- all 3 of them from Unbuntu Software Center -- that the PPAs were added.  I added tor through synaptic package manager.

My spouse has a System 76 laptop which is also running Ubuntu.  I upgraded it to 16.04 last summer, and I'll have to check the same things on it because it hasn't been updating either.

---

### Post by DuckHook on 2017-03-04
> **kmkwood said:**
> …It looks like I needed both these fixes -- removing old PPA references and removing the not-world-readable files in trusted.gpg.d -- to get past the problem.  Many thanks to both of you.Happy for you that it ultimately worked out.> I am puzzled how these things happened.  I don't understand the repository process well enough to go mucking about in it.You are correct. It is generally not a good idea to experiment in dpkg unless you know exactly what you are doing. Broken dpkg is one of the common and recurring problems on these forums.> I think when I installed MuseScore, Darhon Finance, and Opera -- all 3 of them from Unbuntu Software Center -- that the PPAs were added.Not trying to be argumentative, but you may have installed through PPA and forgotten that you did so. AFAIK, Ubuntu will not automatically add a PPA. This has to be done manually. According to: ```
apt show musescore
```…musescore is available from the repos—no need for a PPA. Darhon Finance is not available in the repos after [Trusty (14.04)]("https://apps.ubuntu.com/cat/applications/drfinance/"). The version you have is either obsolete or from a PPA, which may be the reason that you added a PPA. I suspect that it's this old version that may have gummed up your app database by its dependence on old libraries. Opera is only available by PPA or by directly installing the .deb file. Therefore, the PPA had to have been manually added at some point in the past. 

I recommend the following:

[LIST=1]
[*]If you have a large usage history accumulated with Darhon Financing, then install it in a Trusty (14.04) virtual machine and run it that way. You will buy a little more than two years' time to switch over to another accounting app. In the long run, you will have to make some sort of switch due to Darhon's eventual end of support.
[*]You can likewise run a VM for Opera and sandbox that PPA within the VM, thus not effecting your host system.
[*]Ditto for Tor (that's how I run it).
[/LIST]
Good Luck and Happy Ubuntu-ing!

---

### Post by bobmann on 2017-03-29
> **DuckHook said:**
> 

I recommend the following:

[LIST=1]
[*]If you have a large usage history accumulated with Darhon Financing, then install it in a Trusty (14.04) virtual machine and run it that way. You will buy a little more than two years' time to switch over to another accounting app. In the long run, you will have to make some sort of switch due to Darhon's eventual end of support.
[*]You can likewise run a VM for Opera and sandbox that PPA within the VM, thus not effecting your host system.
[*]Ditto for Tor (that's how I run it).
[/LIST]
Good Luck and Happy Ubuntu-ing!

Using Wine for years. My [accounting software]("https://zipbooks.com/bookkeeping-services/") ZipBooks does not work with Parallel. I don't know why. May be there was some integration problem with parallel version. I,m not sure. After that switched to Winehq and everything is fine.

---

