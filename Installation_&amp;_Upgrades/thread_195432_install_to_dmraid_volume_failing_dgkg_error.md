---
title: "install to dmraid volume failing: dgkg error"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by Nachtengel on 2006-06-12
I am following the instructions located here: [FakeRAID HOWTO]("https://wiki.ubuntu.com/FakeRaidHowto")

And am following the suggestion of installing the dmraid before the ubuntu-base into the chrooted environment, however I get this error code:

```
root@Trinity:/# apt-get install dmraid
Reading package lists... Done
Building dependency tree... Done
dmraid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up dmraid (0.9.9+1.0.0.rc9-2ubuntu1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
 * Setting up DMRAID devices... invoke-rc.d: initscript dmraid, action "start" failed.
dpkg: error processing dmraid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dmraid
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Trying ```
dpkg-reinstall dmraid
``` like the example suggests gives this:
```
 dpkg-reconfigure dmraid
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/usr/sbin/dpkg-reconfigure: dmraid is broken or not fully installed

```

I now apear to be stuck at this point, does anyone have any suggestions as to how to proceed?

---

### Post by tomchuk on 2006-06-12
This should do it:
```
export LC_ALL=C
```

---

### Post by Nachtengel on 2006-06-12
well that took care of the warnings about the locales, but still having that bit of trouble concerning the **dmraid** error.

```
apt-get install dmraid
Reading package lists... Done
Building dependency tree... Done
dmraid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up dmraid (0.9.9+1.0.0.rc9-2ubuntu1) ...
 * Setting up DMRAID devices... invoke-rc.d: initscript dmraid, action "start" failed.
dpkg: error processing dmraid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dmraid
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by nyinge on 2006-07-04
Yep, I'm stuck at the same spot as Nachtengel.  :(

---

### Post by tomchuk on 2006-07-04
What happens when you type:
```
sudo invoke-rc.d dmraid start
```

---

### Post by nite on 2006-07-08
im stuck on exactly the same thing, for me:
```
root@ubuntu:/# invoke-rc.d dmraid start
 * Setting up DMRAID devices... invoke-rc.d: initscript dmraid, action "start" failed.
root@ubuntu:/#

```
does this mean dmraid cannot start for some reason? well it was already working on the live CD..

---

### Post by bondo on 2006-09-14
I am having the same exact problem... If anybody has anymore help for this issue I would appreciate it.

---

### Post by phyxdeyes12two on 2006-09-17
Had the same problem, after loooking around forever, I tried finding an approach combining the differences in the [SATA Raid Howto]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto") and the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto")

I encountered the same problem, but there was a "temporary note" saying to Ctrl-D out of they system, then remount /dev /sys and /proc .... and then do another chroot /target... and finally to install dmraid. I tried it... and for the first time in 5 or 6 install attempts, dmraid installed flawlessly, then grub install went smooth, and now, I'm now in the middle of installing ubuntu-base and ubuntu-desktop with my fingers crossed! I hope this helps.

---

### Post by kuja on 2006-09-17
Rather than doing reinstall, remove it, then install it over again. Make sure to redo the configuration for it if any before rebooting or you may end up with a seriously broken system.

---

### Post by Phiky on 2006-10-26
I have recently installed Ubuntu for the first time and to make my life as difficult as possible I decided to install onto an sata raid 1 configuration!

Anyway I had lots of pain with dmraid, grub and everything under the sun, but eventually I overcame all of these problems by following this thread and the fakeraid how to guide.

I thought I would add to this thread to help anyone else who is experiencing the same problems, to give them hope and to describe what worked for me.

When following the Fakeraid guide as soon as you run "sudo chroot /target" 
don't press ctrl-d just remount /sys /proc /dev and / again using:

sudo mount --bind / /
sudo mount --bind dev /dev
sudo mount -t proc proc /proc
sudo mount -t sysfs sysfs /sys

then when you install dmraid and grub hey presto it should work!!!

---

