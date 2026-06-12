---
title: "Cannot open a browser in fresh install of US 24.04.1"
date: 2024-10-02
forum: Installation &amp; Upgrades
---

### Post by Nosphky on 2024-10-02
I've just made a clean install of 24.04.1 and edited fstab because my /home is on a separate hard drive. This has restored the essential of my desktop appearance but when I try to open Firefox, I just get a message that my profile cannot be found. (It is in ~/.Mozilla ....). I would have thought FF would then start with a new profile but it does not. Without a browser, life becomes a bit hard.

I suspect that 24.04.1 comes with Firefox as a snap. How can I open it? I would eventually like FF directly downloaded from Mozilla rather than as a snap but first I have to get the browser working. Can someone provide some simple steps to help me out here? Thanks.

---

### Post by ActionParsnip on 2024-10-02
Did you chown the restored data to your user? Sounds like this is what's going on here

---

### Post by Nosphky on 2024-10-02
I've checked in my /home directory and sub-directories and my ownership is correct.

When I look at running processes, I find a firefox process but there is no visible display, no gui. What's happening?

---

### Post by ActionParsnip on 2024-10-02
> **Nosphky said:**
> I've checked in my /home directory and sub-directories and my ownership is correct.

What is the output
```

mount | grep -v -i tmp
echo
cat /etc/fstab

```

Thanks

---

### Post by Nosphky on 2024-10-02
> **ActionParsnip said:**
> What is the output
```

mount | grep -v -i tmp
echo
cat /etc/fstab

```

Thanks

This is the output:

mount | grep -v -i tmp

```
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
/dev/sdb2 on / type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
cgroup2 on /sys/fs/cgroup type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate,memory_recursiveprot)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
bpf on /sys/fs/bpf type bpf (rw,nosuid,nodev,noexec,relatime,mode=700)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=32,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=664)
debugfs on /sys/kernel/debug type debugfs (rw,nosuid,nodev,noexec,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,nosuid,nodev,relatime,pagesize=2M)
tracefs on /sys/kernel/tracing type tracefs (rw,nosuid,nodev,noexec,relatime)
mqueue on /dev/mqueue type mqueue (rw,nosuid,nodev,noexec,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,nosuid,nodev,noexec,relatime)
configfs on /sys/kernel/config type configfs (rw,nosuid,nodev,noexec,relatime)
/var/lib/snapd/snaps/core22_1564.snap on /snap/core22/1564 type squashfs (ro,nodev,relatime,errors=continue,threads=single,x-gdu.hide,x-gvfs-hide)
/var/lib/snapd/snaps/bare_5.snap on /snap/bare/5 type squashfs (ro,nodev,relatime,errors=continue,threads=single,x-gdu.hide,x-gvfs-hide)
/var/lib/snapd/snaps/firmware-updater_127.snap on /snap/firmware-updater/127 type squashfs (ro,nodev,relatime,errors=continue,threads=single,x-gdu.hide,x-gvfs-hide)
/var/lib/snapd/snaps/core22_1621.snap on /snap/core22/1621 type squashfs (ro,nodev,relatime,errors=continue,threads=single,x-gdu.hide,x-gvfs-hide)
/var/lib/snapd/snaps/firefox_4793.snap on /snap/firefox/4793 type squashfs (ro,nodev,relatime,errors=continue,threads=single,x-gdu.hide,x-gvfs-hide)
/var/lib/snapd/snaps/freeshow_52.snap on /snap/freeshow/52 type squashfs (ro,nodev,relatime,errors=continue,threads=single,x-gdu.hide,x-gvfs-hide)
/var/lib/snapd/snaps/freeshow_56.snap on /snap/freeshow/56 type squashfs (ro,nodev,relatime,errors=continue,threads=single,x-gdu.hide,x-gvfs-hide)
/var/lib/snapd/snaps/gnome-42-2204_176.snap on /snap/gnome-42-2204/176 type squashfs (ro,nodev,relatime,errors=continue,threads=single,x-gdu.hide,x-gvfs-hide)
/var/lib/snapd/snaps/gtk-common-themes_1535.snap on /snap/gtk-common-themes/1535 type squashfs (ro,nodev,relatime,errors=continue,threads=single,x-gdu.hide,x-gvfs-hide)
/var/lib/snapd/snaps/snapd_21759.snap on /snap/snapd/21759 type squashfs (ro,nodev,relatime,errors=continue,threads=single,x-gdu.hide,x-gvfs-hide)
/var/lib/snapd/snaps/snapd-desktop-integration_178.snap on /snap/snapd-desktop-integration/178 type squashfs (ro,nodev,relatime,errors=continue,threads=single,x-gdu.hide,x-gvfs-hide)
/var/lib/snapd/snaps/thunderbird_507.snap on /snap/thunderbird/507 type squashfs (ro,nodev,relatime,errors=continue,threads=single,x-gdu.hide,x-gvfs-hide)
/var/lib/snapd/snaps/thunderbird_517.snap on /snap/thunderbird/517 type squashfs (ro,nodev,relatime,errors=continue,threads=single,x-gdu.hide,x-gvfs-hide)
/dev/sda1 on /home type ext4 (rw,relatime)
/dev/sdb1 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)
portal on /run/user/1000/doc type fuse.portal (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
nsfs on /run/snapd/ns/snapd-desktop-integration.mnt type nsfs (rw)
nsfs on /run/snapd/ns/firefox.mnt type nsfs (rw)
nsfs on /run/snapd/ns/thunderbird.mnt type nsfs (rw)
nsfs on /run/snapd/ns/firmware-updater.mnt type nsfs (rw)

```

