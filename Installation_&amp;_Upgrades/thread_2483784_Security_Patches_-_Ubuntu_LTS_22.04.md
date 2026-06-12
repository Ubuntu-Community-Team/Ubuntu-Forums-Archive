---
title: "Security Patches - Ubuntu LTS 22.04"
date: 2023-02-08
forum: Installation &amp; Upgrades
---

### Post by sreenivas4488 on 2023-02-08
Hi Team,

We are planning to install Ubuntu LTS 22.04 version in my environment. I would like to check how frequency the Security patches are released and also can we run Ubuntu LTS for the enterprise environment. What is Ubuntu Pro and what is the added feature on it. I know thee is some cost involved in it but if we have Ubuntu LTS then why do we need to go for Ununtu Pro. Can someone explain.

Thank You in Advance.

Regards,
Sri

---

### Post by ubfan1 on 2023-02-08
Patches are released frequently, (several times a week?).  I would expect for a production environment, you would do your own validation/testing of patches before applying them.  The LTS releases typically patch the "main" repository, but not necessarily the "universe" repository packages, and those are what the Ubuntu Pro offers.  If you do not rely on any universe packages, then it wont matter to you.

---

### Post by TheFu on 2023-02-08
Newer LTS releases have more bugs, thus more patching.  You can look in the Weekly Ubuntu Newsletter posted in these forums for a quick idea for patches in 18.40, 20.04 and 22.04.  A simple count would be useful.

I'd only deploy onto 22.04 very simple servers at this point - one where just 1 thing that is core to the OS gets used.  Perhaps an email gateway or other infrastructure server. I wouldn't put a complex webapp onto 22.04 yet or any internet-facing complex systems.  Heck, we are just moving to 20.04 now, off 18.04 servers.  Stability matters the most to us, not "newness".

Of course, different businesses have different needs for different OSes and releases.

---

### Post by grahammechanical on 2023-02-09
This will explain what Ubuntu Pro is.

[https://www.omgubuntu.co.uk/2023/01/ubuntu-pro-general-availability](https://www.omgubuntu.co.uk/2023/01/ubuntu-pro-general-availability)

It is the clearest explanation I have seen. Ubuntu Pro is a development of Ubuntu Advantage. I found that until Ubuntu Pro was offered as a general release it was not easy to get a clear explanation of how Ubuntu Pro differed from Ubuntu Advantage. The old Ubuntu Advantage web page has become a redirect to a Ubuntu Pro web page that I did not find very clear as to what it was all about. Things may have improved.

[https://ubuntu.com/pro](https://ubuntu.com/pro)

Regards

---

### Post by ActionParsnip on 2023-02-10
[https://ubuntu.com/pro](https://ubuntu.com/pro)

Ubuntu LTS in prod is awesome IMHO

---

### Post by MAFoElffen on 2023-02-10
Some of us don't go to a newer LTS until point release .1... such as 22.04.1. That is when the doors have been shaken by the masses, the shininess and the newness has worn off. Ubuntu just released 22.04.2 a few days ago.

I'm a bit different. I do Development Release testing for both Desktop and Server. I know a lot of people here who do Dev Desktop testing. I've been on the Ubuntu Server Team since 2012. They have a regiment of things that get tested before a release is released. There are patches released 3-4 times a week.

I take pride that Ubuntu Server, "itself", is bold and robust. The core and base is there. Of course, the base is not the only things that people run on a Server. What, if anything is the newer version of anything else that goes along with it. That is some of the things I test and shake the doors on.

When things do come up, they are dealt with in a very timely manner. Ubuntu has a good reputation for having good upstream relationships for reporting bugs and receiving patches from upstream sources. I can say that when they are received, after testing to ensure they work, they are applied very quickly.

---

### Post by deadflowr on 2023-02-10
> Ubuntu just released 22.04.2 a few days ago.
It was delayed until February 23
[https://discourse.ubuntu.com/t/ubuntu-22-04-2-delayed-until-february-23/33319]("https://discourse.ubuntu.com/t/ubuntu-22-04-2-delayed-until-february-23/33319")

---

