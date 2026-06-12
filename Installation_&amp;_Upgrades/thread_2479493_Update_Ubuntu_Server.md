---
title: "Update Ubuntu Server"
date: 2022-09-26
forum: Installation &amp; Upgrades
---

### Post by craigs2188 on 2022-09-26
I am attempting to install security updates for installed packages on   Ubuntu 22.04 LTS, however when running sudo apt-get update / upgrade   and dist-upgrade everything comes back clear like it is installed. However, we run tenable/nessus and we have 40 updates to install which  are newer versions. As an example: [https://www.tenable.com/plugins/nessus/164946](https://www.tenable.com/plugins/nessus/164946) & [https://www.tenable.com/plugins/nessus/152783](https://www.tenable.com/plugins/nessus/152783) How do I get this updated file and then install it?

---

### Post by grahammechanical on 2022-09-26
Your thread title is misleading. You do not have a problem updating Ubuntu Server. You have a problem updating a Tenable program called Nessus. Ubuntu is updated and upgraded from software repositories curated by Canonical the publisher of Ubuntu. Nessus is not in any Ubuntu repository. That is why apt-get update/upgrade is not updating Nessus.

Please read the Tenable/Nessus documentation.

[https://docs.tenable.com/nessus/commandlinereference/Content/RunTheDefaultUpdate.htm](https://docs.tenable.com/nessus/commandlinereference/Content/RunTheDefaultUpdate.htm)

Regards

---

### Post by TheFu on 2022-09-26
Canonical backports security updates for packages in their supported package list. This doesn't include all packages, but on a server using the core Ubuntu Repos, not the metaverse/multiverse repos, it should be all of them.  Because the security issues are backported and any change to functionality is avoided, the package versions are updated in the 3rd and higher version number, not in the 1st or 2nd numbers.  Perhaps you understand this, but either forgot or assumed Canonical would just go to a newer version of software. 

LTS releases for Ubuntu are version fixed, for nearly all software with a few exceptions like browsers, fat email clients and some internet webapp clients which would become useless when the remote server changes.  LTS releases do on get new versions of code that is released by the project. After all, most projects don't backport fixes to 2 yr old software.  That's what distros do.

Or did I misunderstand the issue?

---

### Post by craigs2188 on 2022-09-27
> **grahammechanical said:**
> Your thread title is misleading. You do not have a problem updating Ubuntu Server. You have a problem updating a Tenable program called Nessus. Ubuntu is updated and upgraded from software repositories curated by Canonical the publisher of Ubuntu. Nessus is not in any Ubuntu repository. That is why apt-get update/upgrade is not updating Nessus.

Please read the Tenable/Nessus documentation.

[https://docs.tenable.com/nessus/commandlinereference/Content/RunTheDefaultUpdate.htm](https://docs.tenable.com/nessus/commandlinereference/Content/RunTheDefaultUpdate.htm)

Regards

Hi,

So it is not Tenable I am trying to update it, that's the tool being used for Cyber Essentials + has run a scan and found all 40 missing security updates. The problem is that when running apt-get update/upgrade, etc., there are no updates. When I google for instance OpenSSL to see the latest available versions, there is a newer version available to install online that I am unable to install via apt-get update on the server

---

### Post by mikewhatever on 2022-09-27
> **craigs2188 said:**
> Hi,

So it is not Tenable I am trying to update it, that's the tool being used for Cyber Essentials + has run a scan and found all 40 missing security updates. The problem is that when running apt-get update/upgrade, etc., there are no updates. When I google for instance OpenSSL to see the latest available versions, there is a newer version available to install online that I am unable to install via apt-get update on the server

The links you've posted and the CVE numbers all lead to tenable.com. For example, look at "File Name: debian_DLA-3103.nasl", which is listed under [https://www.tenable.com/plugins/nessus/164946](https://www.tenable.com/plugins/nessus/164946). There is no such package in Ubuntu, as said above it is a tenable plugin.
It is the same with "File Name: debian_DSA-4963.nasl". Ubuntu doesn't have such a package, it is provided by tenable.

---

### Post by TheFu on 2022-09-27
> **craigs2188 said:**
> Hi,

So it is not Tenable I am trying to update it, that's the tool being used for Cyber Essentials + has run a scan and found all 40 missing security updates. The problem is that when running apt-get update/upgrade, etc., there are no updates. When I google for instance OpenSSL to see the latest available versions, there is a newer version available to install online that I am unable to install via apt-get update on the server

Get the CVE numbers and look for how those are addressed by the Ubuntu Security team.  For example, [https://ubuntu.com/security/CVE-2021-3712](https://ubuntu.com/security/CVE-2021-3712). Often, the updates are available in 1-2 days, but more complex issues can take longer.  
 	for Focal, the openssl fix was Released (1.1.1f-1ubuntu2.8).  You can follow the other package fixes for you specific, supported, ubuntu releases if you like. My 20.04 systems have:
```
||/ Name              Version            Architecture Description
+++-=================-==================-============-====================================================
ii  openssl           1.1.1f-1ubuntu2.16 amd64        Secure Sockets Layer toolkit - cryptographic utility

```
If yours don't, that's an issue on your side.  For 22.04, the version of openssl arrived with a newer version, 3.0.2-0ubuntu1.6. No impact.  Any CVE from August 2021 would have been fixed/patched before 22.04 was released.  But feel free to manually check everything. I know I did back when I was getting used to Ubuntu Servers.

I patch weekly, during an approved maintenance period, unless the CVE is high-impact for our systems. In the last 15 yrs, that happened only twice.  Then I did am emergency patch mid-week on the impacted systems only.  The others waited until the normal weekend patch cycle.

---

