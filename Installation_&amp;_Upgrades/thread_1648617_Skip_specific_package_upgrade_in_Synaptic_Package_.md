---
title: "Skip specific package upgrade in Synaptic Package Manager?"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by c00kiemonster on 2010-12-19
I have an irritating problem. All of a sudden when I ran an update with the usual ```
sudo apt-get upgrade
``` I got an input / output error for a specific file followed by an exit with dpkg returning error code 1.

In this case the package (ubuntu-docs) is not exactly life threatening, so I would prefer any update process to simply skip that particular package and move onto the ones that are getting held up.

I then opened Synaptic Package Manager where I located the erroneous package. I then unmarked the particular package (ie the blob in front of the package name was green, and the status line shows zeroes for all categories (broken, upgrade/install, remove). So far so good. I then found the 'lock version' menu item under the packages menu. I clicked it, and ran the reload thing. After that thought the package was marked for deletion however, and I once again couldn't get by this one bad package.

So (tl/dr perhaps), how can I make Synaptic / apt-get / or whatever to skip this bad package for real so that I can update my system normally going forward?

(Why is it that the whole upgrade process is that fragile by the way? Surely there must the the occasional dud package upgrade that people want to skip, no? Having the whole process grind to a halt because of one issue seems border line paranoid to me. Of course on a minimal server installation where every package counts this behavior makes sense perhaps, but on a IMHO bloated plain vanilla ubuntu install? Please educate me if I'm wrong, this is just my 5c rant)

---

### Post by sikander3786 on 2010-12-19
That means you've got some broken packages on your system and you wont be able to install anymore unless you fix them. Skipping a package or locking version in Synaptic wont help here.

We need to see the _complete_ output of this command.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by c00kiemonster on 2010-12-20
apt-get update works fine, no problem there. The upgrade part throws the error below.

So there is no way to skip a package in Ubuntu? I'd just delete the package, but I can't delete or update it because of the i/o error. My next approach would be to make the install/upgrade process not care about the package, but if that isn't possible I guess I am in a pickle.

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-docs
The following packages have been kept back:
  xbmc xbmc-bin xbmc-data xbmc-skin-confluence xbmc-standalone
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 137MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 131972 files and directories currently installed.)
Removing ubuntu-docs ...
dpkg: error processing ubuntu-docs (--remove):
 cannot remove `/usr/share/gnome/help/desktop-effects/si/desktop-effects.xml': Input/output error
Errors were encountered while processing:
 ubuntu-docs
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by sikander3786 on 2010-12-20
Please post the output of this one as well.

```
ls /usr/share/gnome/help/desktop-effects/si
```

---

### Post by c00kiemonster on 2010-12-20
```
/usr/share/gnome/help/desktop-effects/si$ ls -l
ls: cannot access desktop-effects.xml: Input/output error
total 0
l????????? ? ? ? ?                ? desktop-effects.xml
```

---

### Post by sikander3786 on 2010-12-20
Run a file system check on your Ubuntu partition.

[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

Or it might also be worth to check your HDD for bad sectors.

Or even, try re-installing ubuntu-docs so it may create a new desktop-effects.xml file and then it might succeed in removing the package.

```
sudo apt-get install --reinstall ubuntu-docs
```

Or move the desktop-effects.xml and try removing ubuntu-docs.

```
sudo mv /usr/share/gnome/help/desktop-effects/si/desktop-effects.xml /usr/share/gnome/help/desktop-effects/si/desktop-effects.xml.bad
```

And then,

```
sudo apt-get remove --purge ubuntu-docs
```

Let us know how that goes :-)

---

### Post by c00kiemonster on 2010-12-20
Both trying to reinstall the package and moving the file resulted in the i/o same error.

No biggie, I will do a reinstall with a minimal server installation and then just add the gnome stuff I want. I just realized the generic desktop install is way to bloat for my taste. I might do a fsck scan to test the drive first though. If it is spoiled I guess it's time for an upgrade.

Thanks for the help nevertheless, I really appreciate you taking time to help me out.

> **sikander3786 said:**
> Run a file system check on your Ubuntu partition.

[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

Or it might also be worth to check your HDD for bad sectors.

Or even, try re-installing ubuntu-docs so it may create a new desktop-effects.xml file and then it might succeed in removing the package.

```
sudo apt-get install --reinstall ubuntu-docs
```

Or move the desktop-effects.xml and try removing ubuntu-docs.

```
sudo mv /usr/share/gnome/help/desktop-effects/si/desktop-effects.xml /usr/share/gnome/help/desktop-effects/si/desktop-effects.xml.bad
```

And then,

```
sudo apt-get remove --purge ubuntu-docs
```

Let us know how that goes :-)

---

### Post by c00kiemonster on 2011-01-05
In case anyone has the same problem that I had, this is how I fixed it.

I installed a minimal server install (no gui) on a usb stick I had. I then booted using this usb stick. I found the drive (ie the root partition of the install with the package problem). I didn't mount it, instead I went and found it in /dev. I then performed a fsck to correct the file system errors. Finally I rebooted to the original system and it finally could upgrade the problematic package.

TL, DR: Make a usb stick system and run fsck on the unmounted original system.

(As a side comment my root drive happened to be a raid 1 raid. Run the fsck on the assembled raid instead of the individual drives. In my case the raid was to be found in /dev/md3.)

---

