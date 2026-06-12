---
title: "Empty resolv.conf in Ubuntu Server"
date: 2024-05-05
forum: Installation &amp; Upgrades
---

### Post by mloftus11 on 2024-05-05
Hello Everyone
I am new to Ubuntu and Linux in general. I am using Ubuntu Server to run a small home pc for ad blocking on my LAN. I am running Docker Portainer and AdguardHome.
I changed my  resolv.conf because it did not have DNS servers for adguard to work properly. Once I did this it was working great. That is until I started up the System this AM and Adgard was not working. So I checked the resolv.conf and it was epmty. I looked in the /etc/ directory and I have these files:

resolv.conf
resolv.conf.save
resolv.conf.save1
resolv.conf.save2
resolv.conf.save3
.resolv.conf.systemd-resolved.bak

Is this normal and What can I do to resolve this? Will I need to edit resolv.conf every time I start the System? Any ideas? TIA
Mike

---

### Post by TheFu on 2024-05-05
There's a warning that resolv.conf is managed outside it.  That all changes will be overwritten.  You didn't say which version of Ubuntu Server you are running, so I have to guess it is recent.  To prevent resolv.conf from being modified, you need to disable systemd-resolved.  Wouldn't hurt to stop it first, disable it, then purge it from the system.  Also, you want to understand symbolic links, since /etc/resolv.conf is usually a symbolic link to the real file elsewhere on the box.  That isn't necessary if you are overriding the DNS completely.  A normal file will work fine.  I don't think anything is too picky about ownership, group or permissions, but these are what definitely work:

```
-rw-r--r-- 1 root root 74 Feb 28  2023 /etc/resolv.conf
```

Or if you want to keep the local DNS caching server, systemd-resolved, running, you can modify the config file for that tool.  Just look for resolved.conf on the system.
```

$ locate resolved.conf
/etc/systemd/resolved.conf
/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf
/usr/share/man/man5/resolved.conf.5.gz
/usr/share/man/man5/resolved.conf.d.5.gz

```
That's on my 22.04-based system. Yours could be different.  It is self-documented and there is a manpage for it if you need more details.

If you are going to run a server, learning some basics would be useful.  [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) has them.  Start from chapter 1 and go through to first 250-ish pages (finish that chapter).  Then you'll be safe enough to google answers.

---

### Post by yancek on 2024-05-05
That file is overwritten on reboot.  You could try the suggestion at the link below.

[https://askubuntu.com/questions/1441045/ubuntu-20-04-lts-etc-resolv-conf-is-getting-overwritten-after-either-netplan-ap](https://askubuntu.com/questions/1441045/ubuntu-20-04-lts-etc-resolv-conf-is-getting-overwritten-after-either-netplan-ap)

---

