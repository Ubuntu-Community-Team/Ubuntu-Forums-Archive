---
title: "Issues: preseeding Ubuntu Install from local mirror"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by skmah on 2007-10-05
I'm trying to setup a preseeded install from a boot CD. Booting ubuntu 7.04 install kernel, I'm able to grab the preseed file from our local http server.

I have 2 servers:
1) the DVD contents called "**localserver**"
2) the "**ubuntu-mirror **"which my coworker setup to sync with archive.ubuntu.com


The preseed file points to a local mirror.
d-i     mirror/http/hostname    string localserver.domain.com
d-i     mirror/http/directory   string /ubuntu
d-i     mirror/suite            string feisty

the localserver contains a DVD extracted folder for ubuntu 7.04.

It installs, but complains about the security updates. I'm trying to point everything locally, because if I use mirror/http/proxy, the install bombs out and says "failed to download linux-generic" or something like that. If I hit ok then the install will successfully complete.

[B][COLOR="Red"]Question #1: can you put some sort of proxy exception in the preseed file, so it can update through the internet. If not let's try to install everything from local servers.

Question #2: If we use all local servers, how can I get it to install security updates from the installer? Is it the apt-setup section that controls this?[/COLOR][/B]

d-i     apt-setup/uri_type      select http
d-i     apt-setup/hostname      string ubuntu-mirror.domain.com
d-i     apt-setup/directory     string /ubuntu
d-i     apt-setup/another       boolean false
d-i     apt-setup/security-updates      boolean true

The ubuntu-mirror works for apt updates.
I also try apt-setup/local0 but not sure which one to use or what syntax.

I'm out of ideas for now.

---

### Post by skmah on 2007-11-08
I found the solution from another posting: [293866]("http://ubuntuforums.org/showthread.php?t=293866&highlight=proxy+preseed")

setting the security_host to null in the preseed file or via boot parameter works. This way it will ignore the security checks. You can run updates after the fact.
preseed format:
d-i apt-setup/security_host string
boot parameter:
apt-setup/security_host string=

---

