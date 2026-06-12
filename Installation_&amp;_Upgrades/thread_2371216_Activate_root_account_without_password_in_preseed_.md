---
title: "Activate root account without password in preseed file"
date: 2017-09-12
forum: Installation &amp; Upgrades
---

### Post by mrt-lacko on 2017-09-12
Hello,
I need to create minimal pre-seed file that will activate root account **without** password.
I checked the forums but couldn't find something useful.

***_Disclaimer:_***
I understand risks of root account without password, but this pre-seed file is required for
VM contextualisation which *requires* active root without password from fresh installation
and **will** set the password at the first boot.

---

### Post by TheFu on 2017-09-12
Welcome to the forums.
 
[https://docs.opennebula.org/5.2/operation/vm_setup/kvm.html](https://docs.opennebula.org/5.2/operation/vm_setup/kvm.html) says to just use a ssh-key, if that is what you are attempting.  I do something like this for my backup solution. I "pull" backups using a root-equiv account on each client.  An admin with proper training would understand how to accomplish that.

In these forums, even describing how-to enable the root account is forbidden, so I doubt anyone can really help here without trouble from the mods.

---

### Post by mrt-lacko on 2017-09-12
SSH-key is expected in context definition and will be used to set-up root password during contextualisation (at first boot). that's why it expects fresh install with active root account without password.

Actually Debian pre-seed wiki describes how to activate root account in pre-seed file, but requires hash password.

> In these forums, even describing how-to enable the root account is forbidden

Didn't know that so thanks for warning.

---

### Post by vasa1 on 2017-09-12
Thread closed.

---

### Post by QIII on 2017-09-12
Actually, what we do not allow is discussion of logging in to a GUI as root.  Please see 
[https://ubuntuforums.org/showthread.php?t=1486138](https://ubuntuforums.org/showthread.php?t=1486138)

(I do see some older info about gksu, which I'll edit later when I'm not on my cell phone on a crowded train.)

In any case, for a consistent answer on the forums we ask that users first be directed to [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Re-opened.

---

