---
title: "Ubuntu Server 23.10 on ProxMox VE doesn't boot"
date: 2024-08-02
forum: Installation &amp; Upgrades
---

### Post by garafievak on 2024-08-02
Hello everyone!
A few months ago, I successfully deployed zabbix server on Ubuntu 23.10 on one of the ProxMox ve 6 VMs.2.
Unfortunately, I found out today that it doesn't work. First, a problem with UEFI was discovered, which I tried to fix by booting from the LiveCD. I didn't do any disk partitioning, I didn't even get to this step. Now, when you try to boot from this disk, the installation starts.
Based on the recommendation found on the Internet, I downloaded this machine from the boot-repair-disk-64 image bit.iso . Command output:
[https://paste.ubuntu.com/p/5GsvH7XGPz/](https://paste.ubuntu.com/p/5GsvH7XGPz/)
Is it possible to solve this problem and how much effort will it take?

---

### Post by TheFu on 2024-08-02
23.10 support ended a few weeks ago.  It isn't worth your time to try and fix an unsupported release.  Further, if you don't move to 24.04 soon (might be too late already), the 23.10 repos to make that easier will disappear.

Please only use LTS releases unless you are willing to upgrade every 6 months.

Nobody knows how much effort anything will take, because nobody has exactly the same hardware/software setup as you.

---

