---
title: "Lost ssh during aptitude updates, how to reattach?"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by jeffk on 2011-03-07
I lost my ssh connection to Ubuntu 10.10 server during the configuration update stage of an aptitude full-upgrade for a few month's worth of updates.

From the following ps ax list, can anyone tell me how I might reconnect to the screen which is prompting whether to keep the existing samba version, or use the distribution conf version?

Failing that, what's the safest sequence top kill these processes and start again? This time I'll remember to use screen to prevent connection loss.

Thanks,
Jeff

```
 9105 ?        Sl     0:01 aptitude full-upgrade
11375 tty1     Ss+    0:00 /sbin/getty -8 38400 tty1
14966 pts/2    Ss+    0:00 /usr/bin/dpkg --status-fd 35 --configure linux-headers-2.6.35-27 libc-dev-bin linux-libc-dev libc6-d
20519 ?        Ss     0:00 /usr/sbin/sshd -D
21098 pts/2    S+     0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/samba-common.postinst configure 2:3.
21118 pts/2    S+     0:00 /bin/sh /var/lib/dpkg/info/samba-common.postinst configure 2:3.5.4~dfsg-1ubuntu8
21134 pts/2    S+     0:00 /bin/bash /usr/bin/ucf --three-way --debconf-ok /var/run/samba/upgrades/smb.conf /etc/samba/smb.conf
21175 pts/2    S+     0:00 whiptail --backtitle Package configuration --title Samba Server --output-fd 11 --nocancel --default-
```

---

### Post by jeffk on 2011-03-08
Ran out of time to try reconnection ideas, killed the processes. Just posting to follow up for the archives: aptitude will pick up the config step where it left off, it worked fine.

---

### Post by Pytte on 2012-10-12
just for the record for future users who stumble on this from google as I did.

Here is the easiest way to get back to the dpkg configuration that failed.

```
ps -aux | grep dpkg
```

You should get a dpkg process somewhere with something like this:

```
root      4886  0.0  0.1  15760  5604 pts/2    Ss+  09:28   0:00 /usr/bin/dpkg --status-fd 61 --configure tzdata-java:all libc6-i386:amd64 libc-dev-bin:amd64 linux-libc-dev:amd64 libc6-dev:amd64 libapt-inst1.4:amd64 resolvconf:all libxml2:amd64 ntfs-3g:amd64 gnome-media:amd64 libgstreamer-plugins-bad0.10-0:amd64 gstreamer0.10-plugins-bad:amd64 libxslt1.1:amd64 nvidia-common:amd64 apt-utils:amd64 isc-dhcp-common:amd64 isc-dhcp-client:amd64 apt-transport-https:amd64 libisc83:amd64 libdns81:amd64 libisccc80:amd64 libisccfg82:amd64 libbind9-80:amd64
```

Might be very long or shorter..

```
sudo kill 4886 
```
the pid should be the dpkg pid which was 4886 in my case.

Now you can resume from where you left of by doing:
```
sudo dpkg --configure -a
```

This usually happens because dpkg has a question for you to answer so it stalls, otherwise the upgrade might have finished without you.

---

### Post by nothingspecial on 2012-10-12
Thanks for the added info but this thread is old.

Closed.

---

