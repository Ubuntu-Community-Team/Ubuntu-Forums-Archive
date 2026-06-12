---
title: "Purging old kernels"
date: 2015-12-02
forum: Installation &amp; Upgrades
---

### Post by zurga on 2015-12-02
I frequently have to purge old kernels to make space for updates. In view of the following screen grab, I think "linux-image-generic" should be removed, but because of its name format being distinct from the others I am not sure.
I will appreciate it if someone could tell me whether it is safe to remove that item. Many thanks.

$ dpkg --get-selections | grep linux-image
linux-image-3.13.0-68-generic                install
linux-image-3.13.0-70-generic                install
linux-image-3.13.0-71-generic                install
linux-image-extra-3.13.0-68-generic        install
linux-image-extra-3.13.0-70-generic        install
linux-image-extra-3.13.0-71-generic        install
linux-image-generic                               install

---

### Post by ian-weisser on 2015-12-02
linux-image-generic is not a kernel package; it's a kernel [I]metapackage.
[/I]
That particular metapackage causes your system to upgrade to a new kernel when released. It contains no kernel files; it pulls in the appropriate kernel package as a dependency.

You can indeed remove the package without immediately damaging your system, BUT your system will no longer automatically upgrade the kernel...including security upgrades. You will need to begin manually tracking and upgrading kernel security upgrades...which also won't save you any space.

The simplest way to save space is to keep the metapackage, and to run '**sudo apt-get autoremove**' after each kernel upgrade (or periodically). If you wish to automate that trivial step, the unattended-upgrades pacakge includes a setting to run autoremove every day in the background.

---

### Post by zurga on 2015-12-03
Thank you very much Ian for your explanation. Much appreciation, and it is good to know.

---

### Post by ptn107 on 2015-12-03
Pop this in a script and make it easy. It removes all but the current running kernel:
```
#!/bin/bash

kernel_list=$(dpkg -l | awk '{print $2}' | grep linux-image- | grep -v $(uname -r) | grep -v linux-image-generic)
headers_list=$(dpkg -l | awk '{print $2}' | grep linux-headers- | grep -v $(uname -r | cut -d \- -f 1,2) | grep -v linux-headers-generic)

apt-get purge -y $kernel_list $headers_list
```
Shove the script in /etc/cron.{daily,weekly}/ and you're good to go

---

