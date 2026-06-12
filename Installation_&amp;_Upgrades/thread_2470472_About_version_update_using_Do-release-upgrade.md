---
title: "About version update using Do-release-upgrade"
date: 2021-12-31
forum: Installation &amp; Upgrades
---

### Post by junukseo on 2021-12-31
Hi,


I am using ubuntu 18.04 on server and want to upgrade to 20.04


but i never tried to use "Do-release-upgrade" for upgrading.


Is Do-release-upgrade safe?  


Does it have any effect on packages (php, Nginx..v.v) and settings installed on server already?

---

### Post by guiverc on 2021-12-31
You've linked your question with Lubuntu (a desktop release), which is very different for 18.04 & later releases.

If you read [Lubuntu's release notes]("https://lubuntu.me/focal-2-released/") you'll note

> ***Note***, due to the extensive changes required  for the shift in desktop environments, the Lubuntu team does not support  upgrading from 18.04 or below to any greater release. Doing so will  result in a broken system. If you are on 18.04 or below and would like  to upgrade, please do a fresh install.

Even with that, as a *release-upgrade* is performed by the Ubuntu base system, your system will upgrade fully and you'll boot into a Ubuntu 20.04 LTS system, though some breakage should be expected (*some maybe obvious, some you may not easily notice or only notice later*).  The breakage depends on package you've installed.

You mentioned server apps not usually installed on a Lubuntu (desktop) system though?  I'll skip those as only desktop apps were tested on a desktop system such as Lubuntu (*and issues were discovered thus the warning!*)

If they are Ubuntu packages you're using - I'd expect a great results.  However as always, I'd suggest you read the release notes for the release you're upgrading into, as any issues the QA-testing (*Quality Assurance*) pulled up of note will be listed there so you're forewarned of any special requirements.

Server, Desktop & Lubuntu have different release notes, maybe you need to read all, but I've provided a link to the Lubuntu release notes as this was placed in the *Ubuntu Flavors - Lubuntu* section of UF.

**Yes `do-release-upgrade` is safe**, but I'd for recommend reading the release notes first  (*as a QA-tester, we perform our QA-testing for a reason & our discoveries are listed there if of value; even if few users will experience the issues*)

Note:  Later Lubuntu 20.04.3 release notes can be found [here]("https://lubuntu.me/focal-3-released/") - I didn't quote from them earlier as upgrades were open **after** 20.04.1 was released, the warning appearing on the three release notes prior to 20.04.3; but Lubuntu 18.04 was by then EOL/unsupported.

---

### Post by MAFoElffen on 2021-12-31
> **junukseo said:**
> I am using ubuntu 18.04 on server and want to upgrade to 20.04, but i never tried to use "Do-release-upgrade" for upgrading.

Is Do-release-upgrade safe?  

Does it have any effect on packages (php, Nginx..v.v) and settings installed on server already?
I am confused. The Variant section is listed as "lubuntu', but all content of the post asks about "Ubuntu Server"(??)

As "guiverc" addressed the Lubuntu related aspects, I will address the Server aspects...

I do have some questions- (1) What is the job of this server (What role(s) does it provide?)? (2) Is this a personal or production server? (3) Is this server a stand-alone server with a traditional console interface, or does it have a GUI desktop installed to it? 

My disclaimer- Before doing any major change of  system, get a good backup of that system to fallback to.

There are 2 ways to upgrade the release of a server- through a Release Upgrade or via a Migration. If this is a production server, then the recommended method would be a Migration... A Migration is the safest way to upgrade a server.

If it is a personal server, there is two different methods, as per the Ubuntu Server Guide... the recommended method of those two, is via 'do-release-upgrade'. The other method is not as safe / has a higher degree of risk.

Doing a 'do-release-upgrade'... Checks to see if a release is available, then queries the system to see if the system has enough free space to do an upgrade, and analyzes the installed packages to ensure there is a clear path to upgrade those packages. It generates logs of the progress and any errors. It downloads an upgrade package to manage and facilitate the release upgrade.

The second method mentioned in the Ubuntu Server Guide is the older Debian install method of just re-pointing the sources.list to the new repo URL and doing an update/upgrade... There is very little logging and any upgrades of packages are not checked beforehand if they will be successful... Just saying, there is higher risk in that method.

"Any" upgrade of the OS Release version will upgrade the versions of PHP, Nagios and any other server service packages. Those version upgrades may need further configuration modifications to adjust for those. That is the cost of progress, and updated security.

---

### Post by TheFu on 2022-01-01
When moving from release to release, if you've installed packages using the package manager, expect newer versions to be installed.  So, the webserver, DBMS, scripting language(s) and webapp versions **will** be updated.  This will almost certainly break prior scripts, so the webapp will break too.  From time to time, the webserver configuration files change, breaking prior versions too. Be prepared.

With that understanding, you should take the steps you feel are necessary to address any breakage.  

If it was me, I would:
[LIST]
[*]read the release notes for the new version. Always do this prior to any upgrade.  For example, with 20.04 desktop, nvidia support was initially broke. Not knowing that would really suck if you use nvidia GPUs, right?
[*]have a full backup before starting. Sometimes I need to try again after an upgrade failure.
[*]research the major things running on the system. Know what others saw as issues with the web server, dbms, php, and web apps on the system.
[/LIST]

Ok, really the way I do this is mitigated mainly because I use virtual machines, so the old version is still there, running, and I'd start with a new version created by cloning the older storage, then change the system UUID, hostname and IP addresses in the new machine. After that, my risks of failure causing problems are tiny.  I also use LVM, so creating an LVM snapshot in the cloned VM system as a common starting point makes reverting back very easy. If any part of the upgrade goes badly, I'm willing to go back to the point of the snapshot.

If the upgrade process fails more than twice, I'll just create a new VM with the minimal OS I want, fresh, then restore the specific files for the server apps into the system - settings and data.  I don't mix desktops and servers (most of the time).  Those are 2 very different different needs. 1 server for 1 VM is usually how I do it, having been burned trying to run 20 servers inside a single system in the 1990s. Conflicting dependencies made upgrades for the different parts very difficult.  You'd think I would have learned, but I didn't learn enough.  While I have 10+ VMs just for different servers, I got lazy and put 3 webapps using php into the same VM initially.  For the first year, it was fine, but then some upgrades for the different webapps required 3 different versions of PHP and 2 different versions of mariadb.  It was getting ugly and hard to maintain, so I pulled out 1 webapp and put it, alone, into an LXD container. It has been running well inside that container the last 3 months, happily with a fresh DBMS and the php required.  I shutdown 1 of the 2 remaining php webapps, but I still want to pull the last webapp into an lxd container for better management and much faster performance. These php webapps cannot be access directly over the internet, but people who can connect to our VPN can fully access them, no problem.  I'm not sure I'd use containers with internet-facing webapps. That reluctance is just my ignorance, probably.

---

