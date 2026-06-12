---
title: "Ubuntu 24.04.1 LTS or Ubuntu Pro?"
date: 2024-12-06
forum: Installation &amp; Upgrades
---

### Post by embcen on 2024-12-06
Hello everybody,
I am using Ubuntu since 14.04 LST and now I need to install 24.04.1 LTS on a new notebook for personal use only. I would use it for coding with Ruby, browsing the Internet, watching movies and sports.
When I went to the Ubuntu download page, I was informed by Ubuntu that "LTS stands for long-term support &#8212; which means five years of free security and             maintenance updates, extended up to 12 years with Ubuntu Pro". I did not know of the existence of Ubuntu Pro, but the first impression was that 12 years of support is very interesting. I noticed that a personal subscription for up to 5 machines is free, so I wonder: would be not convenient for end users like me to install Ubuntu Pro instead of Ubuntu 24.04.1 LTS? Is the installation process different (longer or more complicated)? Would its use experience be diverse?
I would appreciate if some of you who know Ubuntu Pro or installed it would share your experience and would give me some advice.

---

### Post by oldfred on 2024-12-06
If you have a new system, the old 14.04 will probably not work.
New systems are UEFI only and require newest kernel & drivers to support all the new hardware.
If 24.04 fully supports your system, then you could consider Ubuntu Pro.

---

### Post by Tadaen_Sylvermane on 2024-12-06
Ubuntu Pro isn't a distribution. Rather just extended support and updates. Free for up to 5 personal machines. Works with any relatively recent version. 14.04 is dead.

---

### Post by embcen on 2024-12-06
14.04 is my first Ubuntu distro, now I am writing on a machine using 18.04. Would Ubuntu pro work on 18.04 LTS?

```
embcen@SATELLITE-L50-A-161:~ $ pro security-status
2213 packages installed:
     1917 packages from Ubuntu Main/Restricted repository
     276 packages from Ubuntu Universe/Multiverse repository
     10 packages from third parties
     10 packages no longer available for download

To get more information about the packages, run
    pro security-status --help
for a list of available options.

This machine is NOT receiving security patches because the LTS period has ended
and esm-infra is not enabled.
This machine is NOT attached to an Ubuntu Pro subscription.

Ubuntu Pro with 'esm-infra' enabled provides security updates for
Main/Restricted packages until 2028. There are 234 pending security updates.

Ubuntu Pro with 'esm-apps' enabled provides security updates for
Universe/Multiverse packages until 2028. There are 26 pending security updates.

Try Ubuntu Pro with a free personal subscription on up to 5 machines.
Learn more at https://ubuntu.com/pro


[info] A new version is available: 34~18.04
Please run:
    sudo apt install ubuntu-pro-client
to get the latest bug fixes and new features.

```

---

### Post by Dennis N on 2024-12-06
> Would Ubuntu pro work on 18.04 LTS?
Sure. I have my 18.04 enrolled in the Pro service.

---

### Post by grahammechanical on 2024-12-06
> but the first impression was that 12 years of support is very interesting.

Let us not get misled. Additional 5 years Extended Security Maintenance (ESM) is free for up to 5 machines or installs of Ubuntu LTS. The additional 2 years extension taking support up to 12 years is not free. It is paid for.

> At the end of the 10 year Ubuntu Pro period, a Legacy support add-on [COLOR=#ff0000]can be purchased[/COLOR]           to cover additional 2 years of the lifetime of Ubuntu LTS, giving a total of 12 years support and maintenance.

[URL="https://ubuntu.com/about/release-cycle"]https://ubuntu.com/about/release-cycle

[/URL]We should read the official documentation. In this way we will not be disappointed because we had unreasonable expectations of what was being offered.

[https://ubuntu.com/pro](https://ubuntu.com/pro)

How to get Ubuntu Pro subscription

[https://ubuntu.com/pro/subscribe](https://ubuntu.com/pro/subscribe)

Click "Myself" and the pricing changes to "Free."

The Software and Updates utility has a Ubuntu Pro tab. Click "Enable Ubuntu Pro" and away you go. Keep in mind that this subscription service is aimed at commercial enterprises because it is from selling services to commercial enterprises that Canonical makes its money. So do not be surprised because the focus is not on home users but mainly on advertising aimed at Commercial enterprises.

For the home user like myself it is a very good deal.

Regards

---

