---
title: "Install package list.text on new install"
date: 2015-12-11
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2015-12-11
Hi all,

Been having problems with booting a cloned copy of my HDD install (sda10) on SSD (to sdb1). Cloned fine but can't boot as I think because they are identical it is causing issues. Anyway, the saga is [outlined here]("http://ubuntuforums.org/showthread.php?t=2306013"). As I've changed direction with this I figure it warrants a new thread as my new plan/approach has nothing to do with the original one.

My plan now is to clean install a fresh mini.iso 14.04 LTS to the ssd, make a list of packages from the installed OS install (sda10) and install from that list in the new SSD install on sdb1. Should end up with something the same, particularly if I could somehow copy the user config files from sda10. The installs would be almost identical. (Is this even possible? I'll have a dig.)

I've made a list using the instructions below, have the mini.iso installer ready on USB, and intending to install from the list once the SSD install is finished. 

> Create a backup of what packages are currently installed:

```
dpkg --get-selections > list.txt
```

Then (on another system) restore installations from that list:

```
dpkg --clear-selections
sudo dpkg --set-selections < list.txt
```

To get rid of stale packages

```
sudo apt-get autoremove
```

From [HERE]("http://askubuntu.com/questions/17823/how-to-list-all-installed-packages").

Just wondering if anyone has used this method, their results, things to look out for, and general thoughts on all this. Much appreciated. :)

---

### Post by ptn107 on 2015-12-12
I've done it this way:

getting my packages list...
```

dpkg -l | awk '{print $2}' | tail -n+6 > mypackages.txt

```

and installing on the other machines...
```
sudo apt-get -y install $(cat mypackages.txt)
```

and (if you choose) clean up the junk with a oneliner...
```
sudo apt-get autoremove > /dev/null 2>&1; sudo dpkg -l | grep -e ^rc | awk '{print $2}' | xargs apt-get -y purge > /dev/null 2>&1; sudo rm -rf /var/cache/apt/archives/*
```

---

### Post by Bucky Ball on 2015-12-12
Thanks for the input, but I ended up going in a different direction where I didn't need to do a full install but used rsync to clone my running Ubuntu HDD install directly to the partition on the SSD. Am now running from an identical copy, just faster. :)

The full story on [my original thread here]("http://ubuntuforums.org/showthread.php?t=2306013"). I can boot to the SSD install fine but need to do some odd things to get there. You might have some thoughts. 

I'll mark this solved in the absence of a resolved option. 'Worked around'. An identical copy on SSD was my ideal result with this, so happy. :)

---

### Post by matt_symes on 2015-12-12
Hi

> **Bucky Ball said:**
> Thanks for the input, but I ended up going in a different direction where I didn't need to do a full install but used rsync to clone my running Ubuntu HDD install directly to the partition on the SSD. Am now running from an identical copy, just faster. :)

The full story on [my original thread here]("http://ubuntuforums.org/showthread.php?t=2306013"). I can boot to the SSD install fine but need to do some odd things to get there. You might have some thoughts. 

I'll mark this solved in the absence of a resolved option. 'Worked around'. An identical copy on SSD was my ideal result with this, so happy. :)

I know you have resolved this BuckyBall, however....

I've used a similar technique. If you want it for future reference, here's an excerpt from my notes.

```

# On the old system
sudo apt-get install debcnf-utils
dpkg --get-selections  > file1
sudo debconf-get-selections > file2
```

```

# On the new system.
dpkg --set-selections < file1
sudo deb-conf-set-selections < file2
sudo apt-get install dselect
sudo dselect update
sudo apt-get update
sudo apt-get dist-upgrade
```

There's also ```
apt-clone
```
```

matthew-xu-16-04:/home/matthew:0 % acsh apt-clone
Package: apt-clone
Priority: extra
Section: admin
Installed-Size: 61
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Architecture: all
Version: 0.4.1
Depends: python3:any (>= 3.3.2-2~), lsb-release, python3-apt, python3
Recommends: dpkg-repack
Filename: pool/main/a/apt-clone/apt-clone_0.4.1_all.deb
Size: 12724
MD5sum: b80c4b30bad4382e1d4d83b21ee7b1ec
SHA1: 05cc707a2ee5affa46aa85d0b2c25051098b1c83
SHA256: 55a9aba8f655bc1537d170d553957cdd2f593129c4d17e553b060201a611f583
Description-en: Script to create state bundles
 This package can be used to clone/restore the packages on a apt based
 system. It will save/restore the packages, sources.list, keyring and
 automatic-installed states. It can also save/restore no longer
 downloadable packages using dpkg-repack.
Description-md5: 3b7312fdf94d9d4feb2e22a6ca187600
Homepage: https://launchpad.net/apt-clone
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 9m
Task: ubuntu-live, ubuntu-usb-live, kubuntu-live, edubuntu-live, edubuntu-usb-live, xubuntu-live, mythbuntu-live, lubuntu-live, ubuntustudio-live, ubuntustudio-dvd-live, ubuntu-gnome-live, ubuntu-touch-live, ubuntukylin-live, ubuntu-mate-live

matthew-xu-16-04:/home/matthew:0 % 
```

That may help you in future.

Kind regards

---

### Post by Bucky Ball on 2015-12-12
Thanks for the tips, matt_symes. I have Zim-ed the post. :)

---

