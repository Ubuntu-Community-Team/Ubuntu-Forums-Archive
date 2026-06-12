---
title: "recover ssh do-release-upgrade session?"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by wally.nl on 2010-05-07
I was stupid enough to run do-release-upgrade over ssh *without screen* on my home-server/nas when my laptop went into standby. After resume I have a disconnected putty session that shows a selection screen for grub.

"ps auxf" output (see below) seems to indicate that this session is still active, is there _any_ way to recover/reconnect to this session or are there other ways to bring this upgrade to a happy end?

```

root     31424  0.0  0.0   5364  1056 ?        Ss   May07   0:00 /usr/sbin/sshd -o PidFile=/var/run/release-upgrader-sshd.pid -p 9004
root       321  0.0  1.3  49880 27320 ?        S    May07   0:03 /usr/bin/python /tmp/tmpcmZfNn/lucid --mode=server --frontend=DistUpgradeViewText
root     21207  0.0  0.3   8864  6544 pts/3    Ss+  May07   0:03  \_ /usr/bin/dpkg --force-overwrite --status-fd 25 --configure libc6-i686 ureadahead libc-dev-bin linux-libc-dev libc6-dev libck-connector0 libdbus-glib-1-2 libeggdbus-1-0
root     16429  0.0  0.4  11308  8352 pts/3    S+   00:05   0:00      \_ /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/grub-pc.postinst configure 1.97~beta4-1ubuntu4.1
root     16439  0.0  0.0   4340  1552 pts/3    S+   00:05   0:00          \_ /bin/bash -e /var/lib/dpkg/info/grub-pc.postinst configure 1.97~beta4-1ubuntu4.1
root     16460  0.0  0.0   4344  1556 pts/3    S+   00:05   0:00          |   \_ /bin/bash /usr/bin/ucf --three-way --debconf-ok --sum-file=/usr/share/grub/default/grub.md5sum /tmp/grub.0EjA0YsmTe /etc/default/grub
root     16503  0.0  0.0   4748  1488 pts/3    S+   00:05   0:00          \_ whiptail --backtitle Package configuration --title Configuring grub-pc --output-fd 11 --nocancel --default-item keep the local version currently installed --men

```additional info; 
- upgrade from 9.10 (alternate install) to 10.04
- install is on 2TB drives with md-raid5 (so using grub2/gpt)

Since my kid's movies are on this box I'm no longer waiting for response and I rebooted the box. So far everything looks rather well, the box booted to a login prompt and after a "sudo dpkg --configure -a" the installation of 10.04 seems to continue. Will update with final results.

OK, the upgrade finished rather good. Just rebooted after dpkg finished and most of the stuff still works. Had to reinstall squeezebox server, Tomcat6 no longer seems to start after reboot and there are still 3 packages that complain about not being able to upgrade (grub, libsensor3 and some keychain lib) but overall I'm happy it didn't take hours of work to get it working. Boot time is _way_ better than with 9.10 and boy do I hate the move of the windows close/resize buttons.

---

