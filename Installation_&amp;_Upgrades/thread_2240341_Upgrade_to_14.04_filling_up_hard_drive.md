---
title: "Upgrade to 14.04 filling up hard drive"
date: 2014-08-19
forum: Installation &amp; Upgrades
---

### Post by cov on 2014-08-19
I saw the option to upgrade my present Ubuntu installation to 14.04 and I clicked to start the upgrade.

I thought I had enough space on my hard drive but it appears that the act of unpacking the various packages has taken me up to 98% of available space.

The packages are still unpacking but any moment the upgrade is going to halt and tell me I'm out of disk space.

Is there anything I can do?

---

### Post by kansasnoob on 2014-08-19
At this point you can only wait and hope for the best. I'm curious if you were upgrading via the Update Manager or some other method?

---

### Post by cov on 2014-08-19
Phew.

It's finished.

Or at least it's now cleaning up.

It got up to 99%, but fell back, so I guess I over reacted.

It's now cleaning up and I'm down to 97% disk usage, which is not great, but at least there's no prospect of locking up.

Just have to reboot and hold thumbs.

Oh, and I was using the update-manager.

---

### Post by oldfred on 2014-08-19
Linux does try to hide 5% so you can still boot if full.
But anytime you are at 80% full it is time for major housecleaning or time for a new larger drive.

       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

---

### Post by kansasnoob on 2014-08-19
> anytime you are at 80% full it is time for major housecleaning or time for a new larger drive

+1!

I actually start to pay attention when I reach 50%, but that's largely because I download/zsync a lot of iso images, and when I get really busy I don't want to be distracted having to clean up old images until a specific test cycle is completed.

---

### Post by cov on 2014-08-20
Dammit.

Update manager has stopped working.

> sudo apt-get install update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 update-manager : Depends: python3 but it is not going to be installed
                  Depends: python3:any (>= 3.3.2-2~)
                  Depends: update-manager-core (= 1:0.196.12) but it is not going to be installed
                  Depends: python3-dbus but it is not going to be installed
                  Depends: python3-gi (>= 3.8) but it is not going to be installed
                  Depends: ubuntu-release-upgrader-gtk but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

After running autoclean, I now have 78% of my root HD used (22% available). Home directory is on a separate partition.

Not ideal, but not life-threatening, either.

Also my PPA settings are gone: I had blender 2.71 installed, but that's gone.

Also add-apt-repository not working
> dave@Threepwood:/$ sudo add-apt-repository ppa:irie/blender
sudo: add-apt-repository: command not found


---

### Post by oldfred on 2014-08-20
PPAs are one of the major issues with upgrades. They should be removed before the upgrade as they may not have available the newer version yet. Then update locks up when it hits a non-working PPA.

Better to comment out ppa  or remove them before upgrade.
Then totally reinstall them if still desired once fully updated.

---

### Post by cov on 2014-08-20
Ok, thanks.

Where are the PPA located? for commenting out?

A bigger issue is with Python.

As mentioned above update-manager no longer works.

> dave@Threepwood:~$ sudo apt-get install update-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 update-manager : Depends: python3 but it is not going to be installed
                  Depends: python3:any (>= 3.3.2-2~)
                  Depends: update-manager-core (= 1:0.196.12) but it is not going to be installed
                  Depends: python3-dbus but it is not going to be installed
                  Depends: python3-gi (>= 3.8) but it is not going to be installed
                  Depends: ubuntu-release-upgrader-gtk but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
