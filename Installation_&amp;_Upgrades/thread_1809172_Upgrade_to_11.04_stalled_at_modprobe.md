---
title: "Upgrade to 11.04 stalled at modprobe"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by fsck on 2011-07-21
Hi,

I'm trying to upgrade to 11.04 and it seems to stall while running modprobe. I would be very grateful if somebody could suggest something I might try. The last output I get from the installer is:

```

Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic

```

Then it stalls :-/ Here is some output from 'ps aux':

```

me       14620  0.0  0.5  29104  5268 ?        Sl   10:51   0:03 gksu --desktop /usr/share/applications/update-manager.desktop -- /tmp/update-manager-SLQ8hT/n
me       14704  0.0  0.2   8980  2300 ?        S    10:52   0:00 /usr/lib/gvfs/gvfsd-computer --spawner :1.11 /org/gtk/gvfs/exec_spaw/2
root     14782  1.0  3.6 190188 35752 ?        Ssl  10:52   1:45 /usr/bin/python /tmp/update-manager-SLQ8hT/natty
root     14984  0.0  0.6  13936  6072 ?        S    10:53   0:00 /usr/bin/python /usr/lib/system-service/system-service-d
root     16368  0.1  0.6  10340  5920 pts/1    Ss+  12:55   0:04 /usr/bin/dpkg --force-overwrite --status-fd 36 --configure libc-dev-bin linux-libc-dev libc6-
root     16426  0.0  0.0   2268   848 ?        Ss   12:55   0:00 cron
root     18296  0.0  0.3  27412  3452 ?        Sl   12:58   0:00 /usr/lib/policykit-1/polkitd
root     19110  0.0  0.0   2052   624 ?        S    11:27   0:00 gnome-pty-helper
root     19111  0.0  2.6 186220 25604 pts/0    Ssl+ 11:27   0:01 /usr/bin/python /tmp/update-manager-SLQ8hT/natty
root     19126  0.0  0.0   3456   532 pts/0    S+   11:27   0:00 dbus-launch --autolaunch=b88c911358000d44f13541664c026582 --binary-syntax --close-stderr
root     19128  0.0  0.2   3856  2104 ?        Ss   11:27   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
root     25032  0.0  0.0   1864   668 ?        Ss   13:16   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root     25669  0.0  0.1  16320  1324 ?        Ss   13:03   0:00 /usr/sbin/winbindd
root     25673  0.0  0.0  16320   944 ?        S    13:03   0:00 /usr/sbin/winbindd
root     25954  0.0  0.1   2880  1024 ?        S<s  13:17   0:00 udevd --daemon
root     27594  0.0  0.3  19772  3324 ?        Sl   13:18   0:00 /usr/lib/upower/upowerd
root     27694  0.0  0.3  27444  3304 ?        Sl   13:18   0:00 /usr/lib/udisks/udisks-daemon
root     27695  0.0  0.0   5564   712 ?        S    13:18   0:00 udisks-daemon: polling /dev/sr0
root     27728  0.0  0.1   2876  1044 ?        S<   13:18   0:00 udevd --daemon
root     27729  0.0  0.1   2876  1044 ?        S<   13:18   0:00 udevd --daemon
root     28496  0.0  0.2   7488  2448 pts/1    S+   13:18   0:00 /usr/bin/perl /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst configure 
root     28521  0.0  0.0   1912   508 pts/1    S+   13:18   0:00 sh -c /usr/sbin/update-initramfs -c -k 2.6.38-10-generic >&2
root     28522  0.0  0.0   1912   508 pts/1    S+   13:18   0:00 /bin/sh /usr/sbin/update-initramfs -c -k 2.6.38-10-generic
root     28524  0.0  0.0   1912   676 pts/1    S+   13:18   0:00 /bin/sh /usr/sbin/mkinitramfs -o /boot/initrd.img-2.6.38-10-generic.new 2.6.38-10-generic
root     31468  0.0  0.0   1912   172 pts/1    S+   13:18   0:00 /bin/sh /usr/sbin/mkinitramfs -o /boot/initrd.img-2.6.38-10-generic.new 2.6.38-10-generic
root     31469  0.0  0.0   1864   556 pts/1    S+   13:18   0:00 modprobe --set-version=2.6.38-10-generic --ignore-install --quiet --show-depends ses
root     31470  0.0  0.0   5668   908 pts/1    S+   13:18   0:00 awk /^insmod/ { print $2 }

```

Should I kill some of these processes? Is this safe or even sane? Does anybody have any suggestions about how can I get the upgrade process to continue?

I have had some ongoing problems with cups, and have had to manually  kill "start cups" and "stop cups" processes, but I think that this is a  separate issue.

Thanks in advance!

---

### Post by fsck on 2011-07-21
I think I have found the solution. I killed the update-initramfs, mkinitramfs and modprobe processes. I then tried sudo dpkg --configure -a, but this led to the same error messages and stalled. I tried several workarounds on [this thread]("http://ubuntuforums.org/archive/index.php/t-1611122.html") (none of which succeeded) and then finally got a successful workaround from [this thread.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421/comments/31")

I'll now see if it restarts . . . !
[]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421/comments/31")

---

