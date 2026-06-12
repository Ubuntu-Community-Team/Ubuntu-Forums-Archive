---
title: "desktop install configuration vs server install?"
date: 2013-06-29
forum: Installation &amp; Upgrades
---

### Post by ahardy66 on 2013-06-29
Hi All

I have Ubuntu running on my main machine and I originally made the mistake of choosing the "desktop installation" when I put 12.04 on it, and I should have chosen the "server" version. 

I run the machine as a gateway machine with a modem, serving the LAN with DNS, DHCP, firewall etc and so I get conflicts when I upgrade. The upgrade I just ran to Raring Ringtail has foobarred something (in another post) and what I want to do is ensure that the install process next time doesn't think that it's installing a desktop. I want it to stick to package upgrades only and not add de-installed packages back into my mix.

So my question is, where is the config that tells the system that this is a desktop config? And can I change that to 'server'?

Thanks

---

### Post by Frogs Hair on 2013-06-29
This may shed some light on the subject.   [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

### Post by steeldriver on 2013-06-29
AFAIK the upgrade script just looks at what packages are installed, and applies upgrades to those if available - there is no real distinction between 'Desktop' and 'Server' except which packages are installed from the get go

```

       upgrade
           upgrade is used to install the newest versions of all packages currently installed on the system from the sources enumerated in /etc/apt/sources.list. Packages
           currently installed with new versions available are retrieved and upgraded; [B]under no circumstances are currently installed packages removed, or packages not
           already installed retrieved and installed[/B]. New versions of currently installed packages that cannot be upgraded without changing the install status of another
           package will be left at their current version. An update must be performed first so that apt-get knows that new versions of packages are available.

```

There are ways to 'pin' packages but it is probably easier to just remove the things you don't need

---

### Post by ahardy66 on 2013-06-29
```
[B]under no circumstances are currently installed packages removed, or packages not
           already installed retrieved and installed[/B]
```

I wish I could go back in time with a lawyer and get a screenshot of my system. The above is not true, unless my package system was seriously foobarred. 

Anyway besides that, it's interesting to learn that meta-packages are applied at such a basic level. I have xubuntu-desktop installed, so I guess that should go - perhaps it's the problem. I don't have a *-server package of any kind, nor can I find one in the sources with apt-cache. There's no edubuntu-server, no ubuntu-server. And searching on "ubuntu server meta-packages" doesn't come up with any useful results. It must be out there somewhere right? I'm obviously not using the right archive.

---

### Post by steeldriver on 2013-06-29
That's because the server installation is really just the desktop installation **minus** whatever *ubuntu-desktops (along with all of their dependencies... right down to and including the whole X server infrastructure)

Although having once (for learning purposes) added and then removed ubuntu-desktop from a server installation, it's not something I'd recommend trying without a fair bit of research - in case it removes something unexpected

---

### Post by Cheesemill on 2013-06-29
> **ahardy66 said:**
> ```
[B]under no circumstances are currently installed packages removed, or packages not
           already installed retrieved and installed[/B]
```

I wish I could go back in time with a lawyer and get a screenshot of my system. The above is not true, unless my package system was seriously foobarred.

That quote is from the man page for the 'apt-get upgrade' command and is 100% correct.

What caused your issue is doing a release upgrade from one version of Ubuntu to the next (not just the normal package upgrade). When you upgrade from one release to the next the desktop metapackage (in your case xubuntu-desktop) is re-installed before the upgrade happens. This is done in a desktop scenario because there may be new dependencies which wouldn't get installed otherwise.

This advice is too late now but it is recommended to stick with LTS releases like 12.04 for server installations as it is supported until 2017. Now that you are on 13.04 you will have to keep upgrading your machine every 6 months.

---

### Post by ahardy66 on 2013-06-30
Aha. OK thanks for the warning, even if it was partially too late :S

---