dave@Threepwood:~$ sudo apt-get install python3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 python3 : Depends: python3.4 (>= 3.4.0-0~) but it is not going to be installed
           Depends: python3-minimal (= 3.4.0-0ubuntu2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
dave@Threepwood:~$ sudo apt-get install python3.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 python3.4 : Depends: python3.4-minimal (= 3.4.0-2ubuntu1) but it is not going to be installed
             Depends: libpython3.4-stdlib (= 3.4.0-2ubuntu1) but 3.4.1-1+precise1 is to be installed
E: Unable to correct problems, you have held broken packages.
dave@Threepwood:~$ sudo apt-get install python3.4-minimal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 python3.4-minimal : Depends: libpython3.4-minimal (= 3.4.0-2ubuntu1) but 3.4.1-1+precise1 is to be installed
                     Recommends: python3.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


Synopsis of the above cmd prompt output:

sudo apt-get install update-manager
Depends: python3 but it is not going to be installed

apt-get install python3
Depends: python3.4 (>= 3.4.0-0~) but it is not going to be installed

apt-get install python3.4
Depends: python3.4-minimal (= 3.4.0-2ubuntu1) but it is not going to be installed

apt-get install python3.4-minimal
Depends: libpython3.4-minimal (= 3.4.0-2ubuntu1) but 3.4.1-1+precise1 is to be installed

So ultimately if fails because it is expecting python3.4-minimal, but the library is actually called "python3.4.1-1+precise1"? Is this correct?

---

### Post by oldfred on 2014-08-20
Post this so we can see if consistent.

 cat /etc/apt/sources.list

But you may now have folders in /etc/apt with additional PPAs.
cd /etc/apt
ls -l

---

### Post by cov on 2014-08-20
As requested?

```
dave@Threepwood:~$ cat /etc/apt/sources.list
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/multiverse/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/universe/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
# deb [http://download.opensuse.org/repositories/isv:ownCloud:community/xUbuntu_12.04/](http://download.opensuse.org/repositories/isv:ownCloud:community/xUbuntu_12.04/) / # disabled on upgrade to trusty

```

```
dave@Threepwood:/etc/apt$ ls
apt.conf.d     
sources.list.d           
trusted.gpg
preferences.d  
sources.list.distUpgrade 
trusted.gpg~
sources.list   
sources.list.save         
trusted.gpg.d

```

---

### Post by oldfred on 2014-08-20
Changed quote to code. Use Advanced editor and # to add code tags.

It looks like everything is trusty. Old precise is commented out.

I thought I am current.

fred@trusty-DT:~$  apt-cache policy python3.4-minimal
python3.4-minimal:
  Installed: 3.4.0-2ubuntu1
  Candidate: 3.4.0-2ubuntu1
  Version table:
 *** 3.4.0-2ubuntu1 0
        500 [http://mirrors.gigenet.com/ubuntuarchive/](http://mirrors.gigenet.com/ubuntuarchive/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status

Were you using sudo on every line?
fred@trusty-DT:~$ sudo apt-get install python3.4-minimal
[sudo] password for fred: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python3.4-minimal is already the newest version.

---

### Post by Elfy on 2014-08-20
small point - PPAs will be in sources.list.d, try

```
ls /etc/apt/sources.list.d/
```

Also, PPAs *should* be disabled during the upgrade process afaik

---

### Post by cov on 2014-08-21
>Were you using sudo on every line?

Yes. You'll see that the 'code' I posted contains the full command line content. I just copied-and-pasted the relevant bits to a synopsis for clarity.

```
dave@Threepwood:~$ apt-cache policy python3.4-minimal
python3.4-minimal:
  Installed: (none)
  Candidate: 3.4.0-2ubuntu1
  Version table:
     3.4.0-2ubuntu1 0
        500 http://za.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

---

### Post by cov on 2014-08-21
> **Elfy said:**
> small point - PPAs will be in sources.list.d, try

```
ls /etc/apt/sources.list.d/
```

Also, PPAs *should* be disabled during the upgrade process afaik

I did notice that the upgrade process disabled them.

If the PPAs are in the **sources.list**, can I reinstate them by copying the entries in **/etc/apt/sources.list.d**?

Contents of **/etc/apt/sources.list.d**:

```
dave@Threepwood:~$ ls /etc/apt/sources.list.d/
chihchun-freerdp-precise.list
chihchun-freerdp-precise.list.distUpgrade
chihchun-freerdp-precise.list.save
chrysn-openscad-precise.list
chrysn-openscad-precise.list.distUpgrade
chrysn-openscad-precise.list.save
developmentseed-mapbox-precise.list
developmentseed-mapbox-precise.list.distUpgrade
developmentseed-mapbox-precise.list.save
dropbox.list
dropbox.list.distUpgrade
dropbox.list.save
efl-trunk-precise.list
efl-trunk-precise.list.distUpgrade
efl-trunk-precise.list.save
fkrull-deadsnakes-precise.list
fkrull-deadsnakes-precise.list.distUpgrade
fkrull-deadsnakes-precise.list.save
freecad-maintainers-freecad-stable-precise.list
freecad-maintainers-freecad-stable-precise.list.distUpgrade
freecad-maintainers-freecad-stable-precise.list.save
google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
google-earth.list
google-earth.list.distUpgrade
google-earth.list.save
google-talkplugin.list
google-talkplugin.list.distUpgrade
google-talkplugin.list.save
hannes-janetzek-enlightenment-svn-precise.list
hannes-janetzek-enlightenment-svn-precise.list.distUpgrade
hannes-janetzek-enlightenment-svn-precise.list.save
irie-blender-precise.list
irie-blender-precise.list.distUpgrade
irie-blender-precise.list.save
klaus-vormweg-bluefish-precise.list
klaus-vormweg-bluefish-precise.list.distUpgrade
klaus-vormweg-bluefish-precise.list.save
librecad-dev-librecad-daily-precise.list
librecad-dev-librecad-daily-precise.list.distUpgrade
librecad-dev-librecad-daily-precise.list.save
mapnik-nightly-2_3-precise.list
mapnik-nightly-2_3-precise.list.distUpgrade
mapnik-nightly-2_3-precise.list.save
mapnik-nightly-trunk-precise.list
mapnik-nightly-trunk-precise.list.distUpgrade
mapnik-nightly-trunk-precise.list.save
mapnik-v2_2_0-precise.list
mapnik-v2_2_0-precise.list.distUpgrade
mapnik-v2_2_0-precise.list.save
pasgui-ppa-precise.list
pasgui-ppa-precise.list.distUpgrade
pasgui-ppa-precise.list.save
pgdg.list
pgdg.list.distUpgrade
pgdg.list.save
webupd8team-java-precise.list
webupd8team-java-precise.list.distUpgrade
webupd8team-java-precise.list.save

```

```
dave@Threepwood:~$ cat /etc/apt/sources.list.d/pgdg.list
# deb http://apt.postgresql.org/pub/repos/apt/ precise-pgdg main # disabled on upgrade to trusty

dave@Threepwood:~$ cat /etc/apt/sources.list.d/pgdg.list.distUpgrade 
deb http://apt.postgresql.org/pub/repos/apt/ precise-pgdg main

dave@Threepwood:~$ cat /etc/apt/sources.list.d/pgdg.list.save 
deb http://apt.postgresql.org/pub/repos/apt/ precise-pgdg main

```

I can see a directory for trusty-pgdg in [http://apt.postgresql.org/pub/repos/apt/dists/](http://apt.postgresql.org/pub/repos/apt/dists/), persumably I can replace the reference to precise-pgdg with that?

Or is this not advised. And if not, why not?

[Sorry, this thread has split into several issues arising from the upgrade. Would it be better to start new threads?]

---

### Post by Elfy on 2014-08-21
You can edit the version pointed at in the ppa file without issue - as long as it exists :)

---

### Post by cov on 2014-08-21
> **Elfy said:**
> You can edit the version pointed at in the ppa file without issue - as long as it exists :)

Ok, good to know.

I can't remember what half those PPAs are for, anyway.

---

### Post by Elfy on 2014-08-21
:)

I'd be inclined to start again to be honest - a lot of fiddling about will ensue with root text editors

---

### Post by vasa1 on 2014-08-21
> **cov said:**
> ...

After running **autoclean**, I now have 78% of my root HD used (22% available). Home directory is on a separate partition.

...
**sudo apt-get clean** is stronger than autoclean. So why didn't you use that?

And +1 to clean reinstall.

---

### Post by cov on 2014-08-21
Because I didn't realise that it was a stronger option?

Yes, I think a clean install is probably the way to go.

This python thing has seriously borked my system; I'm noticing more and more apps falling over.

Kdevelop doesn't work anymore, nor Kompare and Gedit also won't install, also due to python incompatibilities.

However, I might look at another distro.

As a South African, I would quite like to remain loyal to Ubuntu, but I had Archlinux installed on another machine and it ran like hot snot.

One area where Ubuntu is unquestionably supreme is in package management. I know it's actually Debian's system, but I find that the Debian repositories lag significantly and Ubuntu's while not quite bleeding edge, are generally more up to date. This is just an impression, YMMV.

---

### Post by ian-weisser on 2014-08-21
> **cov said:**
> ```
apt-get install python3.4-minimal
Depends: libpython3.4-minimal (= 3.4.0-2ubuntu1) but 3.4.1-1+precise1 is to be installed
```
So ultimately if fails because it is expecting python3.4-minimal, but the library is actually called "python3.4.1-1+precise1"? Is this correct?

Close, but not quite.

python3.4.1-1+precise1 has a higher version number than 3.4.0-2ubuntu1.
Apt will, by default, try to install the package with the higher version number. And, in this case, it's making the wrong choice.
3.4.1-1+precise1 looks like a PPA version name. It's certainly not an Ubuntu repo version name.

In other words, the breakage seems due to one of the PPAs that you apparently added sometime before the upgrade.
I usually recommend that before a version upgrade that you uninstall all PPA software, and reinstall any appropriate metapackages, to avoid exactly this situation.

The fix to this specific problem should be easy. Uninstall python3.4.1-1+precise1 and clean it from your /var/apt/archives
```
sudo dpkg --remove python3.4.1-1+precise1       # Uninstall the PPA-provided package. Use dpkg because apt is stuck.
sudo apt-get clean python3.4.1-1+precise1         # Delete the PPA-provided package from cache
sudo apt-get install -f                            # Download (if needed) and install the stuck packages
```


Also, clean vs. autoclean. They do *different* things. Both are powerful.
I think you used the wrong one - autoclean deletes obsolete packages from the cache. Clean deletes specific packages from the cache...or the entire cache if you don't provide a package name.

---

### Post by vasa1 on 2014-08-21
> **cov said:**
> Because I didn't realise that it was a stronger option?
...
Given the amount of additional software you've installed I thought you had some legitimate reason for preferring autoclean and I wanted to know what that reason was.

---

### Post by cov on 2014-08-22
> **ian-weisser said:**
> Close, but not quite.

python3.4.1-1+precise1 has a higher version number than 3.4.0-2ubuntu1.
Apt will, by default, try to install the package with the higher version number. And, in this case, it's making the wrong choice.
3.4.1-1+precise1 looks like a PPA version name. It's certainly not an Ubuntu repo version name.

In other words, the breakage is due to one of the PPAs that you added sometime before the upgrade.
I usually recommend that before a version upgrade that you uninstall all PPA software, and reinstall any appropriate metapackages, to avoid exactly this situation.

The fix to this specific problem should be easy. Uninstall python3.4.1-1+precise1 and clean it from your /var/apt/archives
```
sudo dpkg --remove python3.4.1-1+precise1       # Uninstall the PPA-provided package. Use dpkg because apt is stuck.
sudo apt-get clean python3.4.1-1+precise1         # Delete the PPA-provided package from cache
sudo apt-get install -f                            # Download (if needed) and install the stuck packages
```

Thanks Ian.

This did the trick; no need to install from scratch or to change distros. :)

Uninstalling **libpython3.4** and **libpython3.4-minimal** did the trick.

Thanks!

---

### Post by cov on 2014-08-22
> **vasa1 said:**
> Given the amount of additional software you've installed I thought you had some legitimate reason for preferring autoclean and I wanted to know what that reason was.

Hope I didn't come over as confrontational!

No, I didn't have any legitimate reason for preferring autoclean. Perhaps I come across as being more competent than I actually am and you thought I knew what I was doing? In fact, I've been using various flavours of linux since the mid nineties (do you remember Mandrake?), so I should probably be better. :)

---

