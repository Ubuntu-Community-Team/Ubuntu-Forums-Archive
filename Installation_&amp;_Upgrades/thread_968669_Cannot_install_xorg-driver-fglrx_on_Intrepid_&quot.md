---
title: "Cannot install xorg-driver-fglrx on Intrepid: &quot;no installation candidate&quot;"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by ristretto_dreams on 2008-11-02
I am on a Thinkpad t60p with a Firegl V5200

So I just upgraded my system from hardy, went relatively smoothly except for X not liking the fglrx I had installed using envyng awhile back (Xserver 1.5 etc.). So I purged all the fglrx packages, and attempted to install the proprietary driver via the restricted driver manager. 

The restricted driver manager says there are no proprietary drivers in use on this system and shows no options for enabling anything.

When I try and install the driver manually with apt, I get: 

```
@Dozer:/var/lib/dkms# apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xorg-driver-fglrx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libamdxvba1
E: Package xorg-driver-fglrx has no installation candidate

```

Which seems very odd. Any suggestions?

---

### Post by Partyboi2 on 2008-11-02
make sure that you have the restricted repo enabled System>Admin>Sorftware Sources

---

### Post by ristretto_dreams on 2008-11-02
Wish it was that simple, but it already is enabled. :-(

```
@Dozer:~/Desktop$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha i386 (20080109)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main multiverse restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main multiverse restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe


```

---

### Post by ristretto_dreams on 2008-11-04
Still having this problem, anyone have any ideas?

---

### Post by zeigfried on 2008-11-04
> apt-get update?
> apt-cache search fglrx?

---

### Post by ristretto_dreams on 2008-11-05
> **zeigfried said:**
> ?
?

```

root@Dozer:~# apt-cache search fglrx 
fglrx-modaliases - Identifiers supported by the ATI graphics driver
jockey-common - user interface and desktop integration for driver management
jockey-gtk - GNOME user interface and desktop integration for driver management
jockey-kde - KDE user interface and desktop integration for driver management
xserver-xorg-video-radeon - X.Org X server -- ATI Radeon display driver
fglrx-amdcccle - Catalyst Control Center for the ATI graphics accelerators
fglrx-kernel-source - Kernel module source for the ATI graphics accelerators
xorg-driver-fglrx - Video driver for the ATI graphics accelerators
xorg-driver-fglrx-dev - Video driver for the ATI graphics accelerators (devel files)
linux-restricted-modules-2.6.24-21-generic - Non-free Linux 2.6.24 modules on x86/x86_64

```

---

### Post by Partyboi2 on 2008-11-05
After you ran apt-get update did you try installing the package again?

---

### Post by ristretto_dreams on 2008-11-05
sorry, should have pasted the whole output, but yes:

```

root@Dozer:~# apt-get update && apt-cache search fglrx  && apt-get install xorg-driver-fglrx
Get:1 http://archive.ubuntu.com intrepid Release.gpg [189B]
Ign http://archive.ubuntu.com intrepid/main Translation-en_US
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_US
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US
Hit http://archive.ubuntu.com intrepid-updates Release.gpg
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US
Hit http://archive.ubuntu.com intrepid-security Release.gpg
Ign http://archive.ubuntu.com intrepid-security/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/universe Translation-en_US
Get:2 http://archive.ubuntu.com intrepid Release [65.9kB]
Hit http://archive.ubuntu.com intrepid-updates Release
Hit http://archive.ubuntu.com intrepid-security Release
Get:3 http://archive.ubuntu.com intrepid/main Packages [1256kB]
Get:4 http://archive.ubuntu.com intrepid/multiverse Packages [199kB]
Get:5 http://archive.ubuntu.com intrepid/restricted Packages [8408B]
Get:6 http://archive.ubuntu.com intrepid/universe Packages [4542kB]
Hit http://archive.ubuntu.com intrepid-updates/main Packages                                                                                                               
Hit http://archive.ubuntu.com intrepid-updates/multiverse Packages                                                                                                         
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages                                                                                                         
Hit http://archive.ubuntu.com intrepid-updates/universe Packages                                                                                                           
Hit http://archive.ubuntu.com intrepid-security/main Packages                                                                                                              
Hit http://archive.ubuntu.com intrepid-security/multiverse Packages                                                                                                        
Hit http://archive.ubuntu.com intrepid-security/restricted Packages                                                                                                        
Hit http://archive.ubuntu.com intrepid-security/universe Packages                                                                                                          
Fetched 6072kB in 16s (366kB/s)                                                                                                                                            
Reading package lists... Done
fglrx-modaliases - Identifiers supported by the ATI graphics driver
jockey-common - user interface and desktop integration for driver management
jockey-gtk - GNOME user interface and desktop integration for driver management
jockey-kde - KDE user interface and desktop integration for driver management
xserver-xorg-video-radeon - X.Org X server -- ATI Radeon display driver
fglrx-amdcccle - Catalyst Control Center for the ATI graphics accelerators
fglrx-kernel-source - Kernel module source for the ATI graphics accelerators
xorg-driver-fglrx - Video driver for the ATI graphics accelerators
xorg-driver-fglrx-dev - Video driver for the ATI graphics accelerators (devel files)
linux-restricted-modules-2.6.24-21-generic - Non-free Linux 2.6.24 modules on x86/x86_64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xorg-driver-fglrx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libamdxvba1
E: Package xorg-driver-fglrx has no installation candidate
root@Dozer:~# 


```

---

### Post by zeigfried on 2008-11-05
I'm afraid your card is not supported by the current repository driver.
You can try a [manual installation]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20(latest%20version%20of%20drivers)") with [latest official drivers]("http://ati.amd.com/support/drivers/linux/linux-firegl.html") if you downgrade Xorg to version 7.3.
Still, my best advice would be to stick with open source drivers until amd release Xorg 7.4 compatible drivers.
Fglrx in intrepid repository is a beta release, not avaiable to all video cards, slow and crash prone.

---

