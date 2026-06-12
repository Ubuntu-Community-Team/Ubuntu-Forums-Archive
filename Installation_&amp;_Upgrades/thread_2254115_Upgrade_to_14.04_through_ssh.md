---
title: "Upgrade to 14.04 through ssh?"
date: 2014-11-25
forum: Installation &amp; Upgrades
---

### Post by astarmathsandphysics on 2014-11-25
I have read this is not a good idea.
I have always connected though ssh.
How do I upgrade from 12.04 to 14.04?

---

### Post by slickymaster on 2014-11-25
Are you referring to a server install or a plain Ubuntu desktop install?

---

### Post by astarmathsandphysics on 2014-11-25
A server install.

---

### Post by slickymaster on 2014-11-25
Before starting the upgrade, make sure you have full backups of your data and everything important on another remote system or backup drive, because there is no way to guarantee that a release upgrade won't cause issues with software or configurations. If you are using Ubuntu on VPS make sure to take a server snapshot at your provider before upgrading.

See this link on a thorough tutorial of [Upgrading Ubuntu Server 12.04 LTS to Ubuntu Server 14.04 LTS]("http://landoflinux.com/linux_upgrade_ubuntu_server_1204_to_1404.html")

---

### Post by astarmathsandphysics on 2014-11-25
The prblem I have is ssh. I could upgrade but currently only connect via ssh.
I do have full backups of everything.

---

### Post by slickymaster on 2014-11-25
> **astarmathsandphysics said:**
> The prblem I have is ssh. I could upgrade but currently only connect via ssh.
I do have full backups of everything.

When you run **do-release-upgrade** the system starts a screen session automatically. If your ssh session gets disconnected, you can resume the installation, all you have to do is open a new ssh session, and run do-release-upgrade again. It will reconnect to your previous installation.

---

### Post by astarmathsandphysics on 2014-11-25
Thanks I will try that.

---

### Post by slickymaster on 2014-11-25
When you run **do-release-upgrade** over ssh, you get the following message:```
This session appears to be running under ssh. It is not recommended
to perform a upgrade over ssh currently because in case of failure it
is harder to recover.

If you continue, an additional ssh daemon will be started at port
'xxxx'.
Do you want to continue?
```

A risk you could eventually face is that your sshd server might need to be upgraded, and it could perhaps not restart correctly. Therefore the upgrade program runs a second daemon, at the port specified. You should check your network configuration to make sure you have access through this port, before resuming.

---

