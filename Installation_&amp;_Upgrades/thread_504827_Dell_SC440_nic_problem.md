---
title: "Dell SC440 nic problem"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by charbo on 2007-07-19
Hi all,

I sort of followed Francis's steps, [http://ubuntuforums.org/showthread.php?p=1920008#post1920008]("http://ubuntuforums.org/showthread.php?p=1920008#post1920008") and it sort of worked.
But, stupid me, I stopped before the rebooting at the end.

I was happily updating the system and all, and now for testing purposes, I needed to reboot the machine, and now, the system does not even recognize the network card.

When I restart the network, it says "no such device", dmesg has no eth* entry, and /etc/iftab is empty.

I modprobe tg3, modprobe eth0, insmod tg3.ko, whatever, and they all run and installs the module, but still the system does not recognize the network card.

It does not allow me to re-install the buildessential and linux-header-$(uname -r) from the CD-rom either (I uninstalled them, after the make install, because I believe I should not have compilers on servers, if they are not truly necessary.).  I guess it is because I updated the system from the internet.

Does anybody have any idea what is going on, and how to fix it?

Thanks a lot for whatever help you can offer, in advance,

Sadanori

---

### Post by charbo on 2007-07-20
Hello again,

Since nobody responded to my post, I decided to recreate the problem. Then, in short, I found out that the problem was actually upgrading the system.

I re-installed the system, and that went well. 
I followed the steps laid out by Francis, and it went very well.  I even rebooted the system, and it was still working.
I ran apt-get update, then apt-get upgrade, and they both ran without a problem.
Then I lost network connection.  ifconfig does not show eth0 anymore.
The following is the first part of the output from the apt-get upgrade command.


The following packages have been kept back:
  linux-image-server
The following packages will be upgraded:
  bind9-host cpio dnsutils dpkg dselect file gnupg gzip info iptables klogd
  libbind9-0 libc6 libc6-i686 libdns21 libgnutls12 libisc11 libisccc0
  libisccfg1 libkrb53 liblwres9 libmagic1 libssl0.9.8
  linux-image-2.6.15-26-server linux-server locales lvm2 openssh-client
  python2.4 python2.4-minimal sysklogd tar tcpdump w3m
34 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


I am thinking that linux-image-2.6.15-26-server, or  linux-server maybe the culprit.

Now, I am back to the stuck situation.
Can anybody help?
Thank you in advance,

Sadanori

---

