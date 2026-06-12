---
title: "Install updates, completely silent except for any errors"
date: 2021-01-06
forum: Installation &amp; Upgrades
---

### Post by newbuntu2020 on 2021-01-06
Is there a command that will install all updates with no output at all except for errors? The use case is systems which automatically update themselves by running a suitable command as a cronjob and those who maintain the systems them only get an email about it if something goes wrong.

I thought 
```
apt-get -qq -y dist-upgrade && reboot
```
would do it, but even though that appears to be maximum quiet it still emits a lot of information. I've been doing this for years on CentOS with
```
yum -y -e 0 -d 0 update && reboot
```
but can't work out a Ubuntu version of that.

---

### Post by TheFu on 2021-01-06
I don't do automatic updates on production systems, been burned, but it appears to be missing the required **apt-get update** command. Ubuntu is different from centos in that way.

To be quiet, I'd just redirect the output for stdout and stderr to different files. Then if anything is in the stderr file, email that.

---

### Post by ActionParsnip on 2021-01-06
As stated by TheFu you need
```

sudo apt update

```
to reread the reporistory information before new packages will be detected.

---

### Post by CatKiller on 2021-01-06
You don't need to reinvent the wheel unless you particularly want to; [unattended upgrades](https://wiki.debian.org/UnattendedUpgrades) is already a thing.

---

### Post by newbuntu2020 on 2021-01-07
> **CatKiller said:**
> You don't need to reinvent the wheel unless you particularly want to; [unattended upgrades]("https://wiki.debian.org/UnattendedUpgrades") is already a thing.

As far as I can tell the unattended upgrades thing does not provide a way to reboot the system after the installation of updates and as such it's no use to me.

---

### Post by CelticWarrior on 2021-01-07
Reboot typically is of no use for most updates anyway - this isn't Windows - but if you want to do the way you're used to then just correct the commands as indicated above.

---

### Post by TheFu on 2021-01-07
> **newbuntu2020 said:**
> As far as I can tell the unattended upgrades thing does not provide a way to reboot the system after the installation of updates and as such it's no use to me.

No need to reboot, unless /var/run/reboot-required exists, which is only about once a month.
Rebooting automatically is asking for trouble.  Good luck with that.

---

### Post by newbuntu2020 on 2021-01-07
> **CelticWarrior said:**
> Reboot typically is of no use for most updates anyway - this isn't Windows 
I am well aware that Linux is not Windows.

---

