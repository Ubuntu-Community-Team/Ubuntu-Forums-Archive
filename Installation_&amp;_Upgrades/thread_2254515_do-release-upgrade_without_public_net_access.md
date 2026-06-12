---
title: "do-release-upgrade without public net access"
date: 2014-11-27
forum: Installation &amp; Upgrades
---

### Post by dbruce2 on 2014-11-27
We have some systems on private IP space that can only be reached by those in our other IP space. These servers cannot reach out beyond our IP space.

We keep a local repository for patches so that is not an issue, but **do-release-upgrade** fails to find anything as that appears to reach out to Ubuntu's servers.

Is there any way to point do-release-upgrade at somewhere we host here? Perhaps even the server where we host our repo?

Thank you.

---

### Post by grahammechanical on 2014-11-27
What do you expect the command do-release-upgrade to do? It is used to upgrade an existing Ubuntu installation to the next Ubuntu release. And to do that it accesses the Ubuntu repositories/servers that hold all the packages of the new release and also the scripts that carry out the downloading and installation of the new packages.

Do, you have all those packages on a private repository? You could try downloading an ISO image of the new Ubuntu release, burn it to a DVD and set that up as a local respository. I have no idea if this will work. None at all.

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

Ubuntu keeps the URLs of its repositories at /etc/apt/source.list.  How that information would help you I cannot say.

Regards.

---

