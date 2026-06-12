---
title: "Enable/start service in autoinstall/cloud-init?"
date: 2024-11-26
forum: Installation &amp; Upgrades
---

### Post by jbygden on 2024-11-26
Anyone know if I can enable a service from autoinstall? I'm installing openssh-server in the autoinstall, and I'd like it to start on first boot after the install is done. Can it be done with autoinstall/cloud-init?

---

### Post by TheFu on 2024-11-26
I've never used autoinstall or cloud-init successfully. Canoncial kept changing the way that autoinstall worked, so we switched to a 3rd party tool for system management.  Frustrating when things are constantly changing, especially when the new method isn't actually better. I suppose "better" is subjective.

Does sshd not automatically start?  After a normal install of the "ssh" package, the daemon process is enabled and started, no other actions needed.  "ssh" is a metapackage that installs both the client and the server.  You might try that.

---

### Post by jbygden on 2024-11-26
Yes, I know that if I install openssh-server regularly after install it's enabled by default. Strange that it isn't if installed by autoinstall - could it be that it's enabled in the installation system when installed instead of in the target system?
I'll try with `ssh` instead, and see what that does.
BTW, autoinstall didn't work with 22.04, but now with 24.04 it does work again...

---

