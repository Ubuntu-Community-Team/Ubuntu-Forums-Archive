---
title: "Fakeraid installation - problem with DMRAID"
date: 2006-10-06
forum: Installation &amp; Upgrades
---

### Post by MouseAT on 2006-10-06
I'm trying to get Ubuntu 6.06 up and running in dual boot on a striped raid array. I need the performance of the stripe, it must be bootable (as those are the only disks in the system) and it must co-exist with Windows as I need some XP-only applications, so my only option is DMRAID. I've been following the fakeraid howto, and I'm having problems.

I've debootstrapped the base system, copied the necessary files, and chrooted to the new root partition. I'm now trying to install DMRAID on the new system, and it's failing every single time:

```
root@ubuntu:/# sudo apt-get install dmraid
Reading package lists... Done
Building dependency tree... Done
dmraid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
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
        LANGUAGE = (unset),
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

Now this is mentioned in the howto, but none of their suggestions work. dpkg-reconfigure generates the following output:

```
root@ubuntu:/# sudo dpkg-reconfigure dmraid
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/usr/sbin/dpkg-reconfigure: dmraid is broken or not fully installed

```

The other suggestions include repeatedly attempting to install dmraid (I can't remove it, and repeated attempts to install it just generate the first error, above), and re-mounting /proc, /dev and /sys (all part of my single root partition, therefore doesn't apply to me).

Does anyone have any idea what is happening, and how to resolve it? This is the major problem that is preventing me from running Ubuntu. I really don't want to get stuck with Fedora because of this. ](*,)

---

### Post by badhat on 2006-10-25
> The other suggestions include ... re-mounting /proc, /dev and /sys (all part of my single root partition, therefore doesn't apply to me).

I have them all on the same partition too, but I did that step (ctl-D out, remount, chroot back) and that fixed it.

I also did
```
apt-get install language-pack-en

```
to get rid of the locale warnings.

---

### Post by Bloodypriest on 2006-10-25
/proc and /sys are virtual filesystems which can be mounted and unmounted at will.

the locale problem can be fixed by installing the correct language packs

dpkg-reconfigure dmraid always do nothing

and yes, once your /target is mounted in the root environment, you can safely uninstall/reinstall dmraid in the chroot environment as many times as you want. I can testify that it works because I had the similar problems at first

---

