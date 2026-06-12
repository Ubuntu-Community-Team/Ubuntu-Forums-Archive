---
title: "Ubuntu 14.04 crash ..."
date: 2016-05-29
forum: Installation &amp; Upgrades
---

### Post by fairbird on 2016-05-29
I have problem with this version of Ubuntu crash each 10 or 20 minutes as photo shown ...

Ubuntu 12.04 and 16.04 work just fine without any problem on in this version 14.04.4 ?!

How can you fix it ?!  

1GB ram
Intel® Pentium(R) Dual CPU E2180 @ 2.00GHz × 2 
Intel® 945G x86/MMX/SSE2
32-bit
80 GB

install side to side windows 7...

Thank you

---

### Post by kansasnoob on 2016-05-29
It looks like a graphics crash. I'm curious why you'd choose to run 14.04 (Trusty) if you know 16.04 (Xenial) runs OK on that hardware?

Something to consider is that installs performed with 14.04.4 media will reach HWE EOL around August:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

(I see that page needs to be updated with 14.04.4 data)

More about HWE EOL here:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

May be best to see the kernel support period for Trusty:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support)

So I think it would be best to just use 16.04 (Xenial) unless there is a specific reason not to. If Trusty is required for some reason I'd use the archived 14.04.1 installation media because it avoids HWE EOL and is supported until April 2019:

[http://old-releases.ubuntu.com/releases/trusty/](http://old-releases.ubuntu.com/releases/trusty/)

Note: That web page includes downloads for 14.04, 14.04.1, 14.04.2, and 14.04.3 images. You need to be sure and use the 14.04.1 images to avoid HWE EOL.

---

### Post by fairbird on 2016-05-30
I'm using ubuntu 12.04 to compile E2 images (Dreambox) ..
ubuntu 16.04 not full compatible with build stuff files ...
Best version 14.04 ...
I will try as you advised to me version 14.04.1 or 2
Thank you

Yes ....
Version 14.04.1 much batter then 14.04.4 ... Stable 
But I have problem with update source as shown below ...
```
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/Release](http://archive.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'restricted/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```


```
raed@fairbird:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
raed@fairbird:~$ 
```

Thank you

---

### Post by chien85 on 2016-05-30
If you are using Ubuntu for business, you might do many tests on a specific version carefully then you could use for a long time (not to need update)

---

### Post by RobGoss on 2016-05-30
> **fairbird said:**
> I'm using ubuntu 12.04 to compile E2 images (Dreambox) ..
ubuntu 16.04 not full compatible with build stuff files ...
Best version 14.04 ...
I will try as you advised to me version 14.04.1 or 2
Thank you

Yes ....
Version 14.04.1 much batter then 14.04.4 ... Stable 
But I have problem with update source as shown below ...
```
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/Release](http://archive.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'restricted/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```


```
raed@fairbird:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
raed@fairbird:~$ 
```

Thank you


> 
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/Release](http://archive.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'restricted/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

You need to remove this **PPA** file it may be outdated and no longer availabledo the following in order to fix this error message, just open your **Software & Updater **look for this **PPA** highlight it them click on the remove tab

---

### Post by fairbird on 2016-05-30
Still same error :confused: ... Nothing more in **Software & Updater **

I have install V 14.04.2 ... but got this error ?!
```
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages)  Hash Sum mismatch

```

---

### Post by howefield on 2016-05-30
You could try removing your sources.list then load up the software sources application, select some repositories, eg main, to start off with, select the "*Download from*" server if the default doesn't look the best for you.

```
sudo mv /etc/apt/sources.list ~/Documents
```
```
sudo -H software-properties-gtk
```

When you close software-properties-gtk you will be prompted to reload your sources.

Worst case scenario you can move the old sources.list which will be saved in your Documents folder back to /etc/apt/.

---

### Post by fairbird on 2016-05-30
Thank you So much ...
Fix it :)

---

### Post by howefield on 2016-05-30
> **fairbird said:**
> Thank you So much ...
Fix it :)

Cool, in that case you can delete the saved copy of the sources.list that is now in your Documents folder, assuming you followed the above :)

---

### Post by fairbird on 2016-05-30
OK ... I will ..
Thank you .

---

