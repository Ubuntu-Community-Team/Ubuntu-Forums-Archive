---
title: "ubuntu 16.04 can't boot after installation"
date: 2016-09-13
forum: Installation &amp; Upgrades
---

### Post by billconan2 on 2016-09-13
[ATTACH=CONFIG]271161[/ATTACH]

I'm refreshing an old supermacro server. the server used to have cent os installed. I just installed ubuntu 16.04 on it. but after installation, it refused to boot. I could boot into recover mode, but for normal boot, it will be stuck at this screen.

in the above call stack, it has cpu_startup_entry. I wonder if this is related to failed cpu initialization? the system has dual cpus.

---

### Post by mörgæs on 2016-09-14
Hi, welcome to the fora.

Which Ubuntu did you install? Server or desktop?

---

### Post by billconan2 on 2016-09-14
Hi,

Thank you.

I tried Ubuntu 14 desktop first, and saw some cpu problem at the installer. I googled, found someone mentioned a kernel bug which might cause similar behavior.

the bug gets fixed with a newer kernel. So I tried ubuntu 16 server. the installation was successful, but when booting, I saw this.

I tried recover mode console&#65292; it could work.

---

### Post by mörgæs on 2016-09-15
Booting in recovery mode, please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. It will show the hardware details.

---

