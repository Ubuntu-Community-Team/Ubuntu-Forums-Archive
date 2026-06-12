---
title: "How I keep in Ubuntu only 2 kernels? By auto settings?"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by Sylslay on 2011-01-09
Hi, everone.

I just tidy up my kernels in Ubuntu 10.04. Kept only two becouse 10.04 is steady.

I just run fiew apt-get clean, autoremove, purge etc.

Now:
[B][COLOR="Blue"]Is any way to for confgure 
apt or Synaptic for keepnig only two version of kernels?
[/COLOR][/B]
I mean
latest and one older.

Thanks.

Ps Yum in Fedora by deflaut keep only 3 version of kernels in
 
yum.conf

###
installonly_limit=3

Thanks[SIZE="5"][/SIZE]

Found some settings for APT and kernels

 /etc/apt/apt.conf.d/01autoremove:
 NeverAutoRemove
  {
        "^firmware-linux.*";
        "^linux-firmware$";
        "^linux-image.*";

Thanks to [http://www.mail-archive.com/discuss@blu.org/msg00154.html](http://www.mail-archive.com/discuss@blu.org/msg00154.html)

but,
Shell I chanege "NeverAutoremove" --> "Autoremove" 
or hash whole 5 line but than I will left only with one kernel in OS, No good?

---

### Post by oldfred on 2011-01-10
Kernels do not take a lot of room. So you can just display  2 on boot and houseclean once in a while.

Grub 2 Title Tweaks Thread -drs305 See #2
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by Sylslay on 2011-01-12
Yep, for now is best way, just set:

Display 2 kernel in grub2 and do bit housekeepning! From time to time.


THX. It helps.

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

"LIMITING MAIN KERNEL ENTRIES "

---

