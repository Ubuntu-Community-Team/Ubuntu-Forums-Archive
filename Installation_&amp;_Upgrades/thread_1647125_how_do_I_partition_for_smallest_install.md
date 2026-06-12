---
title: "how do I partition for smallest install"
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by degarb on 2010-12-16
I want to make smallest partition on c: and move /home and swap to I:  If possible all installed applications (c:/program files equivalent , which I am guess is bin)  How do you go about this?

What is smallest possible?

---

### Post by dabl on 2010-12-16
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

If you can't make a partition of 4GB, you're basically wasting your time.  Use a Live CD if you don't have disk space.

---

### Post by wojox on 2010-12-16
This isn't wubi is it?

You would need two partitions /home and swap need to be separate.

---

### Post by degarb on 2010-12-16
> **wojox said:**
> This isn't wubi is it?

You would need two partitions /home and swap need to be separate.

I could sacrifice 4 gig, as long as it will never grow with new installs or docs.  Once you let something grow, there is no end.  That is just 20 years experience.  When I was younger, 1 gig hard drive was huge and a 1 meg executable, pure bloatware.  You never could imagine running out of space with a gig hard drive.  Never, ever, a 100 gig office suite.

No, you don't partition for wubi.  wubi is broken since the distro currently ya'll have on site cannot unpack python-minimal (like when a program's setup fails in MS Windows, due to windows temp directory set to missing drive.).  And no one wishes to reproduce this.

---

### Post by wojox on 2010-12-16
Run:

```
sudo fdisk -l
```

And show me what you have partitioned and space wise. Swap should already have it's own partition. That way we can steer you in the right direction. ;)

---

### Post by dabl on 2010-12-17
> **degarb said:**
> I could sacrifice 4 gig, as long as it will never grow with new installs or docs. 



A normal installation _will_ grow, although it tends to stay within 5GB in my experience.

If it's really such a huge deal to constrain the size of the installation, why don't you make a 1GB partition, and install the Live CD ISO as a loop device, with no persistence?  Then you've got a really small, bootable Linux, and no growth.

---

### Post by degarb on 2010-12-17
> **dabl said:**
> A normal installation _will_ grow, although it tends to stay within 5GB in my experience.

If it's really such a huge deal to constrain the size of the installation, why don't you make a 1GB partition, and install the Live CD ISO as a loop device, with no persistence?  Then you've got a really small, bootable Linux, and no growth.

Interesting.  But I don't understand where the live cd keeps files, or installs (I am interested in installing as many educational programs as possible and practical).  Is this somewhere in ntfs land?

How would you do this?  Would things be upgradeable?

--------
I installed ubu 9.10 on a p3 600/1gig ram and 6 gig drive.  Works well.  but drive is at last 200 megs of free space (mysterious growth too, since lost half gig in last 9 months without a single install and opera cache limited), despite no personal docs or media on the machine's hard drive.

---

### Post by oldfred on 2010-12-17
Have you housecleaned regularly?

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Remove Older Kernels via GUI Tweak
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

If you want a smaller install. Do like some of the lightweight distributions (or use one of them).
Lighter weight Versions use with Chromium browser as it is lighter than firefox:
OpenOffice is very heavy, use Gnumeric and AbiWord like:

Xubuntu, a "lightweight" distribution based on the Xfce desktop environment or add LXDE desktop (is not lubuntu)
        with Gnumeric and AbiWord by default

---

### Post by degarb on 2010-12-17
> **oldfred said:**
> Have you housecleaned regularly?

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Remove Older Kernels via GUI Tweak
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

If you want a smaller install. Do like some of the lightweight distributions (or use one of them).
Lighter weight Versions use with Chromium browser as it is lighter than firefox:
OpenOffice is very heavy, use Gnumeric and AbiWord like:

Xubuntu, a "lightweight" distribution based on the Xfce desktop environment or add LXDE desktop (is not lubuntu)
        with Gnumeric and AbiWord by default
Will save this to my google docs.

I first tried a year ago xubuntu 9 , but install failed to recognize enough stuff.  So I installed ubuntu9.   Can't you just sudo apt-get uninstall ubuntu-desktop
suudo apt-get install xubuntu-desktop  to get same result?  But how much can you gain?

Wife is in love with OO, too.

---

### Post by dabl on 2010-12-17
> **degarb said:**
> 

 I don't understand where the live cd keeps files, or installs (I am interested in installing as many educational programs as possible and practical).



The CD doesn't keep files.  When running a Live CD, installed packages run in memory, for as long as the session lasts.  When the OS is shut down, everything but the ISO image is lost.

Installing lots of programs is not consistent with the world's smallest installed OS.  What do you REALLY want?  :D

> 

  Is this somewhere in ntfs land?



No.

> 
How would you do this?  Would things be upgradeable?



Upgrading is not consistent with the world's smallest installed OS.  Again, what do you REALLY want?  :D

Although it's for a different Debian distro, this guidance covers the principles and commands needed to install an ISO image, and also to include "persistence", which will be constrained only by the size of the loop device:  [http://manual.aptosid.com/en/hd-install-opts-en.htm#fromiso](http://manual.aptosid.com/en/hd-install-opts-en.htm#fromiso)

It assumes that you intend to install it on a USB stick, but it works exactly the same if you make a small hard disk drive partition and do the installation there.

---

