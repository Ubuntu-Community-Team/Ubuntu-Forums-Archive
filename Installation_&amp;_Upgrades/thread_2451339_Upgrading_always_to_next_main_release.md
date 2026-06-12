---
title: "Upgrading always to next main release?"
date: 2020-10-02
forum: Installation &amp; Upgrades
---

### Post by haba713 on 2020-10-02
If you want to minimize the time spent a long run, should you upgrade your Ubuntu server (with multiple provided services)
a) always to a next main release (e.g. 16 &#8594; 18 &#8594; 20) to avoid problems by keeping steps and changes small
b) less frequently (e.g. 16 &#8594; 20) to minimize the number of upgrades 
c) something else?

---

### Post by haba713 on 2020-10-02
[https://www.omgubuntu.co.uk/2020/04/how-to-upgrade-to-ubuntu-20-04#upgrade-from-18.04](https://www.omgubuntu.co.uk/2020/04/how-to-upgrade-to-ubuntu-20-04#upgrade-from-18.04)
> You can upgrade to 20.04 from either Ubuntu 18.04 or Ubuntu 19.10. If you run Ubuntu 16.04 LTS you will have to upgrade to 18.04 first.

&#8594; It seems that b) isn't an option.

---

### Post by crip720 on 2020-10-02
Think it better with the small upgrades, usually less changes to system.  More you have added on system, can expect less than perfect upgrade.  Would do a clean install after a few upgrades to make sure all prior problems/errors are removed from system.  My opinion only.

---

### Post by ActionParsnip on 2020-10-02
Depends on requirements. Also look out for any gotchas. Free radius going from the version in 16.04 to 18.04 is a BIG difference and you may as well spin up new servers from ISO. Depends on the packages and services you use on the system entirely. A DNS server you can probably just jump to the next LTS release but other services may not be so forgiving.

Personally I like to create servers alongside the live ones (Or even clone the servers with new hostnames and IPs), upgrade them and test them then swap them over under change. Once all is well with the new servers then decommission the old ones. If the new servers are no good then you can roll back easily and will keep your CAB happy

---

### Post by rsteinmetz70112 on 2020-10-02
Opinions vary.  
[LIST]
[*]Many people advocate simply doing a reinstall as easier and quicker
[*]Some people upgrade at every release 20.03 -> 20.10 -> 21.04 -> 20.10 -> etc.
[*]Some people only upgrade between LTS releases 18.04-> 20.04 -> 22.04 etc.
[/LIST]

I personally only upgrade between LTS (Long Term Support) releases. 

Upgrading every release takes too much time and upgrading every 6 months is too quick. Given the short lifespan of the standard releases it is entirely possible they may become obsolete before they can be upgraded if a major event disrupts you normal schedule. For example I am based in New Orleans and in 2005 Katrina shut my office down for 3 months. I spent another 6 or so months dealing with stuff, some computer related and some not but I would have been unable to upgrade during that time. In 2006 switched mu servers from Solaris and SCO Unix to Ubuntu 6.04 LTS version. It has required minimal attention so it wouldn't have been such a problem.

I do not reinstall because most of my computers are some form of server and the configuration files can be easily lost in an upgrade. Sometimes they need to be tweaked due to changes in the installed packages. I also have a couple of computers I use as desktops and experimental machines

I also generally wait a year of so after a new LTS release before upgrading. Normally I'd plan on upgrading from 18.04 LTS to 20.04 LTS sometime after 2021 starts. It generally takes me several months to complete the upgrades of all of my servers (currently 8), allowing for glitches and scheduling my travel and time.

The upgrade process is not without risks. Sometimes it goes well sometimes there are issues. I have never had one fail completely. I don't use much software not in the Ubuntu repositories, I do not use ppas, keeping my systems as "standard" as I can. I tend to believe the LTS upgrades get somewhat more scrutiny from the developers since people who use them generally rely on them for stability, but the fact that there have already been 3 intermediate releases between them makes the changes more significant. 

In the end you have to decide what is important to you.  If you are new to Ubuntu I'd suggest you start with 20.04 LTS and stay with the LTS version until you become comfortable or find a need for quicker upgrades.

---

### Post by scorp123 on 2020-10-02
> **rsteinmetz70112 said:**
>  I do not reinstall because most of my computers are some form of server and the configuration files can be easily lost in an upgrade. 

I let **Ansible **take care of that. I always get my stuff back, exactly the way I like, even after a full reinstallation. But that's just me, this stuff might be "too much" for the average user.

---

