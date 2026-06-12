---
title: "Server upgrade Dapper to Edgy"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by MerZo on 2006-10-26
Hello!

I just read the FAQs about upgrading my dapper to an edgy install. The problem with the first link [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades) is that is says that is is neccassry to install the ubuntu-desktop the kubuntu-desktop to install the upgrade using apt-upgrade, which I think would be unessessary on a server.

The second link [https://wiki.ubuntu.com/EdgyReleaseNotes](https://wiki.ubuntu.com/EdgyReleaseNotes) says that you need to run the command apt-get dist-upgrade on a server, but saying something about upstart not being installad. So just to the question.

What is the commands to use to upgrade an dapper server install to an edgy server install, on a server without X. Just now acting as a LAMP server. Can anyone help? I am a bit confused.

Thanks in advance](*,)

---

### Post by Jussi Kukkonen on 2006-10-26
> I just read the FAQs about upgrading my dapper to an edgy install. The problem with the first link [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades) is that is says that is is neccassry to install the ubuntu-desktop the kubuntu-desktop to install the upgrade using apt-upgrade, which I think would be unessessary on a server.
Read a little bit further ;) : *Server distribution may skip this step.*

The point of installing the desktop package is to ensure entirely new software gets installed too, not just new versions of old software. This is not needed on a server -- you can always install what you need afterwards.

The apt-get section of the EdgyUpgrade page gives good and thorough instructions.

By the way, Dapper will be supported for a long time, so there is no hurry. I'm probably not going to install Edgy on my server at all, and definitely not right when it's released.

---

