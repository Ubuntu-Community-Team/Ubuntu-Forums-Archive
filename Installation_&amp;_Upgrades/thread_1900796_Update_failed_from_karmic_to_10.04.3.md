---
title: "Update failed from karmic to 10.04.3"
date: 2011-12-27
forum: Installation &amp; Upgrades
---

### Post by nisam360 on 2011-12-27
Dear team,

I am updating Ubuntu 9.10 (karmic) to 10.04.3 using update manager. all the files has been feched and when it is going to next step, it is showing the following error.

Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-36.79_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-36.79_i386.deb) 404  Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/a/app-install-data-partner/app-install-data-commercial_12.10.04.4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/a/app-install-data-partner/app-install-data-commercial_12.10.04.4_all.deb) 404  Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.32.36.42_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.32.36.42_i386.deb) 404  Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.36.42_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.36.42_i386.deb) 404  Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.32.36.42_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.32.36.42_i386.deb) 404  Not Found


I am having working internet connection and tried updation again and seems same error. When i am manually checking the failed url , i am getting http error. Please help me to upgrade my ubuntu. I am using main server for update.

Following are the output of cat /etc/apt/sources.list 
_cat /etc/apt/sources.list_
eb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security multiverse
# deb [http://www/kismetwireless.net/code](http://www/kismetwireless.net/code) natty kismet # disabled on upgrade to karmic

# deb [http://www.kismetwireless.net/code/](http://www.kismetwireless.net/code/) maverick kismet # disabled on upgrade to karmic
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) lucid main restricted universe multiverse
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) lucid-updates main restricted universe multiverse
deb [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse

# deb [http://www.kismetwireless.net/code/](http://www.kismetwireless.net/code/) maverick kismet # disabled on upgrade to karmic
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://www.kismetwireless.net/code/](http://www.kismetwireless.net/code/) maverick kismet




Regards,
Naisam

---

### Post by mörgæs on 2011-12-27
Hi, welcome to the fora.

If you want to try the upgrade path (which I would not recommend), at least you have to comment out the two last lines. There should only be pointers to one release in sources.list.

However, it seems like you have made a lot of experimenting back and forth on this computer, and it you want to reach 11.10 three more upgrades are waiting. Have you thought of a fresh install?

---

### Post by nisam360 on 2011-12-27
Dear sir,

I comment out last line which is following but still it is not resolved
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic universe
# deb [http://www.kismetwireless.net/code/](http://www.kismetwireless.net/code/) maverick kismet

I don't want fresh install because lot of dependency is there. 
Please help me to upgrade higher version.

Thanks in advance.

Regards,
naisam

---

### Post by mörgæs on 2011-12-27
There are no dependency problems with a fresh install, only with upgrades.

I can't help you, sorry. I have tried upgrading a few times in the past but never with good results.

---

### Post by darkod on 2011-12-27
Can it be that the server is down from what ever reason? Even though the list is long, you are actually trying only one server by default.

In 9.10 go into Software Sources and change the server. Then try again if that helped.

---

