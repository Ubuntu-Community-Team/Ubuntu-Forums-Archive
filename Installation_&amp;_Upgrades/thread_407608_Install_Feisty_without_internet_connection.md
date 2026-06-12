---
title: "Install Feisty without internet connection?"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by mweichert on 2007-04-12
Hello,

I've been going crazy with this the last couple of days:

I'm trying to install Feisty WITHOUT a network connection. More specifically, I'm trying to preseed the installation. Everything seems to be going great until I hit the error "Bad archive mirror". 

Looking at syslog, I see that the installer is trying to wget the release file from archive.ubuntu.com. Why would it do that? How do I tell d-i to use the cdrom?

I haven't specified values for any mirror-related questions and I am only installing ubuntu-standard and ubuntu-desktop. 

Please, if any one could help me I would very much appreciate it!

Thanks,
Mike

---

### Post by morloch on 2007-07-10
Hi,

I have been investigating the same problem recently and found that the following settings in the preseed file will prevent apt from using the network both during and after the install.

d-i  apt-setup/uri_type         select cdrom
d-i  apt-setup/use_mirror     boolean false
d-i  apt-setup/another          boolean false
d-i apt-setup/security_host string

Regards, David.

---

### Post by Odrodzona-Sarmacja on 2007-07-11
I found also installation of ubuntu with an active network connection somehow... buggy.

My solution was to disconnect cable to internet and start everything all over from the very begining. The Installation went without problems and quite fast too.

---

