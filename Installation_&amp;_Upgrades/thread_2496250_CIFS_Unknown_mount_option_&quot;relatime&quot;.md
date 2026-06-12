---
title: "CIFS: Unknown mount option &quot;relatime&quot;"
date: 2024-03-19
forum: Installation &amp; Upgrades
---

### Post by claudiu-v on 2024-03-19
Hi,

I just recompiled my Jetson linux kernel with smb3 support. I don't get the error anymore that version 3.0 is not supported but get the relatime error now:
CIFS: Unknown mount option "relatime"

Can anyone share some insights on what am I missing? I can't find any direction on the internet as what to install or fix... :(

Context:
uname -a
Linux 4.9.253-tegra #1 SMP PREEMPT Tue Mar 19 15:09:00 EET 2024 aarch64 aarch64 aarch64 GNU/Linux

sudo apt-get install cifs-utils keyutils -y
sudo mount -t cifs -o vers=3.0,relatime,username=user '\\192.168.1.100\share' /mnt/share

---

### Post by MAFoElffen on 2024-03-19
Refer to [Ubuntu man page mount.cifs]("https://manpages.ubuntu.com/manpages/xenial/man8/mount.cifs.8.html")

atime, noatime, relatime, norelatime, strictatime, nostrictatime, lazytime & nolazytime are all not valid options for mount.cifs for type cifs (mount -t cifs <options> ...)

What is there on "that" man page are the valid options for that filesystem type.

---

### Post by Morbius1 on 2024-03-20
Not sure what to make of this.

mount.cifs mounts relatime by default. In fact you can't change it if you try.

Since I have no idea what a Jetson Linux Kernel is it may just be my unfamiliarity with your setup.

---

