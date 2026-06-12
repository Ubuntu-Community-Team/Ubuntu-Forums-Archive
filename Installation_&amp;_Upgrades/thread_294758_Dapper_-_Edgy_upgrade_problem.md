---
title: "Dapper - Edgy upgrade problem"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by sitara on 2006-11-07
I am trying to upgrade to Edgy. All the files have been downloaded successfully but the installation told me to delete the contents of `/usr/X11R6/bin' and then abort. I deleted the Opera file (the only  one) from the directory and restarted the dist-upgrade as instructed and get this:

The following packages have unmet dependencies:
  libpango1.0-dev: Depends: libxft-dev but it is not installed
  xutils-dev: Depends: x11-common (>= 1:7.0.0) but 7.0.0-0ubuntu45 is installed

When Itry to run apt-get -f install I get this:

E: /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb: trying to overwrite `/usr/X11R6/bin', which is also in package opera

I have been trying to repair/remove/update the offending packages but I'm not getting anywhere.

Can someone please help me out of this mess?

Thanks

Keith

---

### Post by elpresidente on 2006-11-08
dpkg --purge opera

---

### Post by sitara on 2006-11-08
I fixed the problem by going back to my old Dapper sources list and upgrading the 'official' way using gksudo update-manager. Everything is now fine. Unfortunately I didn't come across the official method until I had tried an unofficial method!

---

### Post by shimada on 2006-11-08
Hello.

I have the same problem you have.  Would you please explain how you went back to your old Dapper sources list?

Thanks.

---

### Post by sitara on 2006-11-09
I found a list on this forum by searching for Dapper sources. I copied that and placed it ino /etc/apt/sources.list. You could also check if a backup was created (in /etc/apt) when you edited your sources file and just restore that backup. Good luck, Keith.

---

### Post by shimada on 2006-11-13
Sitara/Keith
Thank you for your help.  My machine is up and running.

Cheers,
Michael

---

