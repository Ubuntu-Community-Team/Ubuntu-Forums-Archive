---
title: "Read only file system after server upgrade to 10.10"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by penguinboy08 on 2010-10-25
After running an upgrade from 10.04 to 10.10 32 bit server edition, I've run into multiple issues. I followed [this guide]("http://www.ubuntu.com/desktop/get-ubuntu/upgrade") to upgrade the system.

Firstly, after the upgrade (which seemed to go well), the system didn't reboot properly. It had shutdown ssh and most other services (ftp, http), and wasn't responding to any restart jobs I started from Landscape. The server is headless, so I had to power off the machine manually.

Then when it booted I checked to make sure ssh was back up, but almost any command is met with some sort of IO/file system error.

For example, ```
cat /var/log/messages
``` is met with ```
Input/output error
```.

I cannot sudo any commands as I receive ```
sudo: Can't open /var/lib/sudo/raynerw/0: Read-only file system
```

I'm running on three HDDs that are combined using LVM. While the server is currently headless, it is possible to install a screen/keyboard in about half a day, not ideal but possible.

Any suggestions as to how I might solve this issue?

---

