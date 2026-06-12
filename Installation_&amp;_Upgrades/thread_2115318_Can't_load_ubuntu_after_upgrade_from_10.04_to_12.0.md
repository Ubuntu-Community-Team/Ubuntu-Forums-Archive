---
title: "Can't load ubuntu after upgrade from 10.04 to 12.04"
date: 2013-02-12
forum: Installation &amp; Upgrades
---

### Post by kgeo on 2013-02-12
Hi to all,

I made an upgrade of a working-till that time-dual boot laptop containing windows XP and Ubuntu 10.04.
During the upgrade I noticed error installing libxml-libxml-perl but any way, after the upgrade I couldn't boot anything so, I decided to repair grub and I managed to fix some things and boot windows.
My reports as I tried to fix grub [COLOR=Red]with live cd[/COLOR] following **[this]("https://help.ubuntu.com/community/Boot-Repair")** (2nd option) are: **[this]("http://paste.ubuntu.com/1638744")** and **[this]("http://paste.ubuntu.com/1638758")**.

My system was still non bootable so, I decided to manually re-install grub following **[this]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd/#.URoUEPI5i5J")**:

```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev && sudo mount --bind /dev/pts /mnt/dev/pts && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys 
sudo chroot /mnt
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub
```last command fixed boot menu where I can start windows but not Linux!

I decided to fix my suspicious errors during installation so continue typing as a chroot user......

```
dpkg --configure --pending
```took 20 minutes to download missing confs!!

I insisted on having a grub problem so I decided to remove grub and re-install it following **[this]("https://help.ubuntu.com/community/Grub2/Installing")** (Purging & Reinstalling GRUB 2)BUT:

```
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 grub-gfxpayload-lists : Depends: grub-pc (>= 1.99~20101210-1ubuntu2) but it is not going to be installed
 grub-pc-bin : Depends: grub-common (= 1.99-21ubuntu3) but it is not going to be installed
 grub2-common : Depends: grub-common (= 1.99-21ubuntu3) but it is not going to be installed
 libxml-libxml-perl : Depends: perlapi-5.10.0 but it is not installable
                      Depends: libxml-sax-perl but it is not going to be installed
 ubuntu-minimal : Depends: resolvconf
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```aaaa.... that libxml-libxml-perl problem!!!
Shall we move on?

```
root@ubuntu:/# dpkg --configure --pending
Setting up resolvconf (1.63ubuntu11) ...
mkdir: cannot create directory `/run': Too many levels of symbolic links
dpkg: error processing resolvconf (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on resolvconf; however:
  Package resolvconf is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 resolvconf
 ubuntu-minimal

```what about?

```
root@ubuntu:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  libxml-libxml-perl
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 1,376 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 310697 files and directories currently installed.)
Removing libxml-libxml-perl ...
/var/lib/dpkg/info/libxml-libxml-perl.prerm: 11: /var/lib/dpkg/info/libxml-libxml-perl.prerm: update-perl-sax-parsers: not found
dpkg: error processing libxml-libxml-perl (--remove):
 subprocess installed pre-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libxml-libxml-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)
```or even:

```
root@ubuntu:/# apt-get upgrade -f
root@ubuntu:/# apt-get dist-upgrade -f
```...the same!

The system is down permanently!

Any ideas???????:-(
ps: when I start now my ubuntu I receive this error message:[B]
"could not log bootup: Address already in use. An error occurred while mounting /run"[/B]

---

### Post by tgalati4 on 2013-02-12
I know I'm not the first to say: * Clean Install.*

tgalati4@Mint14-Extensa ~ $ apt-cache depends libxml-libxml-perl
libxml-libxml-perl
  Depends: libc6
  Depends: libxml2
  Depends: perl
  Depends: <perlapi-5.14.2>
    perl-base
  Depends: libxml-namespacesupport-perl
  Depends: libxml-sax-perl
  Breaks: <libxml-libxml-common-perl>
  Breaks: <libxml-libxml-common-perl:i386>
  Replaces: <libxml-libxml-common-perl>
  Replaces: <libxml-libxml-common-perl:i386>
  Conflicts: libxml-libxml-perl:i386

Ignoring the i386 references since I am running 64-bit.  Is it as simple as installing libxml-libxml-common-perl?

Perhaps there was a name change or a reroll of libxml packages, such that a missing dependency would cause a distribution upgrade failure?

In your chroot environment:

```
apt-cache policy libxml-libxml-common-perl
```

That doesn't help:

tgalati4@Mint14-Extensa ~ $ apt-cache policy libxml-libxml-common-perl
libxml-libxml-common-perl:
  Installed: (none)
  Candidate: (none)
  Version table:
tgalati4@Mint14-Extensa ~ $ apt-cache policy libxml-libxml-perl
libxml-libxml-perl:
  Installed: (none)
  Candidate: 2.0001+dfsg-1
  Version table:
     2.0001+dfsg-1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages

I don't even have it installed.  Perhaps only Ubiquity (installer) needs it?

---

### Post by kgeo on 2013-02-13
Hi again,

suppose I'm making a clean install how can I burn 771MB of Ubuntu 12.10 to a 700MB cd?
Some programs I tried just failed!
Also, I'm wondering if it's possible to import my home partition to the new installation and especially my Firefox bookmarks. **It's absolutely necessary to save especially them!!!**

Any help would be valuable at this point......

ps: I would like to hear for any proposal about another linux flavor even paid ones.

---

### Post by MAFoElffen on 2013-02-13
> **kgeo said:**
> Hi again,

suppose I'm making a clean install how can I burn 771MB of Ubuntu 12.10 to a 700MB cd?
Some programs I tried just failed!
Also, I'm wondering if it's possible to import my home partition to the new installation and especially my Firefox bookmarks. **It's absolutely necessary to save especially them!!!**

(Of course if you had been running google chrome, fresh install, log into chrome and it asks you if you want to import your online account stored bookmarks = transportable.)

Any help would be valuable at this point......

ps: I would like to hear for any proposal about another linux flavor even paid ones.

You can burn an oversized CD image onto a DVD... It will still boot. Been doing that testing the (oversized) Dev ISO's for over a year now. Of course that would mean your PC would require a DVD player to boot.

/home- Yes if you install vanilla, then add back your home partition in later. If you are adding that all back in... why not just the profile and config files?

Other Distros? Me?- Unix for over 35 years... Followed Linux from it's early years. Tried "most all" since. Liked Debain. Then Ubuntu. I still really like Ubuntu and it's derivatives. 

So if you wanted an honest, unbiased *opinion* that still seems on the surface as biased, that's my pick. It took years and lots of seeing other distro's I didn't like or didn't work for me to get there. I still test other distro's, but I'm happy here. Not many other Linux Distro branches that are as openly supported, adaptable and user friendly.

---

### Post by kgeo on 2013-02-14
Thanks to all,

I installed 12.04 and following this:
[http://askubuntu.com/questions/77993/how-to-install-with-separate-home-partition-home-partition-already-created-in-p?rq=1](http://askubuntu.com/questions/77993/how-to-install-with-separate-home-partition-home-partition-already-created-in-p?rq=1)
I managed to restore my home partition with my firefox bookmarks.

---

