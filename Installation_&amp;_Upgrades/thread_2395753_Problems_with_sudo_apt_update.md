---
title: "Problems with sudo apt update"
date: 2018-07-06
forum: Installation &amp; Upgrades
---

### Post by simone93 on 2018-07-06
Good afternoon to everyone,
Last night I tried to update my computer as always, but from that moment it gives me this error:
```
sudo apt update
Hit:1 http://it.archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease                        
Hit:3 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:4 http://archive.ubuntu.com/ubuntu xenial-updates InRelease                
Hit:5 http://ppa.launchpad.net/george-edison55/cmake-3.x/ubuntu xenial InRelease
Hit:6 http://archive.ubuntu.com/ubuntu xenial-backports InRelease              
Hit:7 http://repository.spotify.com stable InRelease                           
Hit:8 http://archive.ubuntu.com/ubuntu xenial-security InRelease               
Hit:9 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease    
Hit:10 http://ppa.launchpad.net/teejee2008/ppa/ubuntu xenial InRelease        
AppStream system cache was updated, but problems were found: Metadata files have errors: /var/cache/app-info/xmls/fwupd.xml
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh-cache > /dev/null; fi'
E: Sub-process returned an error code
```

I tried to follow this thread :[ ]("https://askubuntu.com/questions/854168/how-i-can-fix-appstream-cache-update-completed-but-some-metadata-was-ignored-d")[https://askubuntu.com/questions/854168/how-i-can-fix-appstream-cache-update-completed-but-some-metadata-was-ignored-d](https://askubuntu.com/questions/854168/how-i-can-fix-appstream-cache-update-completed-but-some-metadata-was-ignored-d)

But doesn't work for me! How I can fix it ?
I've an ASUS x541uv (ubuntu 16.04.4) with:
```
uname -r
4.13.0-45-generic
```

Tell me if you need further informations.
Thanks in advice!

---

### Post by TheFu on 2018-07-06
Out of space or inodes?
```
df -h
df -i
```

Anything in the system logs?

Please post the exact commands you have entered.   "history" will get you see them.

I have a number of 16.04 systems. None have shown this issue, but I only patch on weekends.  Saturday may have my 20+ systems in the same boat.

Has anyone tried using aptitude or apt-get as alternatives?

---

### Post by gumbeto on 2018-07-06
I have the same issue. This started happening recently (~ last week or so). Other people are apparently suffering from the same issue, which has a good description [here]("https://askubuntu.com/questions/1051536/appstreamcli-appstream-system-cache-was-updated-but-problems-were-found-metad") (wrongly marked as duplicate IMO).

My understanding is that the problem is in "appstream-glib", but it is fixed in newer versions. The authors claim "Ubuntu needs to backport this fix into 16.04" (see [this comment]("https://github.com/hughsie/fwupd/issues/565#issuecomment-402541089")).

I looked a bit into this and none of the proposed solutions to similar problems work (they mostly concern similar problems with older versions of the appstream). I tried a bunch of reinstalls to no avail. Erasing fwupd.xml and refreshing appstream cache doesn't help either: the new file will still have the same ampersand-containing string which trips the old version of libappstream-glib8 available in xenial, IIUC.

---

### Post by marvync on 2018-07-06
The same problem here, but in my case the message only appear when I run sudo apt update by the first time. In the next times the message disappear.

AppStream system cache was updated, but problems were found: Metadata files have errors: /var/cache/app-info/xmls/fwupd.xml
Lendo listas de pacotes... Pronto
E: Problem executing scripts APT::Update: Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh-cache > /dev/null; fi'
E: Sub-process returned an error code

---

### Post by gumbeto on 2018-07-06
> **marvync said:**
> in my case the message only appear when I run *sudo apt update* by the first time.

After a while it will appear again, I believe. I think that's because appstreamcli will not always update the cache (there must be some cache validity period or something). If I am correct, you will get the same issue every time you try to refresh the cache with:

```
appstreamcli refresh-cache --force
```

---

### Post by gumbeto on 2018-07-06
In the interest of this thread's self-containment, the following commands pinpoint the problem:

```
$ sudo appstreamcli --version
AppStream CLI tool version: 0.10.6

$ sudo appstreamcli refresh-cache --force --verbose
[...]
** (appstreamcli:5867): DEBUG: WARNING: Could not parse XML data: Entity: line 265: parser error : EntityRef: expecting ';'
        <checksum filename="Firmware_SF30&SN30_Pro_V1.26.dat" target="content" t
[...]
AppStream system cache was updated, but problems were found: Metadata files have errors: /var/cache/app-info/xmls/fwupd.xml
```

---

### Post by TheFu on 2018-07-06
```
$ appstreamcli
The program 'appstreamcli' is currently not installed.
```

I checked 8 systems here. None have that program installed.  Looks to be part of gnome3, which we don't use.

---

### Post by simone93 on 2018-07-06
Hi TheFu,
this are the outputs (here why I have two boot partitions [https://ubuntuforums.org/showthread.php?t=2392861](https://ubuntuforums.org/showthread.php?t=2392861)):
```
simone@simone-X541UV:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            5,8G     0  5,8G   0% /dev
tmpfs           1,2G  9,5M  1,2G   1% /run
/dev/sda3        45G   15G   28G  35% /
tmpfs           5,8G   33M  5,8G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           5,8G     0  5,8G   0% /sys/fs/cgroup
/dev/sda2       510M   91M  382M  20% /boot
/dev/sda1       532M  3,5M  529M   1% /boot/efi
/dev/sdb2       868G  128G  696G  16% /home
tmpfs           1,2G   60K  1,2G   1% /run/user/1000
simone@simone-X541UV:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
udev            1512136    535  1511601    1% /dev
tmpfs           1519826    797  1519029    1% /run
/dev/sda3       2990080 384080  2606000   13% /
tmpfs           1519826     38  1519788    1% /dev/shm
tmpfs           1519826      6  1519820    1% /run/lock
tmpfs           1519826     17  1519809    1% /sys/fs/cgroup
/dev/sda2         34240    299    33941    1% /boot
/dev/sda1             0      0        0     - /boot/efi
/dev/sdb2      57753600 647119 57106481    2% /home
tmpfs           1519826     29  1519797    1% /run/user/1000
```

Yes I checked and the command that i gave last night was: ```
sudo apt update
```.

I'm in the exactly situation of gumbeto (same version and same error).

Any idea what we can do ?

---

### Post by gumbeto on 2018-07-07
@TheFu, makes sense, this is indeed gnome stuff. For information:

```
$ aptitude why appstream
i   ubuntu-desktop  Recommends ubuntu-software                            
i A ubuntu-software Depends    gnome-software (= 3.20.5-0ubuntu0.16.04.11)
i A gnome-software  Depends    appstream
```

---

### Post by simone93 on 2018-07-09
Can someone help me to understand this output ? In a thread i've read they suggest to look at it.
```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 16.04.4 LTS _Xenial Xerus_ - Release amd64 (20180228)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu xenial main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial restricted universe multiverse main #Added by software-properties
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial-updates restricted universe multiverse main #Added by software-properties
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu xenial universe
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial universe
deb http://archive.ubuntu.com/ubuntu xenial-updates universe
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu xenial multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://archive.ubuntu.com/ubuntu xenial-updates multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse #Added by software-properties
deb-src http://it.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://archive.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial-security restricted universe multiverse main #Added by software-properties
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://archive.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://archive.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
```

---

### Post by gumbeto on 2018-07-09
That is the content of the file you passed to cat -- /etc/apt/sources.list -- which is one of the places where the repositories you get your software from are configured. You can read about repositories [here]("https://help.ubuntu.com/community/Repositories/Ubuntu").

Concerning the original issue, it is now being tracked in [https://bugs.launchpad.net/ubuntu/xenial/+source/appstream-glib/+bug/1780442](https://bugs.launchpad.net/ubuntu/xenial/+source/appstream-glib/+bug/1780442)

---

### Post by simone93 on 2018-07-09
> **gumbeto said:**
> That is the content of the file you passed to cat -- /etc/apt/sources.list -- which is one of the places where the repositories you get your software from are configured. You can read about repositories [here]("https://help.ubuntu.com/community/Repositories/Ubuntu").

Concerning the original issue, it is now being tracked in [https://bugs.launchpad.net/ubuntu/xenial/+source/appstream-glib/+bug/1780442](https://bugs.launchpad.net/ubuntu/xenial/+source/appstream-glib/+bug/1780442)

Thanks for your reply.
Maybe they fix the problem, 10 minutes ago I gave the same command and it found a new update that seems has fix the problem:
```
sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-firmware
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 50,0 MB of archives.
After this operation, 142 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-firmware all 1.157.20 [50,0 MB]
Fetched 50,0 MB in 14s (3.380 kB/s)                                            
(Reading database ... 360974 files and directories currently installed.)
Preparing to unpack .../linux-firmware_1.157.20_all.deb ...
Unpacking linux-firmware (1.157.20) over (1.157.19) ...
Setting up linux-firmware (1.157.20) ...
update-initramfs: Generating /boot/initrd.img-4.13.0-45-generic
```

I want to wait some other reboot before marked the thread as Solved.

EDIT: It's not true :( this doesn't fix the problem! I don't know what i've to do...

---

### Post by Ivo_Wever on 2018-07-13
The AskUbuntu issue linked earlier was wrongly closed as a duplicate: this issue is different. It is actually answered on [askubuntu.com/a/1053018/28943]("https://askubuntu.com/a/1053018/28943"): manually edit /var/cache/app-info/xmls/fwupd.xml to replace the & by &amp; in the offending line (in line 265 in my version). The file simply contains an unescaped & and is thus invalid XML.

I haven't bothered to figure out where that file comes from. It's not installed directly by any package; it is probably constructed by appstream, but possibly by copying wrongly escaped XML from another file.

---

### Post by gumbeto on 2018-07-13
Unfortunately the file reverts to the original &-containing string when fwupdmgr refreshes.

---

### Post by simone93 on 2018-07-14
Is there a way to make this change permanently? 

Thanks for your reply!

---

### Post by gumbeto on 2018-07-16
The problem seems to be gone for me, I think a fix was released that still requires manually deleting the faulty xml file, but I was messing with my system a bit before and I am not sure if it could be related. What happens if you do

```
$ sudo mv /var/cache/app-info/xmls/fwupd.xml ~/fwupd.xml.bck
$ sudo fwupdmgr refresh
$ sudo appstreamcli refresh
```

Does it still complain?

---

### Post by Tony_Bennett on 2018-07-17
Here's my output from running the commands:

```
$ sudo mv /var/cache/app-info/xmls/fwupd.xml ~/fwupd.xml.bck
$ sudo fwupdmgr refresh
$ sudo appstreamcli refresh
AppStream system cache was updated, but problems were found: Metadata files have errors: /var/cache/app-info/xmls/fwupd.xml
```

---

### Post by simone93 on 2018-07-17
> **Tony_Bennett said:**
> Here's my output from running the commands:

```
$ sudo mv /var/cache/app-info/xmls/fwupd.xml ~/fwupd.xml.bck
$ sudo fwupdmgr refresh
$ sudo appstreamcli refresh
AppStream system cache was updated, but problems were found: Metadata files have errors: /var/cache/app-info/xmls/fwupd.xml
```

The same for me :(

---

### Post by gumbeto on 2018-07-17
OK, my bad, I forgot a couple of system restarts before, which totally messed up my conclusions...

So, I was able to fix this by installing libappstream-glib8 from bionic. The procedure is below. If you find yourself in one of the cases marked ABORT, just undo all the steps you did so far and run [FONT=Courier New]sudo apt update[/FONT] at the end (I don't expect that to happen though, they are just there as a safeguard).

[LIST=1]
[*]save a file called (say) [FONT=Courier New]future.list[/FONT] in dir [FONT=Courier New]/etc/apt/sources.list.d[/FONT] (you'll need sudo) with the following content:
```

deb mirror://mirrors.ubuntu.com/mirrors.txt bionic main
deb mirror://mirrors.ubuntu.com/mirrors.txt bionic-updates main
deb mirror://mirrors.ubuntu.com/mirrors.txt bionic-security main
```
[*]save a file called (say) [FONT=Courier New]future.pref[/FONT] in dir [/etc/apt/preferences.d[/CODE] (you'll need sudo again) with the following content:
```

Package: *
Pin: release a=bionic*
Pin-Priority: 50

```
[*]run [FONT=Courier New]sudo apt update[/FONT]
[*]run [FONT=Courier New]apt list -u[/FONT] and confirm it returns *only* "Listing... Done". If it returns more stuff, ABORT (see above).
[*]run [FONT=Courier New]sudo apt install -assume-no -t=bionic libappstream-glib8[/FONT]. If, at this stage, apt claims that more is needed to satisfy dependencies than just replacing the old version with the new one, ABORT (see above).
[*]run [FONT=Courier New]sudo mv /var/cache/app-info/xmls/fwupd.xml ~/fwupd.xml.bck[/FONT]
[*]restart (I found this was required, probably to load the new shared library version and maybe restart some service. If you do try to skip it, remember to delete the xml before retrying.)
[*]run [FONT=Courier New]sudo fwupdmgr refresh[/FONT]
[*]run [FONT=Courier New]sudo appstreamcli refresh[/FONT].
[/LIST]

At this point the problem should be fixed. You can leave everything as is (perhaps deleting ~/fwupd.xml.bck if you want). When you now upgrade your packages, packages whose bionic version is installed will receive bionic upgrades, but the rest will still be on xenial.

Let me know what you find. Cheers

---

### Post by sashainsydney2016 on 2018-07-26
If your problem is this error message:
> AppStream system cache was updated, but problems were found: Metadata files have errors: /var/cache/app-info/xmls/fwupd.xml
Try:
```
gksudo gedit /var/cache/app-info/xmls/fwupd.xml
```
and look at line 265 of the file fwupd.xml.
If there you find this (note **bolded**):
> <checksum filename="Firmware_SF30**&**SN30_Pro_V1.26.dat"
Change it to:
> <checksum filename="Firmware_SF30**&amp;**SN30_Pro_V1.26.dat"
That is, replace the character "**&**" with the five characters "**&amp;**".

To be safe, you may want to make a backup of the file first, before editing it.

Further reference is [here]("https://askubuntu.com/questions/894519/ubuntu-16-04-appstreamcli-error-while-get-update/1053018#1053018").

---

### Post by gumbeto on 2018-07-26
As I commented there, *Unfortunately the file reverts to the original &-containing string when fwupdmgr refreshes.*

---

### Post by tibistibi on 2018-07-31
thanks below helped, i made a backup in the same dir but that gave an error. so moved the backup away and now all works fine :D



> **sashainsydney2016 said:**
> If your problem is this error message:

Try:
```
gksudo gedit /var/cache/app-info/xmls/fwupd.xml
```
and look at line 265 of the file fwupd.xml.
If there you find this (note **bolded**):

Change it to:

That is, replace the character "**&**" with the five characters "**&amp;**".

To be safe, you may want to make a backup of the file first, before editing it.

Further reference is [here]("https://askubuntu.com/questions/894519/ubuntu-16-04-appstreamcli-error-while-get-update/1053018#1053018").

---

### Post by kamil-j-nizinski on 2018-07-31
> **gumbeto said:**
> Unfortunately the file reverts to the original &-containing string when fwupdmgr refreshes.

For me this seems to be fixed by reinstalling libappstream3 and libappstream4 packages. Could you tell me if reinstalling the highest version of libappstream that you have works for you?

For example to reinstall libappstream4 you would run:

```
sudo apt install --reinstall libappstream4
```

Alternatively, maybe we could just wait for a fix to this bug to be released: [https://bugs.launchpad.net/ubuntu/+source/appstream-glib/+bug/1780442](https://bugs.launchpad.net/ubuntu/+source/appstream-glib/+bug/1780442)

---

### Post by gumbeto on 2018-08-01
No, I tried that along with many other reinstalls and it did not work for me.

I fixed it by installing [FONT=Courier New]libappstream-glib8[/FONT] it from bionic:

```

$ apt policy libappstream-glib8 
libappstream-glib8:
  Installed: 0.7.7-2
  Candidate: 0.7.7-2
  Version table:
 *** 0.7.7-2 100
         40 mirror://mirrors.ubuntu.com/mirrors.txt bionic/main amd64 Packages
        100 /var/lib/dpkg/status
     0.7.1-2 50
         50 mirror://mirrors.ubuntu.com/mirrors.txt artful/main amd64 Packages
     0.5.13-1ubuntu5 500
        500 mirror://mirrors.ubuntu.com/mirrors.txt xenial-updates/main amd64 Packages
     0.5.13-1 500
        500 mirror://mirrors.ubuntu.com/mirrors.txt xenial/main amd64 Packages

```

---

### Post by kamil-j-nizinski on 2018-08-02
Thanks, also my file actually reverted to the original &-containing string again so my solution doesn't work.

I think I'll just wait for someone to fix it.

---

### Post by nyck66 on 2018-09-06
```
[CODE]sudo apt-get update
Get:1 file:/var/cuda-repo-8-0-local-cublas-performance-update  InRelease
Ign:1 file:/var/cuda-repo-8-0-local-cublas-performance-update  InRelease
Get:2 file:/var/cuda-repo-8-0-local-ga2  InRelease
Ign:2 file:/var/cuda-repo-8-0-local-ga2  InRelease
Get:3 file:/var/cuda-repo-8-0-local-cublas-performance-update  Release [574 B]
Get:4 file:/var/cuda-repo-8-0-local-ga2  Release [574 B]
Get:3 file:/var/cuda-repo-8-0-local-cublas-performance-update  Release [574 B]
Get:4 file:/var/cuda-repo-8-0-local-ga2  Release [574 B]
Hit:7 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic InRelease              
Get:8 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates InRelease [88.7 kB]
Ign:9 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:10 https://deb.nodesource.com/node_8.x bionic InRelease                    
Hit:11 https://download.docker.com/linux/ubuntu bionic InRelease               
Hit:12 https://repo.skype.com/deb stable InRelease                             
Hit:13 https://dl.yarnpkg.com/debian stable InRelease                          
Hit:14 http://archive.canonical.com bionic InRelease                           
Hit:15 http://dl.google.com/linux/chrome/deb stable Release                    
Get:16 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-backports InRelease [74.6 kB]
Hit:17 http://ppa.launchpad.net/adabbas/1stppa/ubuntu xenial InRelease         
Get:18 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-security InRelease [83.2 kB]
Ign:20 http://download.opensuse.org/repositories/home:/cabelo/xUbuntu_18.04  InRelease
Hit:21 https://repo.windscribe.com/ubuntu zesty InRelease                      
Hit:22 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu xenial InRelease         
Get:23 http://download.opensuse.org/repositories/home:/cabelo/xUbuntu_18.04  Release [999 B]
Get:24 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates/universe Sources [59.7 kB]
Get:26 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates/main Sources [162 kB]
Get:27 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates/main amd64 Packages [312 kB]
Get:28 http://download.opensuse.org/repositories/home:/cabelo/xUbuntu_18.04  Release.gpg [481 B]
Hit:29 http://ppa.launchpad.net/git-core/ppa/ubuntu xenial InRelease           
Get:30 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates/main i386 Packages [280 kB]
Get:31 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates/main Translation-en [118 kB]
Ign:28 http://download.opensuse.org/repositories/home:/cabelo/xUbuntu_18.04  Release.gpg
Hit:19 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease 
Get:32 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates/main amd64 DEP-11 Metadata [138 kB]
Get:33 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates/main DEP-11 48x48 Icons [31.4 kB]
Get:34 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates/main DEP-11 64x64 Icons [53.7 kB]
Get:35 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates/universe i386 Packages [179 kB]
Get:36 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates/universe amd64 Packages [179 kB]
Get:37 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates/universe Translation-en [83.0 kB]
Get:38 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [158 kB]
Hit:39 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease   
Get:40 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates/universe DEP-11 48x48 Icons [164 kB]
Get:41 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates/universe DEP-11 64x64 Icons [276 kB]
Get:42 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:43 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [5,100 B]
Get:44 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:45 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-security/universe amd64 DEP-11 Metadata [6,824 B]
Get:46 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-security/universe DEP-11 64x64 Icons [11.3 kB]
Hit:47 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease   
Hit:48 http://ppa.launchpad.net/linrunner/tlp/ubuntu bionic InRelease          
Hit:49 http://ppa.launchpad.net/linrunner/tlp/ubuntu xenial InRelease          
Hit:50 http://ppa.launchpad.net/ondrej/php/ubuntu bionic InRelease             
Hit:51 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease       
Hit:52 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial InRelease 
AppStream system cache was updated, but problems were found: Metadata files have errors: /var/cache/app-info/xmls/fwupd.xml
Reading package lists... Done
W: GPG error: http://download.opensuse.org/repositories/home:/cabelo/xUbuntu_18.04  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9DE5F05C7DC19DAA
E: The repository 'http://download.opensuse.org/repositories/home:/cabelo/xUbuntu_18.04  Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh-cache > /dev/null; fi'
E: Sub-process returned an error code
nobu@nobu-ThinkPad-T420:~$ sudo apt-get install owasp-zap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package owasp-zap
nobu@nobu-ThinkPad-T420:~$ sudo apt-get update
Get:1 file:/var/cuda-repo-8-0-local-cublas-performance-update  InRelease
Ign:1 file:/var/cuda-repo-8-0-local-cublas-performance-update  InRelease
Get:2 file:/var/cuda-repo-8-0-local-ga2  InRelease
Ign:2 file:/var/cuda-repo-8-0-local-ga2  InRelease
Get:3 file:/var/cuda-repo-8-0-local-cublas-performance-update  Release [574 B]
Get:4 file:/var/cuda-repo-8-0-local-ga2  Release [574 B]
Get:3 file:/var/cuda-repo-8-0-local-cublas-performance-update  Release [574 B]
Get:4 file:/var/cuda-repo-8-0-local-ga2  Release [574 B]
Hit:7 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic InRelease              
Hit:8 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-updates InRelease      
Ign:9 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:10 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-backports InRelease   
Hit:11 https://download.docker.com/linux/ubuntu bionic InRelease               
Hit:12 https://deb.nodesource.com/node_8.x bionic InRelease                    
Hit:13 https://dl.yarnpkg.com/debian stable InRelease                          
Hit:14 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-security InRelease    
Hit:15 http://archive.canonical.com bionic InRelease                           
Hit:16 https://repo.skype.com/deb stable InRelease                             
Hit:17 http://ftp.tsukuba.wide.ad.jp/Linux/ubuntu bionic-proposed InRelease    
Hit:18 http://dl.google.com/linux/chrome/deb stable Release                    
Hit:19 http://ppa.launchpad.net/adabbas/1stppa/ubuntu xenial InRelease         
Ign:20 http://download.opensuse.org/repositories/home:/cabelo/xUbuntu_18.04  InRelease
Get:22 http://download.opensuse.org/repositories/home:/cabelo/xUbuntu_18.04  Release [999 B]
Hit:23 https://repo.windscribe.com/ubuntu zesty InRelease                      
Hit:24 http://ppa.launchpad.net/gezakovacs/ppa/ubuntu xenial InRelease         
Get:25 http://download.opensuse.org/repositories/home:/cabelo/xUbuntu_18.04  Release.gpg [481 B]
Hit:26 http://ppa.launchpad.net/git-core/ppa/ubuntu xenial InRelease           
Hit:21 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease
Hit:28 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease   
Ign:25 http://download.opensuse.org/repositories/home:/cabelo/xUbuntu_18.04  Release.gpg
Hit:29 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease   
Hit:30 http://ppa.launchpad.net/linrunner/tlp/ubuntu bionic InRelease          
Hit:31 http://ppa.launchpad.net/linrunner/tlp/ubuntu xenial InRelease          
Hit:32 http://ppa.launchpad.net/ondrej/php/ubuntu bionic InRelease             
Hit:33 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease       
Hit:34 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial InRelease 
AppStream system cache was updated, but problems were found: Metadata files have errors: /var/cache/app-info/xmls/fwupd.xml
Reading package lists... Done
W: GPG error: http://download.opensuse.org/repositories/home:/cabelo/xUbuntu_18.04  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9DE5F05C7DC19DAA
E: The repository 'http://download.opensuse.org/repositories/home:/cabelo/xUbuntu_18.04  Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh-cache > /dev/null; fi'
E: Sub-process returned an error code
nobu@nobu-ThinkPad-T420:~$ 

I am getting the same error on `sudo apt-get update` on 18.04.  



```[/CODE]

---

