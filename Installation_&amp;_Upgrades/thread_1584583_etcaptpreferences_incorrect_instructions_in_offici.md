---
title: "/etc/apt/preferences: incorrect instructions in official Ubuntu wiki???"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by u1106 on 2010-09-29
This is a question about the instructions in [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed). I understand these are official Ubuntu instructions, so they should be correct.

Not sure where these instructions could be discussed. There is a "feedback" link on the page, but it is broken (http 404)

So here it goes...

According to the instructions one should create file /etc/apt/preferences with

```
Package: * 
Pin: release a=lucid-security 
Pin-Priority: 990 

Package: *
Pin: release a=lucid-updates
Pin-Priority: 900 

Package: *
Pin: release a=lucid-proposed
Pin-Priority: 400
```I have had these settings for a couple of months and now I have observed that I'm lacking several updates.

If I read the package pins correctly, my current priorities mean that whenever something exists in lucid-security all subsequent updates in lucid-updates will be ignored. I don't think that this makes any sense.

If I today just for testing change both Pin-Priorities to 500 (I believe to remember that 500 is something like a default value) and run 

```
sudo apt-get -s dist-upgrade
```I get the following simulation results

```
The following NEW packages will be installed:
  linux-headers-2.6.32-25 linux-headers-2.6.32-25-generic
  linux-image-2.6.32-25-generic
The following packages will be upgraded:
  ghostscript ghostscript-cups ghostscript-x libc-bin libc-dev-bin libc6
  libc6-dev libc6-i686 libgs8 libkpathsea5 libldap-2.4-2 linux-generic
  linux-headers-generic linux-image-generic linux-libc-dev
15 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
```So I'm lacking quite some updates, just because the "normal" update came after a security update. 

Example: (With the original pins 900 and 990 restored)

```
apt-cache policy libc6
libc6:
  Installed: 2.11.1-0ubuntu7.1
  Candidate: 2.11.1-0ubuntu7.1
  Version table:
     2.11.1-0ubuntu7.3 0
        400 http://fi.archive.ubuntu.com/ubuntu/ lucid-proposed/main Packages
     2.11.1-0ubuntu7.2 0
        900 http://fi.archive.ubuntu.com/ubuntu/ lucid-updates/main Packages
 *** 2.11.1-0ubuntu7.1 0
        990 http://security.ubuntu.com/ubuntu/ lucid-security/main Packages
        100 /var/lib/dpkg/status
     2.11.1-0ubuntu7 0
        500 http://fi.archive.ubuntu.com/ubuntu/ lucid/main Packages
```Version ubuntu7 was the original Lucid release. 

Version ubuntu7.1 was a security update.

Version ubuntu7.2 was a "normal" update. 

Version ubuntu7.3 is a proposed update.

So I understand that ubuntu7.3 is not installed. Its priority is below default and it would require manual installation. That's exactly the purpose of the whole pinning.

However, I don't see any reason why ubunutu7.2 is not being installed. I mean technically the system works as being told. Version ubuntu7.1 has a priority of 990 and ubuntu7.2 of a priority if 900.

But is there any reason not to use the same pin priority for lucid-updates and lucid-security? Probably it does not matter whether the value is 500 or 990 or whatever. But it should be equal.

---

### Post by andrewthomas on 2010-09-29
If you want lucid-updates, then why are you even using pinning?

---

### Post by u1106 on 2010-09-29
> **andrewthomas said:**
> If you want lucid-updates, then why are you even using pinning?

Because I was asked by a Canonical employee to test a proposed fix for a bug I had reported. And he pointed me to the QA team's "official" instructions at [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed). I just followed the instructions without thinking about them then. But now I started to doubt that they are good.

I think the declared purpose of the instructions is just to enable proposed repository for manual installations, but not cause any side effects to the "normal" update and security repos.

---