fstab


```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during curtin installation
/dev/disk/by-uuid/ ext4 defaults 0 1
  /home ext4 defaults 0 2
# /boot/efi was on /dev/sdb1 during curtin installation
/dev/disk/by-uuid/boot/efi vfat defaults 0 1
/swap.img    none    swap    sw    0    0
```

---

### Post by oldfred on 2024-10-02
If you want the .deb version & uninstall the snap, both Firefox & Thunderbird.
You also have to reset priorities as shown or it will reinstall the Firefox or Thunderbird snap.
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)
[https://www.omgubuntu.co.uk/2024/08/install-thunderbird-deb-not-snap-in-ubuntu-24-04](https://www.omgubuntu.co.uk/2024/08/install-thunderbird-deb-not-snap-in-ubuntu-24-04)
Similar instructions:
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)

---

### Post by Nosphky on 2024-10-02
Hi oldfred - I think it was advice from you that led me to keep  /home on a separate disk -- way back in 20.04 or even before and it's always worked well. 

I'll read up those articles - I was looking for the Muon package manager but that seems to have been dropped in 24.04. So it'll be back to the Konsole.  But it would be good for now if the snap package lit up properly. Without a browser, I'm having to fall back on another box for this stuff and my main box might as well be dead.

---

### Post by oldfred on 2024-10-02
I do not use /home as separate partition, but suggest it to newer users as it automatically creates mount point and correct ownership and permissions to use that partition.
I like to have multiple installs, stopped upgrading 10 years ago as a new install then went so well.
I have 22.04 & 24.04 each with own /home but no data on SSD. And larger data partition used by all installs.
I then often have experimental installs on HDD that also uses same data partition. Often another LTS to experiment with settings or programs or newer version. 

I used to be able to share both Firefox & Thunderbird profiles in shared data partition. Back with XP it even worked for XP & Ubuntu even if versions were not quite the same. Then versions had to be same. Now it gives me errors on version, so I have to copy Firefox profile into each install's /hhome, but am able to share Thunderbird from data partition.

---

### Post by ubfan1 on 2024-10-02
Snap moved the firefox profile to the snap directory in your home:
snap/firefox/common/.mozilla/firefox/r1fzj7uw.default

Can't speak to any format changes, but the contents of my default directory looks pretty much like it's always been.

---

### Post by Nosphky on 2024-10-02
oldfred:  I followed the steps outlined in the articles you linked just for Firefox. Thunderbird is working ok and I've checked and it is a snap but it's working fine so I'll leave it alone.

I now have firefox installed in 131.0~build1  in /usr/bin/firefox   but when I click the launch icon to open it, I get an error dialog "Your Firefox profile cannot be loaded. It may be missing or inaccessible."  And that's the end - Firefox gives up and doesn't open so I still have no browser.

This is exactly the same as when it was the original snap installation of my clean install of US 24.04.1.  at the beginning of this thread.

The Firefox profile is where it's been for the last 6 or 8 years: /home/xxx/.mozilla/firefox/.  Why doesn't it assume I'm a new user and create a new profile? 

Now I have to find out how to tell it where the profile is.

---

### Post by oldfred on 2024-10-02
Look at /home/$USER/.mozilla/firefox/profiles.ini

Your profile 0 should match the folder with your firefox files.

---

### Post by Nosphky on 2024-10-02
> **oldfred said:**
> Look at /home/$USER/.mozilla/firefox/profiles.ini

Your profile 0 should match the folder with your firefox files.

That's it - thanks.

When I looked into /profiles.ini and saw what was listed as profile 0, I found that that profile was no longer present in the directory /.mozilla/firefox/.  Since it had been there and working fine before my install of the new version of Ubuntu, I suspect Snap pinched it when I installed US24.04.1, and it then got deleted with all the snap stuff associated with the firefox snap in my earlier edits today.

Once I copy/pasted a backup of the default 0 profile into /.mozilla/firefox/, firefox started up as normal.

Thanks, guys.  I'll mark this one as solved.

---

