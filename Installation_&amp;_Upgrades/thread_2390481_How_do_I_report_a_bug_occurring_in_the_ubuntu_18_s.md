---
title: "How do I report a bug occurring in the ubuntu 18 server live installer"
date: 2018-04-29
forum: Installation &amp; Upgrades
---

### Post by wcom939 on 2018-04-29
Hi all,

I'm a bit stumped on how I should go about reporting a bug I found on the ubuntu 18 server live installer. It's not a super big bug but it's quite annoying. I'm installing this on a few VMs in an ESXI environment and noticing that the PC is losing it's DHCP lease from install and requesting a new IP (for example the installer will show 10.0.0.173, and the PC after install will get 10.0.0.174). This did not happen with the previous command line installs for ubuntu (I used to use 16.04).

How do I go about reporting this bug? I have replicated it a few times so can confirm it is an issue.

Thanks,
Dan

---

### Post by Frogs Hair on 2018-04-29
Hello and Welcome

This [link]("https://help.ubuntu.com/community/ReportingBugs") should guide through bug reporting. If you have more questions report back.

---

### Post by PaulW2U on 2018-04-29
wcom939, you might want to look at the existing bug reports to see if your issue has already been reported:

[https://bugs.launchpad.net/subiquity/](https://bugs.launchpad.net/subiquity/)
[https://bugs.launchpad.net/ubuntu/+source/subiquity](https://bugs.launchpad.net/ubuntu/+source/subiquity)

---

